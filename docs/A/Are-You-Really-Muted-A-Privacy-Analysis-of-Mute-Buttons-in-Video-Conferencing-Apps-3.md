---
layout: default
title: 3 User Study
parent: § Are You Really Muted? - A Privacy Analysis of Mute Buttons in Video Conferencing Apps 
grand_parent: A 
nav_order: 30 
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

## 3 User Study
Our first objective is to study the user perceptions of the mute button along with their understanding of its functionality. Towards that end, we conduct an online user study with 230 VCA users. Our study aims to answer two questions about VCA users: (1) *When do they think the VCA accesses their microphone?* and (2) *When do they think the VCA should access their microphone?*. Answering these questions allows us to characterize the user’s understanding and expectations of the mute button, respectively. In the following, we describe the design of the user study, the recruitment, and the findings.

### 3.1 Study Design
We designed a Qualtrics survey<sup>1</sup> to help answer our research questions. We used partial disclosure to hide the fact that the study was about the privacy implications of the mute button. The description of the survey and its title focus on capturing the users’ general experience with VCAs during the pandemic. The survey has four major sections; the first section collects optional demographic information. The second section collects information about the preferred VCA and frequency of usage.

The third section asks the respondents about their experience with the mute button. We adapt the questions from Lau et al. [26], which studies the mute button in smart speakers. In particular, we probe the users about their usage of the mute button, their reasons, and their understanding of its functionality using questions in Table 1. This section contains three open-ended questions and two multiple-choice questions.

The last section adopts a refined version of Internet Users’ Information Privacy Concerns (IUIPC-8) from Groß [21] to measure the participants’ privacy concern. This survey section contains the first mention of privacy, after the respondents have answered the questions related to the mute button. Finally, the survey includes two attention checker questions and was exempted by the IRB at our institution.

#### Participant Recruitment and Demographics
We recruited participants from the Prolific data collection platform. We employed Prolific’s prescreening criteria to enforce gender balance and to forward the survey to only those who have worked from home during the COVID-19 pandemic with 90% approval rate in previous studies. Before conducting the survey, we conducted a pilot study with 15 users to calibrate the payment and ensure that the study design is clear. Through Prolific, we were able to recruit 299 participants, where we kept 223 responses from participants who passed the attention checkers. The median completion time was 8 minutes, and we paid each participant $1.5; the median hourly rate was $11.

Among our participants, 96.8% are between 18 to 44 years old, 63.2% of them work in sales, service, management and professional industry, and 82.5% achieved at least a college degree. During COVID-19, 54.7% of our participants answered that they have used video conferencing apps more than once a day and 40% of them used once a day or once every few days. The most popular video-conferencing app among the participants is Zoom, and the other popular apps include Microsoft Teams, Google Meet and Cisco Webex.

We map the responses to the IUIPC-8 question to a score based on seven-point Likert scale, representing participant’s privacy attitudes. The average scores is 2.02 for all participants, implying that most participants are privacy-conscious in our study. The value of Cronbach Alpha Index is 0.7915 for privacy attitudes responses from 223 participants, which indicates a good internal consistency and reliability of these responses.

![Table 1. The main questions used in the user study. Q1-Q3 are open-ended questions with answers coded by researchers. Q4 and Q5 are multiple choice questions where the participant selects one or more statements from S1-S5 in response. The full list of questions is available in the Appendix.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-table-1.png)

**Table 1.** The main questions used in the user study. Q1-Q3 are open-ended questions with answers coded by researchers. Q4 and Q5 are multiple choice questions where the participant selects one or more statements from S1-S5 in response. The full list of questions is available in the Appendix.

![Fig. 1. The distribution of the codes about reasons users reported for using the mute button as extracted from answers to Q1.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-1.png)

**Fig. 1.** The distribution of the codes about reasons users reported for using the mute button as extracted from answers to Q1.

![Fig. 2. The distribution of the codes about the background activ- ities as extracted from answers to Q2.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-2.png)

**Fig. 2.** The distribution of the codes about the background activ- ities as extracted from answers to Q2.


***
<sup>1</sup> The full survey can be found here: https://osf.io/szd4x/
{: .fs-2}
***

### 3.2 Findings
We report the key findings from our user study, through analyzing the participants’ responses. We coded the responses to the open-ended questions (*Q1*, *Q2*, and *Q3* ) following this procedure. For each question, two authors independently coded the responses, after which they generated a consolidated codebook describing the responses. For *Q1*, we settled on five codes about the reasons for which participants use the mute button. For *Q2*, the codebook consists of twelve codes describing the background activities. The codebook for Q3 contains nine codes representing the participants’ description of the mute button operation. Then, each coder independently coded the first 30 responses for each question; the resulting Cohen’s kappa is 0.85 for *Q1*, 0.90 for *Q2*, and 0.82 for *Q3*, indicating strong agreement [30]. The coders split and coded the rest of the responses. See detailed codebooks of the open-ended questions in Appendix E.

**Usage Patterns:** We start by analyzing the responses to *Q1*, where 214 participants out of 223 indicated that they have used the mute button before. The responses for *Q1*, as shown in Fig. 1, reveal two main reasons why users employ the mute button: (1) hide background activities and (2) avoid interrupting or disturbing others on the call. It is interesting that the participants regard the mute button as a privacy control measure to prevent others from hearing them. For example, *P19* mentioned the reason for using the mute button is: *"So that people won’t listen to private activities or conversations.”*

![Fig. 3. The distribution of the codes about the users’ understand- ing of the mute button operation from answers to Q3.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-3.png)

**Fig. 3.** The distribution of the codes about the users’ understand- ing of the mute button operation from answers to Q3.

The responses for *Q2* indicate an array of background activities the participants perform while muted, as indicated in Fig. 2. Participants mentioned more than one activity in their responses; For example, P166 mentioned: *“Talking, loud video watching, cat activity (meows, occasional falling and crashing of items), cleaning (including vacuuming).”* The most prevalent activity was related to preparing food, cooking, snacking, or eating. Other frequent activities include chatting, watching TV, cleaning, typing, or watching online videos. We elaborate more on these background activities in Sec. 5.3.

![Fig. 4. The distribution of responses to Q4. The statements S1- S5 are defined in Table 1.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-4.png)

**Fig. 4.** The distribution of responses to Q4. The statements S1- S5 are defined in Table 1.

![Fig. 5. The distribution of responses to Q5. The statements S1- S5 are defined in Table 1.](https://statics.bsafes.com/images/papers/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-fig-5.png)

**Fig. 5.** The distribution of responses to Q5. The statements S1- S5 are defined in Table 1.

**Understanding of the Mute Button:** As indicated earlier, we asked the participants two questions (*Q3* and *Q4* ) to gauge their understanding of the mute button. To gain initial insights into the participants’ understanding of the mute button, we study the coded responses to *Q3*, as evident from Fig. 3. The most frequent response was that by using the mute button, the app prevents others in the call from hearing the user. For example, P16 indicated that: *“It doesn’t produce my audio on the other participant’s platform or computer.”* Moreover, other participants focused on the interface change when the mute button is pressed, as in the case of P119 : *“It shows me the mic with a line crossing it signalling it is not working.”* . Meanwhile, 59 participants mention that the mute button disables the microphone. For example, P161 mentions: *“When I press the mute button, my microphone is muted and disabled on the app from picking up any sound waves from where I am.”*

For Q4, we provide five situations, S1-S5, in our user study as shown in Table 1. The responses to Q4 indicate that the participants exhibit a diverse understanding of the operation of the mute button, as shown in Fig. 4. Out of the 223 responses, 69 participants selected only *S4* as a response to Q4. These participants think the app only accesses the microphone when they are in the meeting and the mute button is not pressed.

Further, we found that the participants were split in their selection of *S3* as a response to Q4. Nearly half of the participants (111) did not select *S3*, indicating that the app does not access the microphone when the mute button is pressed. The other half indicated that the app accesses the microphone, even when muted. Interestingly, we observe that 49 participants selected *S2*, *S3*, *S4*, *S5* when responding to Q4, indicating that the app accesses the microphone as long as it is running. Also, we observe that 36 participants selected *S3* and *S4*, indicating that the app accesses the microphone as long as the user is in a meeting. In all the cases above, we found no correlation between the responses and the IUIPC-8 privacy attitude scores.

**Expectations of the Mute Button:** Finally, we analyze the responses to Q5, about when do the participants think the VCAs should access the microphone. The responses reveal that the participants have clear expectations about the operation of the mute button, as indicated in Fig. 5. Among the 223 responses, 173 participants selected only S4 as a response to Q5. These participants indicated that the app should only access the microphone when the meeting is running and the user is unmuted. Interestingly, 27 respondents selected both S3 and S4 as a response to Q5.

In conclusion, the results from the user study suggest that the user’s understanding of the mute button does not match their expectations of its behavior. In the rest of this paper, we study the actual behavior of the mute button and analyze whether it matches user understanding and expectations.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-1/">1 Introduction</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-2/">2 Related Work</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-3/">3 User Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-4/">4 Analysis of Mute Button</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-5/">5 Webex Case Study</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-6/">6 Discussion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-7/">7 Conclusion</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-8/">Acknowledgements</a></li><li> <a href="/docs/A/Are-You-Really-Muted-A-Privacy-Analysis-of-Mute-Buttons-in-Video-Conferencing-Apps-9/">References</a></li></ul>

***

</div>
