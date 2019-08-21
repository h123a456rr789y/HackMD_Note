---
title: The Evolution of Security in 5G
tags: Intern, 5G Security, Slide
description: The Evolution of Security in 5G
---




# The Evolution of Security in 5G
Date:2019/7/15
洪立宇

---

## Outlines
- Introduction
- 5G Security Architecture
- 5G Security Threats
- 5G Security Trend

---

## Introduction

---

### 3GPP Specification and Timeline
- 3GPP is a mobile communications specifications group
- SA3 is the working group that develops mobile communication specifications of security
![](https://i.imgur.com/5KES96b.png)

---

### Mobile Network Security 
![](https://i.imgur.com/9wP2igS.png)

---

### Mobile Network Security 
- New attack vectors of edge computing, convergence of network, virtualization of network, Massive UEs on Network(MIoT)
- Visibility -> Automation, Orchestration, (NFV) 
- Innovation -^ 
- Mitigation controls
- Segmentation 

---

### 5G Use Case Categories
![](https://i.imgur.com/OG8uVGv.png)


---

### 3GPP 5G Specification Phases 
![](https://i.imgur.com/GQFBdIb.png)

---

## 5G Security Architecture

---

### 5G Security Architecture
- Network access security (I)
- Network domain security (II)
- User domain security (III)
- Application domain security (IV)
- SBA domain security (V),set of security features about the SBA security.
- Visibility and configurability of security (VI)

----

### 5G Security Architecture
![](https://i.imgur.com/7uR3sx2.png)


---

### Service Based Architecture (SBA)
![](https://i.imgur.com/yusoCOM.png)

---

### Security Functions in 5G Architecture
![](https://i.imgur.com/alWrhI4.png)

---

## 5G Security Threat
![](https://i.imgur.com/pAKYjlV.png)

---

### IoT & MIoT Threat
- Problems:
    - Cannot provide a **complete accounting** of all their network-connected devices 
    - For identified IoT entities, **ownership** frequently remains murky 
    - **Increasing volume** of connected devices
    - **Zero-day** vulnerabilities may be exploit for DDoS attack
- DDoS can solved by 5G RAN overload function and CU-CP 

---

### CU/DU In RAN

- Pros:
    - Allocate the resource efficiently 
    - Beneficial to Network Slicing and NFV
    - Good for Network Orchestration by CU
- Cons:
    - Harder to deploy the CU and DU than 4G BS
    - Higher cost for operating 

---

### CU/DU Security
- Support a number of deployment options (e.g. co-locataed CU-DU deployment is also possible)
- DUs, deployed at the edge of the network, don't have access to any user data when **confidentiality protection** is enabled
- Even with split, **air interface** security point in 5G remains the same as in 4G, namely the RAN.

----

### CU/DU Security
![](https://i.imgur.com/0cY1Jr0.png)

---

### Subscriber Privacy Threat

- In 4G IMSI catcher can **impersonate BS** and capture IMIS meanwhile even force UEs to use no encryption, or easily breakable encryption to eavesdropping 

- 5G use SUPI and SUCI to mitigate the problem above, but the attacker may **force** UEs to communicate in **non-5G mode** (ex. 3G) which nullify the mitigation.

----

### Subscriber Privacy Threat
![](https://i.imgur.com/495ImOS.png)

---

### 5G Threat Surface
![](https://i.imgur.com/wRh7vUg.png)
- Rogue Base Station (RBS) threat :RBS masquerades as a legitimate base station between the UE and the mobile network  

---

### Edge Computing Vulnerability
![](https://i.imgur.com/2BoOE2y.png)

---

### Virtualization Vulnerability
![](https://i.imgur.com/zg3u5BX.png)

---

### 5GC Threat Detection
![](https://i.imgur.com/nf0GROf.png)

---

## 5G Security Trend

---

### Safeguarding 5G Networks with Automation & AI

- Network is distributed at the edge and virtualized in 5G
- Network’s endpoints can be used as detection spots to send messages back to a centralized control plane (CCP) -> Big Data
- Build extra layer of protection at large data centers 
- A Game of Probability (Good Data & Bad Data )

----

### Safeguarding 5G Networks with Automation & AI

![](https://i.imgur.com/TmhrUzT.png)

---

# The End 

