---
layout: default
title: COUNTERMEASURES 
parent: § A Risk based Approach to Cybersecurity - A Case Study of Financial Messaging Networks Data Breaches 
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

## COUNTERMEASURES
As seen in the case studies above, APTs are quite difficult to detect and tend to be complex in nature. Although the generic stages are the same, the exact vulnerability(ies) used in performing APTs could change from one to another. Therefore, a critical task when developing approaches to deal with threats would be to build systems that can respond to the constantly changing threat environments with agility and resilience. The author first reviewed the latest actions taken by SWIFT to strengthen defenses against cyberattacks. Then, a comprehensive framework was proposed to complement the SWIFT customer security control framework with the NIST risk management framework (RMF).

### SWIFT Customer Security Program
SWIFT recently published an update to its Customer Security Program (CSP) and Customer Security Controls Framework (CSCF), a key aspect of the CSP (SWIFT, 2019a). The member institutions need to attest compliance with the CSCF v2019 by the end of 2019. SWIFT began enforcing these updated cybersecurity controls in more than 11,000 member institutions, partly responding to a series of cyberattacks between 2013 and 2018 and ultimately aiming to reinforce the security of the global banking system. According to one of the latest updates from SWIFT (2020a), more than 91 percent of customers (which represents over 99 percent of SWIFT’s traffic) attested to their compliance with controls mandated by SWIFT’s CSCF v2019.

The major goal of SWIFT CSP is to ensure the confidentiality, integrity, and availability of the systems that connect to the SWIFT network. It addresses a range of aspects including the protection of members’ local environments, preventing and detecting fraud in counterparty relationships, and working with members of the financial services industry to prevent future cyberattacks (Rut, 2019). Within the program, the CSCF is expanding to the 19 mandatory and 11 advisory security controls as of 2019, which are articulated around three overarching objectives: “Secure your Environment”, “Know and Limit Access”, and “Detect and Respond” (SWIFT, 2020b). There are three ways to comply with the SWIFT requirements: self-assessment, internal audit, or external audit (Koetsier & Diemont, 2018). Each type of compliance requires different degrees of independence, depth, and reliability of the attestation data.

Among the CSCF security controls, two important mandatory security measures are worth highlighting. First, it is mandatory for all member institutions to implement and enforce effective password policy and multi-factor authentication (MFA, mandatory controls 4.1 and 4.2) to prevent credential compromise. The use of hardware tokens is allowed, provided the member institutions properly manage and track the tokens (mandatory controls 5.2) during issuance, use, and storage to prevent unauthorized access to the SWIFT system. Furthermore, compliance can be achieved through the use of a management interface that facilitates assigning and tracking of each individual token (SWIFT, 2018). Secondly, a “secure zone” should be created by complying with all 30 controls collectively. “Secure zone” is where all local SWIFT infrastructure will reside, which isolates all local SWIFT systems from the wider enterprise network and restricts access and privileges on all systems within this secure zone.

### Applying The NIST RMF To Enhance Security Controls
Despite the enforcement of CSCF security controls in all SWIFT local systems, two major aspects of the “bigger picture” are omitted. First, the concept of “secure zone” only focuses on local SWIFT systems. However, a number of upstream systems and counterparties within financial institutions are out of scope of the CSCF (F-Secure, 2018). Another concern lies in a commonly observed trend that organizations treat CSCF as a stand-alone security framework serving only one purpose: to meet SWIFT security requirement (Koetsier & Diemont, 2018).

There is a pressing need for a SWIFT member institution to adopt a risk management mindset and conduct a comprehensive risk assessment of its networks (including both internal networks and external networks with counterparties) instead of focusing on “secure zone” only. In order to enable these SWIFT member institutions to better understand the nature of the threat landscape and implement security controls from a holistic perspective, the author recommend a risk management framework as another countermeasure. An organization within the banking ecosystem can approach the assessment of cybersecurity risk by integrating the National Institute of Standards and Technology (NIST) risk management framework (RMF) to complement its existing security control. The framework leads to a comprehensive and multi-level risk management process that can be implemented throughout an enterprise (NIST, 2018, 2019). The steps included in the RMF is demonstrated in Figure 2. Each of the six steps in the RMF is illustrated with more details and examples next.

Figure 2

*Risk management framework (RMF)*

![Risk management framework (RMF)](https://statics.bsafes.com/images/papers/A-Risk-based-Approach-to-Cybersecurity-ACase-Study-of-Financial-Messaging-Networks-Data-Breaches-fig-2.png)

1. *Categorize information systems.* The framework enables SWIFT as well as its customers to categorize their information systems based on the severity of a likely worst-case or adverse impact on their businesses. For instance, the impact level could be determined as low if the resulting loss has limited impact or moderate if the loss has a serious impact and high when losses have catastrophic impacts on the business’ integrity. This also includes examining the enterprise network perimeter in order to identify which systems communicate with the SWIFT infrastructure and the administration procedures surrounding these systems. 

2. *Select security controls.* Security controls would be selected from the outcome of the initial categorization of information systems and risk assessment using appropriate baselines determined by the banks’ risks tolerance levels. Furthermore, as covered in the previous section, the SWIFT CSCF establishes a security baseline of mandatory and advisory controls for the entire user community (SWIFT, 2019a, 2020b). For instance, by selecting an MFA access control approach, the Bank of Bangladesh heist in 2016 could have been simply prevented because it would be more difficult for the hackers to obtain both login credentials and hardware tokens possessed by bank employees at the same time.

3. *Implement security controls.* After security controls are selected, they can then be integrated into an organization’s security architecture and system using quality security engineering practices as well as employee trainings. Financial institutions need to develop a thorough plan regarding which permissions and actions privileged users should have access to and how an attacker could subvert or abuse these privileges. If these actions are necessary and cannot be prevented, an organization should follow the mandatory controls delineated in the CSCF closely. One challenge to follow the CSCF controls lies in the framework that defines the guidelines at a macro-level without details. Therefore, a strong focus should be placed on establishing controls on mail gateway, endpoint devices, and account control (F-Secure, 2018).

4. *Assess security controls.* The next step in the suggested framework guide requires SWIFT and the banks to test the effectiveness of the selected controls to find out if they were correctly implemented and working as intended. The controls surrounding each of these steps should then be assessed to confidently determine whether or not they would prevent such actions. This process should include security assessments of all controls along the path as well as establishing an understanding of the legitimate use cases for all components. For instance, in the NIC Asia Bank data breach, the pirated software was cited as one of the major contributing factors because it prevented the bank from upgrading software and building a robust IT infrastructure. If the bank followed the process of assessing security controls, installing and running pirated software on bank computers would not be allowed in the first place.

5. *Authorize information systems.* The framework provides the guidelines to support “consistent, well-informed, and ongoing security authorization decisions (through continuous monitoring), transparency of security and risk-related information, and reciprocity of security assessment results” (NIST, 2019). It emphasizes the importance of the official management decision given by a senior organizational official to authorize operation of a system and to explicitly accept the risk to organizational operations and assets based on the implementation of an agreed-upon set of security controls. 

6. *Monitor security controls.* The controls implemented for the systems should be monitored continuously for signs of changes or attacks and regularly reassessed for effectiveness through an integrated enterprise-wide monitoring program. It is crucial that financial institutions continuously log all key servers within the environment and maintain visibility of servers and endpoint devices. For instance, NIC Asia Bank heist was caused by unintentional insider threats in which several employees accessed a designated computer for SWIFT transfers and used it for other purposes. Implementing a continuously monitoring and detection system would have flagged such abnormal behavior and halted further activities on the designated computer. A network-based intrusion prevention system (IPS) could be installed for detection of any known attacks against SWIFT systems and prediction of some unknown attack patterns and trends.

***

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
