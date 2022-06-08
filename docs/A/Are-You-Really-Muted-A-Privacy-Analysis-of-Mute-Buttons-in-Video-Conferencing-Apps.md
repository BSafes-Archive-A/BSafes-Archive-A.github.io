---
layout: default
title: § Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps  
parent: A
has_children: true
nav_order: 9780500
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
This is the mobile-friendly web version of the [original article](https://ecommons.luc.edu/cgi/viewcontent.cgi?article=1286&context=cs_facpubs).
# Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps
{: .no_toc }

### Loyola University Chicago 
{: .no_toc }
Loyola eCommons

***

Computer Science: Faculty Publications and Other Works, Faculty Publications and Other Works by Department 

***

7-2022

### Yucheng Yang
{: .no_toc }
*University of Wisconsin - Madison*

### Jack West
{: .no_toc }
*Loyola University Chicago*, jwest1 'at' luc.edu

### George K. Thiruvathukal
{: .no_toc }
*Loyola University Chicago,* gthiruvathukal 'at' luc.edu

### Neil Klingensmith
{: .no_toc }
*Loyola University Chicago*, nklingensmith 'at' luc.edu

### Kassem Fawaz
{: .no_toc }
*University of Wisconsin - Madison*

<div class="youtube-container">
<iframe width="100%" src="https://www.youtube.com/embed/TtAShulBnmY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="youtube-video"></iframe>
</div>
**Video:** Loyola University Chicago Campus Up Close 

**Recommended Citation**
Yucheng Yang, Jack West, George K. Thiruvathukal, Neil Klingensmith, Kassem Fawaz, "Are You Really Muted?: A Privacy Analysis of Mute Buttons in Video Conferencing Apps", In Proceedings of the 22nd Privacy Enhancing Technologies Symposium, 2022.

This Article is brought to you for free and open access by the Faculty Publications and Other Works by Department at Loyola eCommons. It has been accepted for inclusion in Computer Science: Faculty Publications and Other Works by an authorized administrator of Loyola eCommons. For more information, please contact ecommons@luc.edu.
{: .fs-2}

1. TOC
{:toc}

## Abstract: 

Video conferencing apps (VCAs) make it possible for previously private spaces — bedrooms, living rooms, and kitchens — into semi-public extensions of the office. For the most part, users have accepted these apps in their personal space without much thought about the permission models that govern the use of their private data during meetings. While access to a device’s video camera is carefully controlled, little has been done to ensure the same level of privacy for accessing the microphone. In this work, we ask the question: *what happens to the microphone data when a user clicks the mute button in a VCA?* We first conduct a user study to analyze users’ understanding of the permission model of the mute button. Then, using runtime binary analysis tools, we trace raw audio flow in many popular VCAs as it traverses the app from the audio driver to the network. We find fragmented policies for dealing with microphone data among VCAs — some continuously monitor the microphone input during mute, and others do so periodically. One app transmits statistics of the audio to its telemetry servers while the app is muted. Using network traffic that we intercept en route to the telemetry server, we implement a proof-of-concept background activity classifier and demonstrate the feasibility of inferring the ongoing background activity during a meeting — cooking, cleaning, typing, etc. We achieved 81.9% macro accuracy on identifying six common background activities using intercepted outgoing telemetry packets when a user is muted.

</div>
