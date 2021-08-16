---
layout: default
title:  METHOD 
parent: § An exploratory study of mode efficacy in cybersecurity training
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

## METHOD

### Participants
Two-hundred and nine undergraduate students at a top tier university in the United States in a computer science program participated in this study. These students have an interdisciplinary background including in business, human factors, operating systems, and networks. This population was selected because they have sufficient experience with these topics to understand cybersecurity. The students were randomly assigned to one of four sections of the cybersecurity course (described in more detail under Instrumentation). Section 1 (lecture/lab) had 46 students, ages ranged from 20 to 23, 7 were females. Section 2 (lecture/lab + simulation) had 53 students, ages ranged from 19 to 23, 8 were females. Section 3 (lecture/lab + live activity) had 61 students, ages ranged from 20 to 25, 11 were females, and Section 4 (lecture/lab + simulation + live activity) had 49 students, ages ranged from 21 to 23, 9 were females. A knowledge pre-test was given to all participants prior to commencement. The distribution was even across all four sections, and there was no statistical difference in pre-test scores across the sections; hence there was no need to adjust for pre-test scores in the analysis. Nevertheless, there was some variance, hence we used the pre-test scores as a covariate.

### Instrumentation
To address instruction variability, the same instructor taught all four sections over three semesters, and the same textbook was used (Workman et al., 2013) and core instruction was used in all four sections and employed educational best practices (as described earlier). The course assignments and exams were identical, and presentation materials were the same, except where noted below. The course content covered threats and countermeasures to be applied to a variety of non-specific cybersecurity threats to systems and applications. The materials also specifically covered the OWASP top 10 vulnerabilities for Web applications.

At crucial learning points during the presentations of the materials, students were prompted to respond to questions or suggest remediations to programming code, firewalls, open ports, and so forth. There were several group projects, and one group presentation. Laboratory exercises included working with IDS (host and network), threat modeling tools, network analyzers, infrastructure monitors, log analyzers, port scanners, penetration testers and vulnerability scanners, writing a cryptographic program and then running static and dynamic code analyzers against their code.

The baseline instruction (Section 1) consisted solely of the classroom and laboratory work, along with quizzes from the textbook, a mid-term and a final examination. Section 2 replaced the textbook quizzes and with simulation challenges. The simulation had two parts, the first presented a series of scenarios; for example, it rendered a Webpage with a login, then had the participants follow instructions to enter various kinds of information, such as to determine whether the page was vulnerable to a SQL Injection. The participants would then try to identify the vulnerable code and correct remediation. The second part was a guided game in which participants would assume a role as attacker or defender (ultimately both) in which they would try to exploit or select a solution to remediate the vulnerabilities. Section 3 replaced the textbook quizzes with two live competitive activities. In the first, the environment incorporated the OWASP Mutillidae with modifications, and the second was an activity with CTF365. Participants would take active roles in trying to compromise systems, while simultaneously striving to find and fix vulnerabilities. Section 4 replaced the quizzes, midterm and final with first the simulation challenges, followed by the live activities.

![Figure 2: Sample Fixtures and Panes for Integrated Simulation](https://statics.bsafes.com/images/papers/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-fig-2.png)
Figure 2: Sample Fixtures and Panes for Integrated Simulation

At the end of the course for all four sections, students underwent an assessment. The assessment tested analytical and procedural skills, in other words, how well students identified vulnerabilities and took appropriate actions. This was done by two means. This first part were timed case studies of attacks, countermeasures, and remediation. The case studies were based on real incidents, and presented all the facts but did not specify the flaw(s). The participant had to correctly identify the main vulnerability, and any additional issues. One case study, for instance, presented a problem in which open-source Web Application Firewall (WAF) was misconfigured to allow too many permissions, violating the least-privilege principle. This was followed by a Server-Side Request Forgery (SSRF) attack, and subsequent failures by humans-in-the-loop to notice the alarms from the monitors that signaled unusually large downloads from Amazon Web Services (AWS) S3 buckets. Case studies had clear and definable vulnerabilities and remediation solutions.

The second part of the assessment involved an applied lab in which participants had to scan systems, log files, routers, firewalls, and so forth, to find ten major vulnerabilities in a Web application and correctly remediate them. Thus, this assessment part of our study added an active detection element, and consisted of a platform with a simulated network, and attack modules that would carry out various kinds of attacks. Participants utilized tools they had worked with such as intrusion detection systems, monitors and so forth to identify the attack and take corrective actions. The attack/detection/remediation activity consisted of several components. At a macro-scale, these included a simulation engine with selectable infrastructure templates; attack modules that executed a particular attack; an API set that would allow custom applications and attack modules; a database to store state and other information, a student monitoring system to track student accuracy and point allocations for competitions; and a set of open source monitoring tools that the student would use to identify the attack.

Five hundred points were allotted to this assessment, for which students received T-Shirts and mugs, but were not included in the students’ grades. The case studies were worth 1/2 of the points with 1/2 allocated to the lab. These were used as the dependent variable performance scores in the analysis.

![Figure 3: Sample Attack/Detection/Remediation Fixtures and Panes](https://statics.bsafes.com/images/papers/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-fig-3.png)
Figure 3: Sample Attack/Detection/Remediation Fixtures and Panes

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-1/">INTRODUCTION</a></li><li> <a href="/docs/A/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-2/">THEORY AND HYPOTHESES</a></li><li> <a href="/docs/A/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-3/">METHOD</a></li><li> <a href="/docs/A/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-4/">RESULTS</a></li><li> <a href="/docs/A/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-5/">DISCUSSION AND CONCLUSIONS</a></li><li> <a href="/docs/A/An-exploratory-study-of-mode-efficacy-in-cybersecurity-training-6/">REFERENCES</a></li></ul>

***

</div>
