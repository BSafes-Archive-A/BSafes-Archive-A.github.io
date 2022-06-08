---
layout: default
title: 7 Conclusion   
parent: § Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps 
grand_parent: A
nav_order: 70 
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

## 7 Conclusion
In this paper, we present the first large scale study of VCA mute-button privacy. Our user study shows that users are unaware of Webex listening to their microphone while muted. We examined all widely used VCAs and desktop operating systems and pinpointed a potential privacy leakage within Webex. We discovered that while muted, Webex continuously reads audio data from the microphone and transmits statistics of that data once per minute to its telemetry servers. Using runtime binary analysis tools, we intercepted unencrypted copies of the telemetry data before it was transmitted. We used over 180 hours of simulated background noise to build a data set for classification. Our classifier achieves an 81.9% macro accuracy on identifying six common background activities using intercepted outgoing telemetry packets when a user is muted. Operating system vendors can establish a stronger permission model for the microphone by implementing an OS-level software mute.

Our analysis of the VCAs provide new insight to a user’s understanding of the mute button. We show that Webex transmits audio-derived data while the user is muted. Counter-measures should be supported by policies and regulations to ensure that users’ private background activities are not monitored.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-1/">1 Introduction</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-2/">2 Related Work</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-3/">3 User Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-4/">4 Analysis of Mute Button</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-5/">5 Webex Case Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-6/">6 Discussion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-7/">7 Conclusion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-8/">Acknowledgements</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-9/">References</a></li></ul>

***

</div>
