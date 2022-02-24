---
layout: default
title: RESULTS   
parent: § A Taxonomy of Cyberattacks against Critical Infrastructure 
grand_parent: A 
nav_order: 80 
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

## RESULTS
### Scenarios
While we are yet to see a true large warfare effort on a global scale, there have been numerous instances when critical infrastructure and industrial control systems (ICS) have been attacked. Figure 3 shows the history of these attacks over the last two decades and identifies some of the main actors on the global arena that have the potential to cause devastating damages. Some of these countries are USA, Russia, China, North Korea, Israel, and Ukraine. Even though it is very difficult to prove with certainty that an attack was funded by a particular state, there is some information about state-funded cyberarmies such as the ones in China (Hvistendahl, 2010) and North Korea (Haggard & Lindsay, 2015).

![Figure 3. History of Cyberattacks Globally in ICS – adopted from Azarcon (2017)](https://statics.bsafes.com/images/papers/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-fig-3.png)  

*Figure 3. History of Cyberattacks Globally in ICS – adopted from Azarcon (2017)*

For the purposes of this study, we used three scenarios to illustrate possible types of cyberattacks against critical infrastructure. Those were informed based on publicly available data on Stuxnet virus, the Ukrainian power grid shutdown, and the numerous ransomware attacks against government facilities in the US. First, we present the scenario, then we test to see whether our taxonomy can effectively explain it, and then we examine possible controls to increase the guardianship aspect of the RAT used to inform the taxonomy development.

### Stuxnet
When it comes to cyberterrorist attacks, a real massive cyberwar on a global scale is yet to happen. However, this does not mean that it will not happen one day. Stuxnet opened the door to this type of crime. The purpose of the Stuxnet worm was to sabotage Iran’s uranium enrichment program, not spread terror. But the cyberweapon’s demonstration effect was enormous, showing the world how cyberterrorism could potentially cause substantial physical damage to critical infrastructures by attacking the computer controllers and SCADA systems that regulate industrial machinery.

The Stuxnet code has spread to computer programmers and hackers around the world. However, its sole victim was the electrical motors and industrial controllers used at Natanz and it did not cause any known damages to other devices (Farwell & Rohozinski, 2011). Almost a decade later, it is still unclear whether non-state hackers have the capacity and the willingness to modify and learn from the code in Stuxnet and other cyber-weapons developed by states to attack other SCADA systems in similar ways. Such uncertainty is troublesome and as Kenney (2015) suggests, “policymakers and computer security professionals should devote greater resources to understanding the potential for non-state actors to exploit cyberweapons developed by states and how to stymie the spread of this malicious code” (p. 127).

Based on this information, we can classify Stuxnet as follows:

- CPS components: cyber-physical 

- Hacker motivation: political and economic 

- Security: Threats (external, man-made), vulnerabilities (technical), and controls (vulnerability scanning, penetration testing, log monitoring, and auditing).

What this shows is that Stuxnet is a complex type of cyberattack against critical infrastructure and it can target more than one of the proposed dimensions in the taxonomy. We were expecting this because most SCADA cyberattacks are quite sophisticated and attackers rarely have a single reason to breach such systems.

The value of the taxonomy comes from the fact that based on the attacker motivation per RAT, we can tailor our controls and provide more efficient means of guardianship of our critical assets such as developing plans for identifying and responding to incidents related to national security infrastructure. Being able to detect cyberattacks and respond to them in a comprehensive and timely fashion is crucial for any entity.

### Ukrainian Power Grid Shut Down
In December 2015, the Ukrainian Kyivoblenergo, a regional electricity distribution company, reported service outages to customers that were due to a third party’s illegal entry into the company’s computer and SCADA systems. Over 225,000 customers in various areas were affected by the power loss and the Ukrainian government officials claimed the outages were caused by a cyberattack, and that the Russian security services were responsible for the incidents (Lee et al., 2016)

In terms of capability, the attackers demonstrated a variety of capabilities, including spear phishing emails, variants of the BlackEnergy malware, and the manipulation of Microsoft Office documents that contained the malware to gain a foothold into the IT networks of the electricity companies (Lee et al., 2016). They showed the capability to gain a foothold and harvest credentials and information to gain access to the ICS network.

Additionally, the attackers proved expertise, not only in network connected infrastructure, such as Uninterruptable Power Supplies (UPSs), but also in operating the ICSs through supervisory control system, such as the Human Machine Interface. The SANS report (Lee et al., 2016) presents a level of sophistication of a cyberattack that only a state-funded entity would possess and it also presents some recommendations for critical infrastructure facilities when it comes to cyberterrorism defense.

Based on this information, we can classify the Ukrainian power grid shut down as follows:

- CPS components: physical 

- Hacker motivation: political 

- Security: Threats (external, man-made), vulnerabilities (technical), and controls (vulnerability scanning, penetration testing, log monitoring, and auditing).

Similar to the Stuxnet virus, the attack against the Ukrainian power grid demonstrates the motivation of nation-state actors to establish power and dominance over other countries and showcase their ability to control critical infrastructure systems. This perfectly exemplifies the need to provide more rigorous guardianship and controls to prevent other attacks like that in the future.

### Ransomware Attacks
And finally, our third scenario is based on the numerous ransomware attacks that have been on the rise in the last few years. Some examples include WannaCry and Ryuk. WannaCry is a ransomware worm that spread rapidly through several computer networks in May of 2017. After infecting Windows computers, it encrypts files on the hard drive, making them impossible for users to access, then demands a ransom payment in bitcoin in order to decrypt them.

A number of factors made the initial spread of WannaCry particularly significant: it struck a number of important and high-profile systems, including many in Britain's National Health Service; it exploited a Windows vulnerability that was suspected to have been first discovered by the NSA; and it was linked to the Lazarus Group, a cybercrime organization that may be connected to the North Korean government (Fruhlinger, 2018).

Another type of ransomware attack attributed to the same Lazarus Group in North Korea is Ryuk. Unlike the common ransomware, systematically distributed via massive spam campaigns and exploit kits, Ryuk is used exclusively for tailored attacks. In fact, its encryption scheme is intentionally built for small-scale operations, such that only crucial assets and resources are infected in each targeted network with its infection and distribution carried out manually by the attackers.

This, of course, means extensive network mapping, hacking and credential collection is required and takes place prior to each operation. Its alleged attribution to Lazarus Group may imply that the attackers are already well experienced in the targeted attacks domain, as seen by attacks such as the breach of Sony Pictures in 2014 (Cohen & Herzog, 2018).

Some recent victims of such ransomware attacks are the City of Baltimore, Jackson County, and the Atlanta airport. It is interesting to note that Jackson County was one of the few who decided to pay the cyberterrorists and as a result, they paid almost $500,000 in bitcoin to get their data back. These few examples clearly demonstrate the need to develop more rigorous tools for protecting critical assets.

With respect to our proposed taxonomy, such ransomware attacks against SCADA systems can be classified as:

- CPS components: cyber 

- Hacker motivation: economic 

- Security: Threats (external, man-made), vulnerabilities (technical), and controls (data backup and recovery).

Going back to the two research questions posed in the beginning of the paper, through exploring the three scenarios we demonstrated that the proposed taxonomy can successfully classify knowledge on cyberattacks against critical infrastructure, because the dimensions it is comprised of are broad enough to capture various threats, targets, and security controls. And with regards to the second research question, we established that RAT can, and is in fact, a valuable tool to build our theoretical foundation. It gives us a solid research background that we can use to solve real-world problems such as incident detection and response as prescribed by DSR.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-1/">
INTRODUCTION</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-2/">
PROBLEM IDENTIFICATION</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-3/">
BACKGROUND LITERATURE</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-4/">
ROUTINE ACTIVITY THEORY</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-5/">
RESEARCH QUESTIONS</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-6/">
TAXONOMY DEVELOPMENT</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-7/">
METHODOLOGY</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-8/">
RESULTS</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-9/">
LIMITATIONS AND FUTURE RESEARCH</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-10/">
CONCLUSION</a></li><li> <a href="/docs/A/A-Taxonomy-of-Cyberattacks-against-Critical-Infrastructur-11/">
REFERENCES</a></li></ul>
***

</div>
