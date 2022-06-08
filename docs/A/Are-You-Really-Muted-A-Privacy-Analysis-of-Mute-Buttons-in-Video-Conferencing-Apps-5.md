---
layout: default
title: 5 Webex Case Study 
parent: § Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps 
grand_parent: A 
nav_order: 50 
---
<style>
.dont-break-out {
  /* These are technically the same, but use both */
  overflow-wrap: break-word;
  word-wrap: break-word;

     -ms-word-break: break-all;
  /* This is the dangerous one in WebKit, as it breaks things wherever */
  word-break: break-all;
  /* Instead use this non-standard one: */
  word-break: break-word;
}

.youtube-container {
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 56.25%;
}
.youtube-video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

</style>

<div class="dont-break-out" markdown="1">

1. TOC
{:toc}

## 5 Webex Case Study
Based on our findings from the previous section, we perform an in-depth analysis of the microphone access pattern in Cisco Webex<sup>6</sup> . We focus on Windows 10 as it is the most widely used operating system at home and in enterprise<sup>7</sup> . As Webex continuously samples the user’s microphone (when muted), we need to study whether audio-derived data leaves the local device.

Determining whether audio-derived data from a VCA is leaving on the network port is not a straightforward task because the network flow from VCA to a server is encrypted. Raw dumps of the network traffic from Wireshark are not informative about precisely what the network traffic carries to the VCA’s server. And we know that VCAs send and receive network packets that do not contain any audio or video data, so counting network packets cannot give us an indication of whether audio-derived data is leaving a device while the VCA is muted. Instead of directly logging network packets, we need to track how audio data is processed within a VCA.

### 5.1 Methodology for Traffic Interception
Fig. 6 depicts the flow of data from microphone to network in native Windows apps. Understanding how a particular VCA handles data from the microphone requires tracking the data as it traverses the chain of processing shown in Fig. 6. Most of the data processing in the VCAs we study is handled by proprietary DLLs<sup>8</sup> . Tracking data through function calls from the main VCA process to a DLL is unreliable because runtime binary analysis tools like IDA Pro [2] and x64dbg [4] often cause the app to crash when they single-step through function calls to a DLL. And since each VCA uses a different set of external DLLs, we could not establish a single workflow to analyze all VCAs. Existing tools such as TaintDroid [18] are able to establish the data flow within an application in older Android versions. However, in native applications designed for Windows and macOS, flow tracing is difficult and sometimes impossible.

![Fig. 6. Data flow of audio bytes within a Windows 10 VCA. This pipeline is generalizable across the Windows platform. Our system attaches to the bolded modules.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-6.png)

**Fig. 6.** Data flow of audio bytes within a Windows 10 VCA. This pipeline is generalizable across the Windows platform. Our system attaches to the bolded modules.

It is easy to see when an app accesses the hardware (networking and microphone) by monitoring Windows API calls (see Sec. 4.2), but we are not aware of any tool that can automatically follow data through an entire Windows app. Tracking microphone data after each instruction is not straightforward. Such data initially exists inside of dynamically-allocated memory buffers. Upon each access, this data might move to a new buffer after undergoing a transformation, such as encryption, compression, or encoding. Further, the new buffers may originate from different allocator functions to be stored in the main process’s memory image or in an external DLL’s memory image. Race conditions among the threads in Webex compound the difficulty of tracing: all memory accesses at a specific address of the stack require stoppages, logging, and memory analysis, all of which take time to perform.

However, we do not necessarily need to show a linkage between every successive subroutine that handles microphone data in a VCA to demonstrate that audioderived data leaves on the network. We can already dynamically trace the audio into the app. We need to show that data from that buffer leaves our machine and is transmitted to a Webex server.

To design such a system, we first map all of the outgoing traffic from Webex. The most efficient way of doing so is to use the Microsoft Network Monitor (MNM). We observe Webex’s network traffic using the MNM while the app is muted and unmuted, and we notice a set of packets that are periodically going to a user metrics Cisco server. Now that we have our packets, we need to ensure that the audio buffer within Webex is accessed in the muted state.

Binary tracing on the audio buffer’s read/write access using x64dbg always ends up in stack space which thwarts our further tracing. However, while following the bytes and logging API calls (from Sec. 4), we noticed that Webex calls encoding libraries which access in some time correlation with the audio bytes. We then trace API calls to encryption methods to verify what is happening using the API Monitor. We capture all input arguments and output buffers as a log file from these calls while the user was muted during a Webex meeting. The log contains timestamps, input parameters to the API call, and the resulting output buffer. With the results

![Fig. 7. Correlation between audio gain reported by Webex and in- put audio signal power level (in dbA) when noise removal mode is enabled. Although we cannot observe the raw audio while muted, the statistics reported by Webex leak information about the user’s background noise.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-7.png)

**Fig. 7.** Correlation between audio gain reported by Webex and in- put audio signal power level (in dbA) when noise removal mode is enabled. Although we cannot observe the raw audio while muted, the statistics reported by Webex leak information about the user’s background noise.

***
<sup>6</sup> We used Webex client version 41.12.3.11 through our study.
{: .fs-2}
<sup>7</sup> 90% of respondents to our user study used Windows.
{: .fs-2}
<sup>8</sup> Dynamically Linked Libraries (DLLs) are the Windows implementation of shared libraries.
{: .fs-2}
***

of the function logged, we compare the encrypted buffer to network traffic leaving the machine and notice a oneto-one match between the encrypted bytes (from Wireshark) and the data sections of network packets from Webex. Consequently, we link the data regions of outgoing user metrics packets to our post-encrypted output buffers. Upon observing the input, we notice that the input arguments in these cases are in plain-text where detailed data is compressed using base64 encoding. Decoding the input arguments revealed the packet content to be a JSON structure9 , which contains audio-derived data and other data elements.

### 5.2 Findings for Traffic Interception
The data we capture from the API hook is a JSON array with unencrypted and unobfuscated attribute names such as: audioMaxGain, audioMeanGain, audioMinGain, and many others. These JSON arrays are transmitted by Webex once per minute to https://tsa3.webex.com, a telemetry server, while the user is muted. The names of these attributes suggest that the JSON array contains audio-derived statistics, most probably connected to the automatic gain control employed by Webex. Our aim is to further analyze the attributes to understand the relationship between the recorded audio levels and these attributes values when the microphone is muted.

Webex has two microphone modes: music mode and noise removal mode (the default mode). As the name suggests, noise removal mode refers to Webex removing background noise in real-time while the user is speaking. Music mode, on the other hand, transmits audio as the microphone hears it. We perform a small-scale experiment to study whether the audio attributes from Webex network traffic are correlated with the input audio for both microphone modes. We play episodes of the U.S. TV shows “Friends” and “The Office” into a microphone during a Webex meeting while muted. To isolate environmental factors, we feed the audio from the TV shows directly into the Webex meeting through a virtual microphone interface. We repeated each experiment for both microphone modes.

We partition each audio file (corresponding to an episode) into a set of one-minute windows. We then compute the maximum and average magnitudes for each window to report their correlation with audioMinGain and audioMeanGain. Note that the audioMinGain value would correspond to the maximum observed audio level because it requires less gain control. Further, the minimum and mean values depend the most on the input audio. On the other hand, the maximum depends more on the input device and the amount of silent moments, which are random in each episode.

Fig. 7 depicts the correlation between the estimated power levels and measured gain values for noise removal mode. As evident from the figure, the measured and estimated values exhibit high correlation; the correlation with the mean gain is higher as it is a more robust metric to window shifts. Note that we do not have access to the source code when computing the gain values,

***
<sup>9</sup> An example of such a structure is here: https://osf.io/szd4x/
{: .fs-2}
***

so a perfect correlation is unlikely. This correlation is slightly lower than that of the music mode (Fig. 11 in Appendix D), implying that the noise removal changes the input audio. Still, the measured audioMinGain and audioMeanGain are representative of the audio levels.

### 5.3 Classification of Background Activities
We established that Webex accesses the microphone while muted and sends audio statistics to their servers. Further, this data is highly correlated with the energy level received at the microphone, and appears to be indicative of the activity happening in the background. The logical question that follows is: *is there a potential of learning the user background activities from audio statistics sent to Webex’s servers?* In the following, we describe how these statistics can fingerprint the user’s background activities, when they are muted.

We analyze the inference of information from user’s Webex telemetry traffic while being muted. For each one-minute window, this information contains three values that change relatively : mean, min, and max audio gains. An entity with access to this information, such as Webex’s cloud service or any adversary able to view this traffic in transit, can perform this analysis to infer what activity is occurring in the user’s environment.

#### 5.3.1 Data Collection
We focus on the background activities from our user study of Sec. 3. In Fig. 2, we highlight twelve activities that happen in the user’s background. Out of these activities, we do not consider: (1) silent and physical activities as they do not result in gain changes, (2) bathroom as it is unlikely that the user’s microphone will pick up bathroom noises, (3) street noise as it does not represent a private activity, and (4) diverse noise such as TV shows which may contain all of the classes in a single 30-minute instance. As such, our objective is to identify whether the gain values can fingerprint six types of activities: (1) music playing, (2) cooking or eating, (3) people talking, (4) animal sounds (especially dog barking), (5) keyboard typing, and (6) cleaning.

![Fig. 8. Clusters of audio statistics data color coded by back- ground activity type. Clusters are visually separable.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-8.png)
**Fig. 8.** Clusters of audio statistics data color coded by back- ground activity type. Clusters are visually separable.

To simulate the real-world environment with specific background activities, we choose multi-hour long ASMR YouTube videos that consist of single background activity. Each video is different such that the videos are produced by different people (YouTube users) doing the same task. The purpose of selecting the videos in such a way is to minimize the effects from the recording environment. We play each video over the air through a Webex meeting, while muting the microphone, and log the extracted gain values.

Our data collection consists of two Windows 10 machines. The first machine plays the videos using its speaker and hosts the meeting for the other machine. The other machine runs a Webex meeting client (without any other app running). One machine is equipped with a Logitech QuickCam Pro 9000 while the other uses a Logitech C920S Pro HD 1080p webcam for microphone input. Both machines then join the same meeting room and collect data simultaneously; on both, we mute the microphone, turn off the camera, and keep the default microphone settings.

We place the machines in a 12 푓 푡 × 7 푓 푡 × 10 푓 푡 room. We adjust the distance from the speaker to the two microphones and generate multiple datasets based on the varying distances. Webex only allows for meetings to last for 24 hours. For each Webex meeting, we can extract around 1440 data points, stamped with the corresponding label. Each data point corresponds to three features: audioMaxGain, audioMeanGain, and audioMinGain, representing three user metrics values from one minute of audio. In summary, we performed data collection over the course of two months, yielding over 180 hours of data points.

We visualize the distribution of the six background activities in Fig. 8. This figure shows that it is feasible to fingerprint background activities by analyzing the extracted gain values from Webex. Each activity exhibits relatively consistent and distinguishable gain values, despite sampling diverse videos to represent each activity.

#### 5.3.2 Classifier Training
We design a classifier to highlight how the background activities can be fingerprinted based on the observed gain values. In what follows, we describe how we curate the data for this classifier, how we design and train the classifier, and the results of the classification.

##### Data Preprocessing
We split the YouTube videos into a development set (training and validation) and an evaluation set. The two sets have no overlaps in the videos. We set the distance from the microphone to speaker as 10 cm, 25 cm, and 50 cm for both sets of videos, whereas we added an extra distance condition, 100 cm, for the evaluation set.

Table 3 shows the data distribution for the development and evaluation sets. We split the development set into a training set (80%) and validation set (20%) for hyper-parameter tuning. We split the evaluation set into two subsets to study the effect of distance. The first evaluation subset is collected at distances of 10 cm, 25 cm, and 50 cm between the speaker and microphone. The second subset is collected at a distance of 100 cm; the data in the second evaluation subset has no overlap with the development set in terms of distance and source videos.

For a t-minutes long YouTube Video, we extract  data points; each data point is assigned the same label derived from the title of the video. To accommodate videos of varying lengths, we limit the input to the classifier to clips of length . Thus, we apply a sliding window with length  to each window and set the moving stride to be 1. We define each clip as:

![We define each clip as](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-other-1.png)

where max represents the audioMaxGain for the ℎ minute in the window.


![Table 3. Dataset distribution, development set (training and vali- dation) and evaluation set (subset 1 and 2).](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-table-3.png)

**Table 3.** Dataset distribution, development set (training and vali- dation) and evaluation set (subset 1 and 2).

##### Model Design and Training
We train a supervised multi-class classifier to distinguish background activities given clip data of length. Similar to Schuster et al. [39], we use a Convolutional Neural Network (Fig. 10 in Appendix); the network consists of two 1-dimensional convolution layers, flatten layer, three dense layers, and a softmax layer (of size 6). The design of the convolutional layer takes into account feature and temporal correlations.

We train the network using an Adam optimizer with a cross-entropy function as the loss calculation function. We set the learning rate to 0.001 and initialize model parameter weights in a random uniform distribution. As the total length of the training set and validation is around 3000, we evaluate different batch sizes: 50, 500, 1000, 1500, and 3000. We utilize early stopping to prevent over-fitting. Because the dataset is imbalanced, we calculate the precision separately for each class and compute the average precision score weighted by their proportion in the validation dataset. Then we use the weighted average of precision score and accuracy of all classes as the early stopping criterion. We select the best-performing epoch index and batch size to train the optimal classifier for each window length.

We train the network on windows of size n: 3, 5, 7, 10. Comparing the performance of 4 optimal classifiers for each window length, we observe that n = 7 (96.13% precision on validation set) outperforms windows n = 3 (92.26%) and n = 5 (92.98%), in terms of the accuracy score and precision score of the validation set. We achieve 96.90% with windows length n = 10 but we remove it in case of over-fitting.

#### 5.3.3 Classification Results
We present the per-class performance of classifier with window lengths 3 and 7 in Fig. 12 and Fig. 9. For window size of n = 7, we achieve 77.75% macro accuracy on evaluation set 1 and 89.03% macro accuracy on evaluation set 2. The average of per class precision for evaluation set 1 is 73.07% while that is 87.47% for evaluation set 2. Note that evaluation set 2 is collected with 100 cm microphone to speaker distance; our results suggest that the volume level and video content do not considerably hurt the classifier performance.

For window size of n = 3, we achieve 78.70% macro accuracy on evaluation set 1 and 78.48% macro accuracy on evaluation set 2. The average of per class precision for evaluation set 1 is 79.35% while that is 84.35% for evaluation set 2. Both classifiers follow our early stopping criteria and achieve high performance on evaluation sets. This performance indicates that, even with three-minutes worth of measurements, it is possible to infer the ongoing background activities.

For both window sizes, dog barking, crowd talking, and cleaning show high precision as well as accuracy on both evaluation datasets. Some music and people talking samples are misclassified as keyboard typing on evaluation set 1 and 2 respectively, while cooking and eating shows a lowest performance among the six background activities. On both evaluation sets 1 and 2, “cooking or eating” data points are severely mingled with “keyboard typing” as both classifiers cannot accurately classify these two classes at the same time. We discuss this aspect in Sec. 6.1.

Finally, we test whether Webex’s noise-canceling feature affects the statistics reported in log packets. The results are nearly identical with noise-canceling disabled or enabled. However, there is a difference between the logged gain values from Webex when alternating between the music and noise-removal modes. Therefore, we only collect and present results based on data collected with noise-canceling enabled — the default setting — through our entire classification process.

Our classifier performs well on both evaluation sets in under various kinds of background noise, recording environments and volume levels. The gain values logged by Webex and sent to its cloud server can be used to distinguish multiple types of background activity.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-1/">1 Introduction</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-2/">2 Related Work</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-3/">3 User Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-4/">4 Analysis of Mute Button</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-5/">5 Webex Case Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-6/">6 Discussion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-7/">7 Conclusion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-8/">Acknowledgements</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-9/">References</a></li></ul>

***

</div>
