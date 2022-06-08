---
layout: default
title: 4 Analysis of Mute Button
parent: § Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps
grand_parent: A
nav_order: 40 
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

## 4 Analysis of Mute Button
Following the results from our user study, we investigate whether the actual behavior of VCAs matches user expectation by focusing on desktop environments. Our objectives are to determine: (1) if VCAs actively access the microphone when muted and (2) what kind of indicators (if any) they give users that the microphone is being accessed.

### 4.1 Overview of VCAs and Platforms
There are two broad categories of runtime environments in which VCAs execute: native apps that run directly in the operating system and web apps hosted by a web browser. Each has a different permission model for accessing the microphone. Most of the VCAs we study in this work have a native app implementation for the major operating systems (macOS and Windows) and a web app used on unsupported platforms (Linux and others). The VCAs that we studied (listed in Table 2) exhibit a consistent look and feel across platforms. Their implementation, however, on each platform is different, due to syscall interfaces and display APIs. Zoom on Windows, for example, is a self-contained Windows-specific software package. Zoom on macOS has a similar user interface to its Windows counterpart, but the underlying code base appears to be different.

![Table 2. A summary of the VCAs we studied. v: native app ◦: web-based app X: No implementation.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-table-2.png)

**Table 2.** A summary of the VCAs we studied. v: native app ◦: web-based app X: No implementation.

Native apps can collect data from the microphone with few restrictions. Web apps—implemented in JavaScript— request access to the microphone through a web browser, which generally has more restrictive policies for data collection and more tools that allow the user to control the app’s access to hardware.

#### Browser Based Apps
Browser-based VCAs rely on their host browser to mediate their interactions with the operating system and the hardware. The browser-based VCAs that we studied are implemented entirely in JavaScript, and they use a special-purpose API called WebRTC [19] for driver interactions—including microphone accesses—that are typically not available to web apps. WebRTC is a native interface written in C++ and C, acting as a driver for the hardware within the browser that can call the operating system to access the microphone. Information transferred by WebRTC is subject to controls and policies of the browser. Web-based VCAs are sandboxed inside the browser and do not circumvent WebRTC.

There are two ways a user can mute a web-based VCA: (1) using a browser-level mute button or (2) using a WebRTC software mute signal from the app. Both techniques are more trustworthy than app-controlled mute because they are implemented and enforced by the browser, not the app.

The browser-level mute button completely disables microphone access to the VCA, as if the microphone is not active within the system. Web-based VCAs also implement an app-level mute button, which has similar functionality to the browser-level mute: it enables a software mute inside of WebRTC, disabling all audio transfers from the microphone. Users must trust the web-based VCA to use the software mute functionality rather than some internal mute button implementation. We found that all of the studied apps use the WebRTC mute functionality correctly. Furthermore, it is straightforward to verify that web-based VCAs correctly use the software mute functionality through source code audits and the WebRTC debugger built into Chromium.

#### Native Video Conferencing Apps
Native VCAs can directly call the operating system to retrieve audio data from the microphone. Most of them abide by the operating system (OS) rules to access the microphone data, with some exceptions. The OS imposes fewer restrictions on native apps than the browser runtime environment imposes on web apps.

All operating systems utilize a permissions-based access system to retrieve data from the microphone. In most cases, apps must have explicit permission to access hardware resources such as the microphone. Each app follows three steps to configure and use the microphone: (1) user approval, (2) driver initialization, and (3) audio data retrieval. Windows and macOS require the user to explicitly provide permission for each app, which the app retains indefinitely while it runs (unless the user revokes the permission).

Once the user approves the access for the app, the app must create an interface to the audio drivers. Some OSes, like Windows, offer users a visual cue that indicates when the app is using the microphone. But unlike the WebRTC browser runtime, none of the major operating systems we are aware of support enforce a software mute. This lack of an OS-mediated software mute means each native app must implement its own internal mute functionality. Even when a software mute is active, apps can still access the microphone while the user is muted.

### 4.2 Analysis Methodology
To understand what happens when the user presses the mute button on desktop VCA clients, we utilize various OS-based tools to trace audio data as it is transferred from the operating system to the app. Our objective is not just to establish whether the app has permission to access the microphone when muted. Instead, we aim to understand whether the app actually reads microphone data when the user is muted.

#### Linux
Audio data transfer from the Linux kernel to the VCAs is mediated through PulseAudio and ALSA. ALSA is a kernel subsystem that provides a kernel-level interface to the audio hardware, and PulseAudio is a userland process that interfaces with ALSA and provides higherlevel features like mixing and multiplexing. All the VCAs we studied interface with the userland PulseAudio process.

To intercept audio data in transit from PulseAudio to a VCA, we use the DynamoRIO runtime code manipulation system [1], which allows us to inject foreign code into a running process. Our additional code, written in C, is called each time a fresh buffer of microphone data arrives from PulseAudio. We write the audio buffer’s address in the process’s memory space to a log file. We then trace the buffer addresses from the log using IDA Pro. The contents of the buffer are the raw audio bytes from the microphone. DynamoRIO oversees the process’s execution by loading and running modified basic blocks one at a time, which substantially slows the app’s execution, occasionally causing it to crash.

#### Windows
Although it is possible to track microphone access by monitoring the system registry [22], we were not able to track transfers in real time from the microphone to the VCA. The registry only records times at which an app opens or closes a connection to an audio device. The OS registry—linked to a visual indicator in the system tray—does not distinguish detailed API calls which encode information about whether a VCA is reading audio data or accessing status flags about microphone activity.For fine-grained and detailed information, we intercept syscalls from the VCA to the operating system.

In Windows 10, syscalls are obfuscated behind a userland API library which acts as an intermediary between the apps and the OS. The Windows API library is similar to the Linux/Unix C library syscall wrappers, except that there is no one-to-one mapping between the parameters that the app passes to the API and the parameters that the API passes to the OS. Instead, the API functions as a higher-level wrapper around system calls, and there is no official documentation available from Microsoft detailing how to call the operating system directly.

Windows implements many special-purpose API functions for actions like accessing the microphone, which in Linux and Unix are all handled as files. We develop a two-step process to trace audio data in transit from the Windows OS to the native VCAs. First, we use a tool called API Monitor [12] to instrument the userland API with hooks to log pointers to the inputs and outputs of several microphone-related API calls. We then use a live binary analysis tool called x64dbg [4] to read the contents of the buffers out to a log file. We utilize an anti-anti-debugging library called Scylla-Hide [3], which hides the fact that an app is being debugged to prevent the app from crashing.

#### Chromium
Chromium acts as an intermediate layer between the operating system and the browser based VCAs. To verify whether web-based VCAs access the microphone while muted, we inject our own logging code in the source of Chromium. We instrument the following three browser functions in Chromium, which are responsible for transporting audio from the operating system to the VCA<sup>2</sup> . First, the browser initiates audio-related read_data function, which retrieves the raw microphone data from the operating system and stores it in a raw audio buffer. Then it calls encode and send_stream functions, which transforms the raw audio into an encoded stream and transfers the encoded audio stream to the web-based VCAs.

#### macOS
An audio subsystem manages microphone data created by Apple via AVFAudio or the AVAudioEngine interfaces [10]. These interfaces have the same purpose and interact with the audio hardware in userland. VCAs make a system call to mach_msg_trap within either an audio interface thread managed by Apple and retrieve

***
<sup>2</sup> Appendix B includes more details about the functions inside Chromium.
{: .fs-2}
***

raw audio bytes from the microphone. All of the VCAs we studied connect to the microphone using either of these interfaces and make the same system calls when reading bytes from the microphone.

To monitor VCAs’ microphone accesses we use a XCode tool called Instruments [9] and the standard Unix networking tool tcpdump. Instruments logs all system calls and their arguments to a user interface in the Apple system log. tcpdump records network traffic while any of the VCAs are running. We attach Instruments to a live VCA and perform a tcpdump on the networking interface to extract and monitor the dataflow from microphone to the VCA. We then observe the results from Instruments to correlate behavior patterns with with Windows evaluation. VCAs in macOS behave similarly to their Windows implementations.

### 4.3 Findings

To understand how VCAs consume microphone data, we conducted experiments on each app-OS combo shown in Table 2. We installed all VCAs and registered two accounts for each app on each of the four operating systems. The app-OS combinations that are only accessible in a browser are tested in Linux on Chromium. We initiated the meeting app for each meeting experiment and used the techniques explained above to trace microphone data from OS to VCA under two conditions: mute button toggled on and mute button toggled off. Most platforms we studied display a visual indicator to alert the user that an app is accessing the microphone<sup>3</sup> . We found three broad policies that VCAs follow to read data from the microphone while muted:

1. **Continuously sampling audio from the microphone:** apps stream data from the microphone in the same way as they would if they were not muted. Webex is the only VCA that continuously samples the microphone while the user is muted. In this mode, the microphone status indicator from an operating system remains continuously illuminated. 

2. **Audio data stream is accessible but not accessed:** apps have permissions to sample the microphone and read data; but instead of reading raw bytes they only check the microphone’s status flags: *silent, data discontinuity, and timestamp error.* We assume that the VCAs, like Zoom, are primarily interested in the silent flag to tell if a user is talking while the software mute is active. In this mode, apps do not read a continuous real-time stream of data in the same way as they would while unmuted. Most Windows and macOS native apps<sup>4</sup> can check if a users is talking even while muted but do not continuously sample audio in the same way as they would while unmuted. In this mode, the microphone status indicator in Windows and macOS remains continuously illuminated, reporting that the app has access to the microphone. We found that applications in this state do not show any evidence of raw audio data being accessed through the API.

3. **Software mute:** apps instruct the microphone driver to completely cut off microphone data. All of the web-based apps we studied used the browser’s software mute feature. In this mode, the microphone status indicator in the browser goes away when the app is muted, indicating that the app is not accessing the microphone.

The notable exceptions to these trends are the Microsoft VCAs (Teams and Skype) and Cisco Webex. Microsoft VCAs are much more difficult to trace because they do not use the standard Windows userland API. Instead, they directly make calls to the operating system. Since the Windows syscall interface is undocumented, we could not determine how Teams and Skype use microphone data when muted. More interestingly, we observe that Cisco Webex — unlike the rest of the Windows native VCAs — continuously accesses the microphone while muted. Using x64dbg, we were able to trace Webex’s copied audio buffer until that buffer reaches the stack. We discovered that while the app was muted, Webex’s audio buffer contains raw audio from the microphone. In the next section, we focus our data flow analysis on Cisco Webex in Windows because of its popularity<sup>5</sup> in the enterprise setting and, more importantly, its unusual behavior.

Recall that our user study reveals two main observations: participants are split whether the VCAs access their microphone while muted, and expect them to access the microphone only when they are unmuted. Our results from this section indicate that the participants

***
<sup>3</sup> Some Linux distributions do not provide any visual indication that the microphone is in use.
{: .fs-2}
<sup>4</sup> Except Skype and Teams, which we cannot observe because they do not use the conventional Windows API.
{: .fs-2}
<sup>5</sup> The monthly statistics from Cisco Webex include 600 million participants and 6 billion calls [42].
{: .fs-2}
***

are largely unaware of the operation of the VCAs. More importantly, the behavior of these apps violates user expectations. This mismatch between user expectations and app behavior highlights privacy issues with the design of the mute button.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-1/">1 Introduction</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-2/">2 Related Work</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-3/">3 User Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-4/">4 Analysis of Mute Button</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-5/">5 Webex Case Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-6/">6 Discussion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-7/">7 Conclusion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-8/">Acknowledgements</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-9/">References</a></li></ul>

***

</div>
