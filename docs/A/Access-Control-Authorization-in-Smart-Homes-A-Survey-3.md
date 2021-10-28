---
layout: default
title: 3 Access Control
parent: § Access Control Authorization in Smart Homes - A Survey  
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

## 3 Access Control
Access control is an effective technique for addressing privacy, security, and access violation issues in smart homes. Its main goal is to ensure that the house resources can only be accessed by authorized users, data, and services. It protects the system by restricting legitimate users’ access according to their privileges and preventing unauthorized users[36, 37] .

###  3.1 Access control models
Several access control models are available and can be implemented in smart homes. They range from a very basic level, such as an access control list, to a slightly more advanced level, such as attribute-based access control.

#### 3.1.1 Access Control List (ACL)
Traditionally, the access control matrix was one of the early techniques used for access control. Its columns and rows are composed of objects and subjects, and each record has a set of subject-related access rights[38]. Later, ACL was developed. It is a set of specific resources accessible only for specified users concerning their privileges[36] .

#### 3.1.2 Discretionary Access Control (DAC)
DAC is specially developed for systems and databases with multi-user platforms. It grants access depending on user identities. In DAC, the entire system is under the control of the owner, who grants access to the other users, which is why it is called discretionary access control. It allows users to substitute their privileges to other users[39]. The main disadvantage of DAC is that nonlegitimate users can gain access to resources.

#### 3.1.3 Mandatory Access Control (MAC)
This model is static. Each object has an assigned label to indicate specific privileges of the object. Moreover, each subject has a label to indicate which object a requester can access[40]. In MAC, all users only have access to resources based on their task-related privileges, and because of its static nature, this model is not flexible and cannot be used for dynamic domains, such as smart homes.

#### 3.1.4 Role-Based Access Control (RBAC)
It is commonly deployed for small and large organizations[41]. As the name of this access control model suggests, the users can have access to the resources based on their roles. RBAC mainly depends on the following elements: subject (users), object (resources), roles (collection of permissions), and operations (actions on the resources). In RBAC, access rights are granted to roles, and roles give users permissions based on their role rather than their identity. Every user can have multiple roles, and each role could be granted to multiple users. This model is also not recommended in the smart home system because of its limitations in context-awareness and dynamicity, so it cannot satisfy the smart home system requirements.

#### 3.1.5 Capability-Based Access Control (CapBAC)
Unlike other models, CapBAC is a distributed approachbased model, where things can make the decision without any reliance on the central device. CapBAC can be implemented on highly capable devices. Hence, this model is not truly suitable for the smart home system because it typically consists of low-power and resourceconstrained devices.

#### 3.1.6 Usage Control (UCON)
Other models, such as Attribute-Based Access Control (ABAC) and RBAC, can only change the attributes after or before the access request. However, the attributes cannot be changed during the execution of the access rights. UCON provides more flexibility than other models while handling authorization by introducing decision factors (obligations and conditions) and mutable attributes. Mutable attributes are the actors, resources, or contextual information whose values can be changed based on an object’s usage. With continuous policy evaluations, UCON can interfere with access to prevent misuse of the resources when the access right becomes invalid, even during ongoing access[42] .

#### 3.1.7 ABAC
ABAC is fine-grained, flexible, and dynamic access control. In this model, access rights depend on the subject, object, environmental conditions, and their related policies[43]. This model gives the best combination of various attributes for building a flexible and dynamic authorization framework. Its flexibility and context-aware nature make it a more suitable authorization model for smart homes and other IoT domains than other traditional role-based models.

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
