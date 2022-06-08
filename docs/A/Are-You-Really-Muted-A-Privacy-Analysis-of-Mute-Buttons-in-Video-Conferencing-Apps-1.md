---
layout: default
title: 1 Introduction
parent: § Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps
grand_parent: A
nav_order: 10 
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

## 1 Introduction
As the de facto alternative for in-person meetings during the COVID-19 pandemic, the demand for online video conferencing for professional and personal use increased significantly. Video Conference Apps (VCAs), such as Zoom, Slack, Teams, and Webex, became available on all modern devices and operating systems. To support their functionality, these VCAs require access to the device’s microphone and camera. Operating systems (OSes) provide the users with permission controls that allow the app to access the microphone and camera. Once granted, the app has access to both hardware resources until the user revokes the permission.

In addition to OS-based controls, VCAs provide their users with two privacy control mechanisms during a call: turning off the camera and muting the microphone. In most OSes, such as Windows and macOS, turning off the camera from the app engages an OS-level control which prevents the app from accessing the camera. A visible hardware indicator (e.g., a light near the camera) informs the user whether an app is accessing their camera. On the other hand, the implementation of the mute button is app-dependent and rarely has a visible hardware indicator. OSes do not expose an easily accessible microphone switch to the apps without going through many steps (e.g., via a control panel).

Apart from smart speakers, which pose tangible privacy threats, the mute button has received little attention in the context of VCAs. Previous research investigates users’ privacy attitudes towards VCAs and alludes to the mute button as a privacy control tool available to the users during a virtual meeting [17, 25]. However, the mute button’s privacy implications during the interactions between the user and VCAs have not been adequately addressed.

This paper investigates the privacy issues associated with the mute button in VCAs, focusing on whether a mismatch exists between the user’s perception of the mute button and its actual behavior. We follow a twopronged strategy to guide our investigation. First, we

***
**Yucheng Yang†:** University of Wisconsin-Madison, E-mail: yang552 'at' wisc.edu
{: .fs-2}
**Jack West†:** Loyola University Chicago, E-mail: jwest1 'at' luc.edu
{: .fs-2}
**George K. Thiruvathukal:** Loyola University Chicago, Email: gkt 'at' cs.luc.edu
{: .fs-2}
**Neil Klingensmith:** Loyola University Chicago, E-mail: neil 'at' cs.luc.edu
{: .fs-2}
**Corresponding Author: Kassem Fawaz:** University of Wisconsin-Madison, E-mail: kfawaz 'at' wisc.edu
{: .fs-2}
† Both authors contributed equally to this work.
{: .fs-2}
***

design a user study to uncover what the users think the mute button does (i.e., their understanding) and what they believe it should do (i.e., their expectations). Second, we compare the user study findings against an empirical investigation of the actual behavior of the mute button across a range of VCAs and operating systems.

We conducted a user study with 223 participants recruited from Prolific. Our user study revealed that the participants perceive the mute button of VCAs as a privacy control, preventing other meeting participants from overhearing them. We observed a dichotomy in the understanding of the mute button: participants were split about whether a VCA accesses the microphone after they click the mute button. However, most of them indicated that the VCA should access the microphone only when unmuted.

Based on the findings from the user study, we empirically characterized the conditions in which the VCA actively queries the microphone in different operating systems. This task was challenging because OSes only log microphone accesses for each app; they do not provide fine-grained statistics about microphone queries. We addressed this challenge by instrumenting Windows, macOS, Linux, and the Chromium browser to track the fine-grained microphone queries by popular VCAs. We conducted a set of experiments on each VCA-OS combination to monitor the API accesses of each VCA under different conditions. We discovered that *all* of the apps in our study could actively query (i.e., retrieve raw audio) the microphone when the user is muted. Interestingly, in both Windows and macOS, we found that Cisco Webex queries the microphone regardless of the status of the mute button.

We followed our instrumentation efforts with an analysis of Webex, a popular VCA for the enterprise setting. We analyzed how it processes the queried microphone data to determine whether any audio-derived data leaves the device. This analysis also proved challenging as the VCAs, such as Webex, encrypt outgoing traffic. Further, tracking the data flow within apps is not straightforward because they employ proprietary and obfuscated libraries. To facilitate tracking of audio data, we performed a backward search from the encrypted network traffic to locate the inputs to the encryption functions. This search allowed us to decrypt the contents of the network packets sent by Webex to its servers. We discovered that Webex sent periodic packets containing audio-derived telemetry data to its servers, even when the microphone was muted. Although these packets are transmitted at a low rate (once per minute), their audio-derived values correlate with the volume levels of background activities.

To verify our hypothesis, we present a classifier to fingerprint background activities from these telemetry values. Training this classifier was also challenging. Without access to the proprietary algorithm that generates the audio-derived data, it is not feasible to use existing audio datasets to create training data for the classifier. Furthermore, the training data has to represent real-world situations, including realistic noise types and varying volume levels. We address this challenge by collecting Webex-based telemetry data corresponding to more than 200 hours of background activities. Our evaluation of the classifier with over-the-air data shows that telemetry data from Webex can conclusively fingerprint a set of popular user activities, such as music, chatting, and vacuum cleaning. We demonstrate that even with user data that is compressed and transmitted on a minute-by-minute basis, some activities have unique patterns that are discernable in Webex’s telemetry data. 

Our key contributions are as follows.

– *User Study:* We conduct a user study with 223 VCA participants to assess their understanding and expectations regarding the mute button (Sec. 3). 

– *Audio Access Tracing:* We analyze VCAs’ finegrained access to the microphone; we found that most VCAs have access to audio-derived data even when the user is muted (Sec. 4).

– *Webex-based Case Study:* We conduct a thorough system-level study of the Webex Windows client. We discover that, in contradiction to its claims in the privacy policy, Webex sends periodic audioderived data to its servers (Sec. 5).

– *Background Activity Detection*: We present a design for a machine learning model the infers background activities from Webex’s audio-derived data (Sec. 5.3). 

– *Mitigation Strategies:* We distill our findings in the form of mitigation strategies that provide users with better control over the mute button (Sec. 6).

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-1/">1 Introduction</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-2/">2 Related Work</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-3/">3 User Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-4/">4 Analysis of Mute Button</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-5/">5 Webex Case Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-6/">6 Discussion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-7/">7 Conclusion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-8/">Acknowledgements</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-9/">References</a></li></ul>

***

</div>
