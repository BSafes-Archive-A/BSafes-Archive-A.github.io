---
layout: default
title: 2 Related Work
parent: § Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps  
grand_parent: A
nav_order: 20 
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

## 2 Related Work
In the following, we discuss the recent results about the privacy of VCAs. While there is existing research studying possible exfiltration of audio and video data from mobile apps [37], we focus on the research specific to VCAs. We also include related work about mute buttons in the context of smart speakers. Finally, we discuss the work surrounding background activity recognition, which is relevant for our analysis in Sec. 5.3.

### Privacy Issues in VCAs
The security and privacy of video conferencing platforms has been studied since the early 2010s. In 2013, Kilpi et al. examined privacy and security issues in future (at that time) videoconferencing technologies [25]. They discuss the mute button as a necessary privacy control for the users. More recently, Emami-Naeini performed an online user study to understand the user concerns with VCAs [17]. They found that users are concerned about the security and privacy properties of VCAs. They also found that individuals consider the mute button as a privacy control: they perceive privacy violations from forgetting to press the mute button.

During the pandemic, more people were exposed to privacy and security risks caused by VCAs [34, 38]. In 2019, Zoom fixed a camera leakage vulnerability caused by its casual use of a local web server [35]. Meanwhile, real-time background blurring for VCAs is widely adopted to protect user’s privacy in an office or home environment [36, 45]. However, VCAs may leak a user’s video privacy in many ways. Kagan et al. [23] demonstrated that collage images of video conference meetings posted on public websites may leak sensitive information such as users’ names, ages and genders. Altschaffel et al. [8] showed that traffic patterns of encrypted metadata and multimedia data exchanged during VCA meetings, can be used to identify increased activity in front of camera or even identify users. There are also concerns with the information that VCAs collect about their users. For example, Consumer Reports identified privacy concerns with the data collection practices of popular VCAs, such as Zoom, Google Meet, Microsoft Teams, and Cisco Webex [40]. These concerns centered around the purposes of collecting metadata from the meetings.

In this paper, we follow-up on these previouslyreported vulnerabilities and privacy studies. In particular, we study the users’ understanding and expectation of the mute button, and whether they match the VCAs’ behavior. We focus on the interaction between the VCA and the user’s microphone when the user presses the mute button, as opposed to previous research that studies the mute button in the context of protecting the user’s privacy from other meeting participants.

### Mute Button in Voice Assistants
Researchers have also considered the privacy issues from always-listening smart home devices[6, 26]. Smart home devices continuously process the raw audio to detect a trigger word or phrase. As such, the privacy threats arise from these devices accidentally or maliciously recording the user’s background activities [7]. Researchers have first discussed the efficacy of the physical mute button as a privacy control to mitigate these threats. The mute button was found to be inconvenient and suffering from user trust issues [14, 26]. Follow-up works proposed other privacy controls, such as ultrasound jamming [14, 15, 41], cutting the power [14], and employing interpersonal communication cues [32].

Contrary to the smart device case, VCA users widely utilize the mute button to prevent others from listening to their background activities (Sec. 3). Users trust that other meeting participants cannot hear them after applying the mute button. However, the behavior of the VCA, after applying the mute button, is less understood. In this paper, we characterize the operation of the mute button from the perspective of the interaction between the user and the VCA.

### Activity Fingerprinting
Finally, we discuss research about fingerprinting activities from audio-derived data. User activities and contextual information, including walking, driving, and riding, can be inferred from ambient sound. Lu et al. [29] presents an audio event classifier that identify user’s current activities utilizing the microphone input of mobile phones. Not only the ambient sound, but encrypted audio traffic can be used to infer user’s private information. Previous studies proved that encrypted IoT traffic might leak private information of their environment, including device status and user activities. Traffic analysis of the video streams from home security cameras enables monitoring daily activity patterns [11, 16, 28]. Li et al. [27] further demonstrated the possibility of detecting fine-grained activities, including dressing, moving, and eating, from encrypted home security camera traffic. They selected features such as traffic packet size and length distribution. Similar to encrypted traffic analysis, Schuster et al.[39] performed an encrypted Video Stream Identification by analyzing bitrate burst and time interval of video streaming traffic. They utilized the segment transmission mechanism of MPEG-DASH and successfully identified Netflix video titles using a trained classifier.

Kennedy et al. and Wang et al. [24, 43] demonstrated that an attacker can infer which voice commands a user says to a smart speaker, by eavesdropping and analyzing outgoing encrypted traffic from smart speakers to a cloud server. Wang et al. [43] further manifested the incoming traffic from the server also leak voice commands information. Moreover, Bae et al. [5] presented a video streaming service identification attack by monitoring video downstreaming traffic through LTE networks with high accuracy.

These research works demonstrate that data derived from audio streams can be used to fingerprint their content and is therefore relevant to our discussion in Sec. 5.3 about inferring the background activities while the user is muted.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-1/">1 Introduction</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-2/">2 Related Work</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-3/">3 User Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-4/">4 Analysis of Mute Button</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-5/">5 Webex Case Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-6/">6 Discussion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-7/">7 Conclusion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-8/">Acknowledgements</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-9/">References</a></li></ul>

***

</div>
