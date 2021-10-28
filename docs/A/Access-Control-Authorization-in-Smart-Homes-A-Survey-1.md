---
layout: default
title: 1 Introduction
parent: § Access Control Authorization in Smart Homes - A Survey   
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
Ever since Kevin Ashton conceived the Internet of Things (IoT)[1], and with the speedy development of networking technologies and the IoT, human lives have been constantly changing from a physical dimension to a virtual dimension in which people can talk, chat, work, and interact with the connected objects.

The smart home as an IoT application was introduced to facilitate human life and change the way we live, play, and do business. It is meant to make life more flexible, comfortable, and exciting. However, apart

***
- Ziarmal Nazar Mohammad, Fadi Farha, and Fang Zhou are with the School of Computer and Communication Engineering, University of Science and Technology Beijing, Beijing 100083, China. E-mail: nmziarmal43@gmail.com; fadi farha@xs.ustb.edu.cn; zhoufang@ies.ustb.edu.cn.   
{: .fs-2}
- Shunkun Yang is with the School of Reliability and Systems Engineering, Beihang University, Beijing 100191, China. Email: ysk@buaa.edu.cn.   
{: .fs-2}
- Adnan O.M Abuassba is with the School of Computer Studies, Arab Open University, Ramallah 4375, Palestine. E-mail: adnanasba@yahoo.com. 
{: .fs-2}
* To whom correspondence should be addressed. Manuscript received: 2021-01-02; accepted: 2021-01-20
{: .fs-2}
***

from the benefits of smart homes, several security and privacy issues need to be considered while building and designing a smart home. While introducing new technologies aiming to make our homes smarter and more automated, cyberspace is also growing fast[2–5] , surrounding our lives with billions of smart devices that can invoke privacy and security issues[6–10] .

Smart home technology, which is one of the most important and fastest-growing fields of the IoT, is being massively deployed by many manufacturers and companies. The smart home includes home automation, home monitoring, and home security for the local users.

Smart homes face many security and privacy threats. For instance, hacking the security cameras of the smart home can violate the user’s privacy and access sensitive data, such as health data, pictures, and movies. These violations and unauthorized access to the smart home can lead to many critical and dangerous issues[11] .

Smart home devices can be accessible by multiple users through a user-friendly interface, such as a web browser or mobile application[12]. Third-party vendor applications basically control smart home devices through mobile-based and web browser-based interfaces and interact with a back-end cloud system. This system can expose the services via web APIs that accept queries to control the devices and data from multiple vendors.

Companies and manufacturers need to enforce access control to solve smart home authorization problems and ensure that unauthorized users do not access sensitive resources. There are many commercial authorization frameworks, some of which enforce coarsegrained access controls, such as Nest Thermostat (store.google.com/us/category/connected home?), which grants full access to the smart device or no access at all, and Apple Home Kit (www.apple.com/ios/home/), which provides a local and remote full control or view. Other authorization frameworks provide more robust access control policies that support environmental conditions, such as Samsung Smart Things (www.samsung.com/us/smartthings/), which tracks the user’s smartphone GPS coordinates and determines whether the user is at home. However, because this framework is a real-time user tracking, it violates user privacy. Such shortcomings and challenges in implementing access control policies in smart homes can easily lead the devices and apps to access unauthorized users, which may cause privacy and data loss problems[13–15]. An example of these shortcomings is having full access or permission issues in baby monitors that are hacked and remotely controlled. Therefore, a fine-grained access control system should be enforced to prevent unauthorized access to smart devices and data and support multiple user management[16] .

Fine-grained access control systems apply policies according to several aspects, such as smart device capabilities, the relationship between users, and context information, including location and time-based conditions[17]. Because of IoT integration with web services and APIs, suitable access control is needed, especially to open smart home platforms. The access control model needs to be flexible and not too strict. The strictness of the authorization framework will affect the dynamicity of the smart home system.

In recent years, several authorization frameworks have been proposed for the smart home with different assumptions and technologies. These variations and assumptions make the evaluation and effectiveness of the authorization framework complicated. Although many surveys discussed privacy and security challenges in the IoT[18–21], only a few research works addressed access control[22–26] .

In this survey, we conduct a review and analysis of the most recently proposed access control solutions for smart homes. As shown in Table 1, existing surveys have the following limitations:

(1) They do not cover all aspects of access control. Most of these surveys only focus on the specification of policies, while the other two aspects, including management and evaluations of the policies, are partly or completely neglected. 

(2) The existing surveys do not summarize the requirements of access control for smart homes, and no evaluation and analysis of existing authorizations frameworks are available.

This survey presents an overview and analysis of existing access control schemes in smart homes. We mainly note the unsolved challenges in existing access control frameworks for smart homes and turn research into more flexible and suitable authorization solutions. The main contributions of our survey are as follows:

(1) An overview of the current authorization solutions for the smart home and their evaluation based on specified requirements is presented.

(2) Guidelines and open challenges that should be considered while designing smart home authorization frameworks are provided.

The remainder of this paper is organized as follows: Section 2 explores the smart home architecture. Section 3 reviews access control and its different models. Section 4 concerns access control in smart homes. In Section 5, we analyze the existing access control solutions for the smart home, and Section 6 consummates our work and appoints a direction for future research.

### Table 1 Comparison with existing surveys of access control.
![Table 1 Comparison with existing surveys of access control](https://statics.bsafes.com/images/papers/Access-Control-Authorization-in-Smart-Homes-A-Survey-Table-1.png)

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
