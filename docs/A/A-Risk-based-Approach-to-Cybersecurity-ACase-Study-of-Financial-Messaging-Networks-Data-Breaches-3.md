---
layout: default
title: A CLOSER EXAMINATION OF SWIFT DATA BREACHES
parent: § A Risk based Approach to Cybersecurity - A Case Study of Financial Messaging Networks Data Breaches   
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

## A CLOSER EXAMINATION OF SWIFT DATA BREACHES
Technology is changing and shaping how organizations do work and how people perform tasks. The growth in information technology (IT) has enabled organizations in the banking sector to serve customers and manage high volumes of assets in a more effective and streamlined manner. At the same time, the financial industry also becomes a highly profitable target for criminals due to various cybersecurity challenges.

Criminals have launched a series of cyberattacks on the global banking system through the SWIFT messaging system. One of the high-profile heists in the early days involved phony transfers of $81 million from the central bank of Bangladesh in February 2016. Hackers first introduced a malware into the bank’s server to steal login details for the SWIFT messaging system. They then successfully covered their infiltration traces by removing evidence from printed SWIFT messages in real time (Al-Mahmood, 2016). In addition, several other unauthorized bank transfers with the similar infiltration mechanism surfaced in other parts of the world. The criminals were able to operate the infiltration schemes successfully without being detected for months until the damages were done (Sharma, 2017).

### Analysis
According to a report by Reuters, SWIFT issued a private alert in April 2016 about fraudulent transfers across its network but withheld names of victims and the losses from those attacks (Finkel, 2016). The warning was the first indication that the popular Bangladesh attack was not a standalone event but one of related criminal schemes targeting the messaging platform. Later in the summer of the same year, an executive of the organization told a group of the association of banks in Singapore during a meeting that it was looking into twenty-six attempted attacks on banks (Burne & Sidel, 2017).

Researchers at Symantec discovered evidence in the Philippines bank hack which was related to the group involved in the hacks in Bangladesh central bank and Tien Phong Bank in Vietnam (Symantec, 2016). An examination of SWIFT’s practices indicated that it was not fully prepared for the toughest challenges the attacks brought (Burne & Sidel, 2017). Even though it thoroughly locked down the heart of its network, the emergence of reports of subsequent attacks continued raising concerns about vulnerabilities in the messaging system run by SWIFT.

In a Cyber Security and SWIFT hacking conference organized by the National Banking Institute of Nepal with an audience of over 150 bankers, it was discovered that virtually all the bankers present did not use genuine software at their offices (Sharma, 2017). Pirated software has been regularly cited as a major vulnerability source resulting in out-ofdate patches, updates, and cybersecurity safeguards. This worrisome fact further corroborates the belief that more rigorous and effective cybersecurity framework and standards are much needed to be enforced across the SWIFT member banks.

The SWIFT network attacks were carried out in the same pattern. Virtually all the attacks involved the use of malware on the banks’ network systems. The attackers combined this method with employee credentials to get on the banks’ networks but none of those attacks affected SWIFT’s core network directly. The success of the attacks was mostly the outcome of the weaknesses in the security measures put in place by those banks. When examining the major attacks closer, a common pattern can be found across different data breaches in terms of attack vectors, mechanisms, and vulnerabilities. First, the attackers used state-of-the-art skills to gain access to the banks’ networks, then instituted command and control to direct information using a backdoor for their secret hideouts. Soon as they gained access to the banks’ networks, the next thing was to sort out major transaction applications like the SWIFT messaging network applications. Once sorting out, the attackers studied the flow of information and collected credentials for the SWIFT Alliance Access (SAA), SWIFT Alliance Web Platform and SWIFT Alliance Gateway (SAG), looking for resources with the necessary characteristics such as IP addresses, port numbers, files, Web pages and digital certificates. After the surveillance was completed, the onslaught method was then created using gained resources about the banks’ operations, server distribution, credentials, and SWIFT’s application units. Armed with these details, the attackers could then set up phony messages or alter actual messages to allow transfers to controlled accounts. Finally, when the money got into the controlled accounts, it was then moved immediately either as cash or transformed into bitcoin and scattered around to frustrate the evidence trail.

Three strains of malware used to exploit the SWIFT networks in South-East Asia are named as Backdoor.Fimlis, Backdoor.Fimlis.B, and Backdoor.Contopee (Symantec, 2016). One piece of interesting forensics evidence is that Backdoor.Contopee shared part of the common source code with another malware named Trojan.Banswift that was used to manipulate transactions in the Bangladesh attack (APSM, 2016). It further corroborates the speculation that Lazarus group who was blamed for the Sony Entertainment attack was involved in some of those SWIFT data breaches as well.

In summary, these attacks are indications of the continuous threats cybercriminals posing to payment systems, through which they can access large amounts of money transferred to SWIFT and its wide community. Furthermore, these incidents also imply the need for stronger security protocols throughout the organizations. Common attack tactics (FSecure, 2018) are illustrated in Figure 1.

Figure 1.

*Common Attack Tactics Carried Out in SWIFT Hacks*

![Common Attack Tactics Carried Out in SWIFT Hacks](https://statics.bsafes.com/images/papers/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-fig-1.png)


A more structured detailing of each case with a comparison across all ten cases is demonstrated in Table 1.

Table 1

*Summary of Ten SWIFT Hacking Cases from 2013-2018*

![Summary of Ten SWIFT Hacking Cases from 2013-2018](https://statics.bsafes.com/images/papers/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-table-1.png)

### Regulations and Legislations
While SWIFT could advise its member banks to adopt certain minimum-security standards, no designated organization was in charge of how central banks and financial institutions should secure their payment networks. The SWIFT data breaches shed light on the primary challenge in fighting cybercrimes, which is the blanket nature of online environments as well as the complexity involved in investigations and prosecution.

The cross-border nature of cybercrime creates a huge obstacle for countries to successfully trace the origins and hold them accountable without help from others (Brenner, 2007). Despite the efforts by many nations across the world to combat cybercrimes, criminal activities continue to flourish and become heightened in Africa and Asia (Butkovic et al., 2019). For example, cybercrimes committed in Europe or the U.S. stand a higher chance of being punished than those committed in other regions because of the attitude of government in those places. Another reason is the difference in lawmaking patterns that do not touch on all areas involved in cybercriminal activities. Such gap introduces a lot of exploitable legal means of escape, which increases the likelihood of cybercrime in those countries.

Cybersecurity-related incidents are usually not reported, and when they are, the prosecutors are opposed by difficult challenges. For instance, many developing nations do not have laws that address cybercrimes. The extant laws formulated for the security of tangible properties are not armed to handle their counterparts in the cyberspace. Even in the areas where legislation exists for cyber offences, investigations and prosecution of these type of crimes are often obstructed due to the constraints in investigative competence and difficulties of collecting digital evidences across the country’s judicial structure.

Multiple daring cyberattacks on banks across the world within several years woke up executives from complacence to a world of digital truth. Prior to these attacks, security requirements for the network was prescribed in a handbook with guidelines that were mostly voluntary and rarely enforced. Such situations have changed since SWIFT revised its procedures in 2017 to require member banks of a demonstration of annual security compliance with new protocols in response to the attacks (Baert, 2016). Sixteen new controls were rolled out, including tighter password security (e.g., two-factor authentication) and an order for banks to update their software regularly (Burne & Sidel, 2017). An anomaly detector designed to flag and suspend unusual payment instructions was also part of the controls. It was believed the new security toolkits and controls could easily mitigate the recent heists if a version of the tool was implemented earlier instead of relying on banks to safeguard their own security (Burne, 2017).

In early 2017, as part of SWIFT's global payments innovation (GPI) initiative, private blockchain was carried out in a closed environment, with specific profiles and strong data controls, privileges, and access being diligently monitored (SWIFT, 2017). After SWIFT took all these measures to protect its customers, fresh attacks were still recorded in the following years as highlighted in some of the cases above, proving these criminals had more advanced knowledge and capability on manipulating the banking system than previously believed.

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-1/">
BACKGROUND INTRODUCTION</a></li><li> <a href="/docs/A/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-2/">
RESEARCH METHODOLOGY</a></li><li> <a href="/docs/A/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-3/">
A CLOSER EXAMINATION OF SWIFT DATA BREACHES</a></li><li> <a href="/docs/A/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-4/">
DISCUSSION</a></li><li> <a href="/docs/A/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-5/">
COUNTERMEASURES</a></li><li> <a href="/docs/A/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-6/">
CONCLUSION</a></li><li> <a href="/docs/A/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-7/">
REFERENCES</a></li></ul>

***

</div>
