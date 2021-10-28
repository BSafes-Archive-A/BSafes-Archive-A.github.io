---
layout: default
title:  6 Authorization Frameworks for Smart Homes  
parent: § Access Control Authorization in Smart Homes - A Survey 
grand_parent: A 
nav_order: 60 
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

## 6 Authorization Frameworks for Smart Homes
Several authorization frameworks have been developed in the last few years to fill the gaps in smart home resource authorization. This section reviews and analyzes recent existing solutions based on the smart home requirements and discusses which authorization framework is suitable for smart homes.

### 6.1 Existing authorization frameworks
Several authorization frameworks have been proposed for smart homes and can be categorized into two main types: policy evaluation strategy and architecture. Most of the policy evaluation strategy authorization frameworks[12, 42, 48–57] are inspired by the eXtensible Access Control Markup Language (XACML) standard[58]. Moreover, several policy evaluation strategies-based and architecture-based authorization frameworks[56, 59–61] are built on the top of OAuth[62] to enable token generation.

With the several architectural types of access control, several technologies and deployments are presented, such as Policy Decision Point (PDP), policy enforcement point, policy Administration Point (PAP), and policy information point, which can be deployed in the cloud or edge devices[49], in addition to authorization solutions built based on blockchain[42, 52, 57]. Some works, such as Refs. [12, 54–56, 60, 61, 63], are prototype implementations, and many others, such as Refs. [42, 52–55, 57, 59, 64], are conceptual level proposed solutions.

Another recent authorization framework specific to the smart home environment was proposed by Sikder et al.[12] and solves several problems, such as supporting multi-user management and context-awareness, but for the architecture of access control, it was based on RBAC, while the smart home needs a dynamic and flexible access control model, such as ABAC or UCON.

In the above mentioned authorization frameworks, if the user does not meet specific requirements, the policy server will reject its request. For instance, if a legitimate user temporarily left the country and wants to have access to smart home resources in an emergency, then smart home access control should be flexible by providing more options to users, such as generating a verification code and sending it to the user’s email or phone number or asking secret questions to provide temporary access. Tables 3 and 4 briefly explain the existing access control systems used for smart homes.

To implement the access control-based authorization frameworks on the real smart home domain, most of the existing authorization frameworks[42, 48, 52, 53, 57, 59, 64, 69] only mention that the access control architecture is built based on authorization framework, and the use cases only show the authorization flow. Few existing authorization frameworks have been conducted to implement and evaluate a real smart home[12, 56, 70]; hence, other research works only provide a prototypebased implementation[54, 55, 61, 66].

### 6.2 Discussing smart home authorization frameworks
According to the literature, we conclude that the smart

### Table 3 Access control requirements for smart home.
![Table 3 Access control requirements for smart home.](https://statics.bsafes.com/images/papers/Access-Control-Authorization-in-Smart-Homes-A-Survey-Table-3.png)

### Table 4 Existing access control characteristics.
![Table 4 Existing access control characteristics.](https://statics.bsafes.com/images/papers/Access-Control-Authorization-in-Smart-Homes-A-Survey-Table-4.png)

home has several requirements, especially in policy management, totally different from other IoT applications, and these requirements need to be considered while designing and implementing access control for smart homes. As shown in Table 2, the smart home highly relies on Requirement1, Requirement2, Requirement3, and Requirement6, and partially relies on Requirement4 and Requirement5.

Concerning the policy specifications, an authorization framework that can support fine-grained (Requirement1) and context-aware (Requirement2) access control can be satisfied with the design and implementation of ABAC and UCON.

With respect to policy management and policy evaluation, there are other access control requirements. The smart home authorization framework should always be operational (Requirement6) and satisfied by the authorization framework’s reliability and availability. Furthermore, homeowners may want to manage and specify policies themselves in a smart home with several devices. However, they might not have sufficient security knowledge, so the smart home authorization frameworks should be user-friendly, easy to specify, and access control policy managers. As a result, consideration of usability (Requirement3) is very important while designing and implementing an access control system for smart homes.

Two more essential requirements to be considered are the automation of access control (Requirement4) and the insensitivity of the resource-constrained device communication and computing capabilities to the smart home access control system (Requirement5).

Finally, the ideal access control framework for the smart home must be a centralized and policy-based framework in which the authorization decision should be automatic and dynamic based on the specified policies. It should also be location-aware and based on context. The policy authorization framework should be externalized, so any changes and updates in the policies will not affect the smart home application design and coding parts. This stipulation means that the PDP should be implemented in edge devices or the local cloud.

Moreover, the PAP should allow the homeowner to specify and modify the policies. Because of the small number of smart home devices, latency can be tolerated, and a run-time evaluation can be adapted.

Some authorization frameworks, such as Refs. [12, 48, 49, 55, 65, 68], are specially proposed for smart homes, but these frameworks do not cover all the requirements of smart homes. Works such as Refs. [48, 49] are coarsegrained authorization frameworks that are not suitable for all access control cases in smart homes, such as when the users change their location while accessing their smart home. Other works[12, 55, 68] propose a finegrained and context-aware access control system for smart homes, but they do not consider the multi-users’ role, robots’ role, and usability of the access controlbased authorization framework. Furthermore, none of the access control solutions for smart homes mentioned the robots’ role, which nowadays can be considered users in smart homes. For instance, service robots may need to access the smart lock or smart coffee machine to brew coffee for home residents or perform other tasks.

### 6.3 Open challenges and future works
Because of the openness, heterogeneity, and nature of smart homes, many challenges need to be considered while designing and implementing an access controlbased authorization framework for smart homes. Some of the unaddressed issues and future challenges that face the existing access control techniques in smart homes are as follows:

**Multi-user management:** Most of the existing authorization frameworks assumed that the smart home is a single-user domain, and the house owner is the only user responsible for having control over smart devices. As mentioned previously, there are many scenarios in which multiple users need to have access to smart home devices; therefore, while designing and implementing access control for smart homes, multi-user management needs to be considered.

**Resource-constrained:** Most smart home devices have a low-power and resource-constrained nature, so they cannot process high-computational encryption algorithms[71]. Such devices cannot decide which user should have privileged access. There should be a centralized authorization framework that helps these resource-constrained devices to make authorization decisions to address this challenge.

**Dynamicity:** The multi-user nature of smart homes brings a new challenge to the smart home system in which users may want to access the resources anytime and anywhere. Therefore, while designing and implementing access control for smart homes, the authorization decision should be made dynamically by the system, i.e., there is no need for a house owner or admin user to authorize the requests coming from other users manually.

**Flexibility:** The access control system should be tolerant with some changeable attributes and not too strict with the rules. For instance, a user may be out of the country and want to access smart home resources. In this case, if the access control is location-aware, the user will fail to satisfy the condition of the location attribute needed for the authorization decision. Consequently, the authorization framework will reject the user request. For example, the authorization framework should skip the location attributes if the user answers a secret question or enters the verification code correctly.

**Machine-to-machine interaction:** Robots in smart homes represent a new challenge to the existing access control solutions for the smart home. As we all know, robots are widely used in smart homes. By 2024, almost 79 million smart homes worldwide will use robots[72] . Almost all the existing access control solutions used in smart homes can only accept requests from a human. They cannot make authorization decisions for a machine, such as a robot, which can be considered a user in smart homes. For instance, the service robot helping people[73] needs to clean the house. To do that, it should have access to the smart lock to enter the room and perform its task. While designing access control for smart homes, this challenge needs to be considered. Access control solutions should identify the robot’s identity and have an additional feature that could decide which robot has access to a specific device or resource.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-1/">
1 Introduction</a></li><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-2/">
2 Smart Home</a></li><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-3/">
3 Access Control</a></li><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-4/">
4 Access Control in Smart Home</a></li><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-5/">
5 Smart Home: Use Cases and Challenges</a></li><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-6/">
6 Authorization Frameworks for Smart Homes</a></li><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-7/">
7 Conclusion</a></li><li> <a href="/docs/A/Access-Control-Authorization-in-Smart-Homes-A-Survey-8/">
References</a></li></ul>
***

</div>
