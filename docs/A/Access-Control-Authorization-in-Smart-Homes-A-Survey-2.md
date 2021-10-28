---
layout: default
title: 2 Smart Home
parent: § Access Control Authorization in Smart Homes - A Survey   
grand_parent: A 
nav_order: 20 
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

## 2 Smart Home
The smart home is an important IoT application in daily life. Smart devices, such as doorbells, thermostats, door locks, smart ovens, smart lights, and smart refrigerators, are installed and configured in smart homes. They can be remotely controlled by home users via user-friendly interfaces, such as web browsers or mobile applications. The interactions inside the smart home can be machineto-machine or human-to-machine. As an example of the machine-to-machine interactions, a smart fridge can automatically interact with a smartphone and send a notification to it when something is running low in the fridge, such as milk and fruit. An example of the humanto-machine interactions is a house owner controlling smart devices, such as light bulbs, or allowing other family members to control the smart devices using their smartphone application or a simple web browser.

The smart home application presents several challenges due to its multi-user and multiple device nature. Sharing smart devices between smart home users causes many conflicts in terms of user demands leading to many complicated scenarios[27]. Before explaining access control and how it works with the smart home, we briefly explain the smart home’s elements and structure.

### 2.1 Smart home elements
The smart home elements, also named nodes, are divided into the following three categories[26]:

(1) Physical nodes: They include any entity or thing that can interact with the environment and provide resources, such as sensors, actuators, smart fridges, microwave ovens, light bulbs, cameras, and doorbells.

(2) Application nodes: They include the resources provided by physical nodes that feed the application nodes to deliver services to users.

(3) Intermediate nodes: They are located between physical nodes and application nodes. They connect two or more different networks and route traffic between them, such as a bridge and gateway.

### 2.2 Smart home architecture
The architecture of the smart home shows the actual functionality and connectivity of the smart home system, including architectural models and architectural styles.

#### 2.2.1 Architectural models
Several architectural models have been proposed for the IoT[28–34]. Typically, the architecture models are divided into layers, and each layer has its own functionality. Because the smart home and other IoT systems are made of resource-constrained smart devices, the access control and authorizations solutions deployed in the architecture’s middleware layer have been reviewed in this survey. For greater clarity, we separate middleware from the network layer. Thus, a four-layer architecture model is adopted.

As shown in Fig. 1, the application layer consists of application nodes that provide end-user services. The middleware layer consists of intermediate nodes to maintain connectivity and interoperability within the smart home system. The network layer provides communication and data transfer between nodes. Finally, the physical layer consists of smart devices.

#### 2.2.2 Architectural styles
In recent years, several architectural styles have been proposed. The architectural style varies based on several factors, such as the domain and communication between application nodes, intermediate nodes, and physical nodes. As shown in Fig. 2, three main types of architectural style are used[23, 35]:

![Fig. 1 Architectural model and smart home elements.](https://statics.bsafes.com/images/papers/Access-Control-Authorization-in-Smart-Homes-A-Survey-Fig-1.png)
Fig. 1 Architectural model and smart home elements.

![Fig. 2 Architecture styles of the smart home.](https://statics.bsafes.com/images/papers/Access-Control-Authorization-in-Smart-Homes-A-Survey-Fig-2.png)
Fig. 2 Architecture styles of the smart home.

(1) Centralized architecture: In this architecture, all the physical nodes are connected through an intermediate node. Moreover, the requests from the application node must pass through an intermediate node. This type of architecture is usually used with resource-constrained smart devices. 

(2) Connected architecture: Physical nodes can process and forward data to intermediate nodes, and application nodes can directly retrieve data from physical nodes. 

(3) Distributed architecture: Intermediate nodes are unnecessary, and every node can process data and communicate with other nodes[26] .

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
