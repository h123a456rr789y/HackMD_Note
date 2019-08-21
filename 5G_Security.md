---
title: 5G Security
tags: Intern, 5G Security, Slide
description: 5G Security
---


# 5G Security
Date:2019/8/15
洪立宇

---

## Outlines
- 5G Security Function
- 5G Security Threats
- 5G Security Solution and Mitigation

---

## 5G Security Functions

---

### Service Based Architecture (SBA)

![](https://i.imgur.com/4LoSlUa.png)

---

### Security Functions in 5G Architecture
![](https://i.imgur.com/Ic7CEKf.png)

---

### 5G Security Functions
- SEPP: Receives all service layer messages and  forwards them to the appropriate network function after verifying security 
- SEAF: Allows for the re-authentication of the device when roaming, or even without full authentication method (ex: AKA)
- AUSF: Verifies UE authentication & stores key for future re-use
![](https://i.imgur.com/ovBNkMa.png)

----

### 5G AKA Authentication
![](https://i.imgur.com/tIsDRnQ.png)


----

### 4G AKA Authentication
![](https://i.imgur.com/JJgC2W1.png)

---

## 5G Security Threats
![](https://i.imgur.com/JCQJoxA.png)

---

### 5G New Design 
![](https://i.imgur.com/dTmDa4h.png)

---

### 5G Security Threats
![](https://i.imgur.com/YaLmRvJ.png)
            - OAM: Orbital Angular Momentum
            - Source: Taiwan National Communications Commission, NCC

---

### Key Security Challenges in 5G
- Flash network traffic & DoS
- Security of radio interfaces: Radio interface **encryption keys** are sent over **insecure channels**
- User plane integrity: No cryptographic **integrity protection** for the user **data plane**
- Roaming security: User-security parameters are not updated with roaming from one operator network to another

---

## Challenges and Solution
- SDN
- NFV
- Mobile Cloud & MEC
- Privacy

---

### SDN Challenges and Solution 

- Programmable SDN controller updates or modifies flow rules, **control info can easily identified -> DoS attack**
- Centralization of network control & SDN architecture (i.e., OpenFlow)->prone to saturation attacks(due to limited flow buffer)
- Sol:
    - Use the transparency of SDN to gather flows and packets from CP -> **quick response IDS**
    - Create **visibility** of the network to analyze the traffic and build high reactive and proactive **security monitoring**

---

### NFV Challenges
- NFV in mobile networks is the dynamic nature of VNFs that leads to **configuration errors**
- **VNFs are vulnerable** to typical cyber-attacks such as spoofing, sniffing, and DoS
- **Common accessibility** of the infrastructure. The attacker can interfere with operations of the infrastructure by inserting malware or manipulating network traffic

---

### NFV Solution
- Not only the security in VNF  in  **multi-tenant environment** but also physical entities of telecom network(ex: hypervisor)
- **Firewalls** and **IDSs** can be used to prevent outside attacks.
- **Identity and access management mechanisms** (e.g., role-based access control) can be used to mitigate the impact of insider attacks
- **Multiple controllers** may increase resilience to security attacks. However, misconfiguration forwarding elements or inter-federated conflicts will hinder security policy enforcement.

---

### MEC Challenges

- **Multi-tenant** cloud networks where tenants run their own control logic, interactions can cause **conflicts in network configurations**
- **Cloud-enabled IoT** environment and the **open APIs** for MEC applications and end users are vulnerable
- **Man‐in‐the‐middle (MitM)** and **malicious mode** problems have been identified

---

### MEC Solution
- Visibility of the network topology (NPB,APM)
- Secure Operating System for Edge Platforms
- VPN and General Encryption of All Data
- User Access Management (Authentication)

---

### Privacy Challenges
- Semantic information attacks (ex: App)
- Timing attacks
- IMSI catching attack (fake BS)
- 5G have **different actors** such as virtual mobile network operators (VMNOs), communication service providers (CSPs)->**synchronization of privacy polices**

---

### Subscription Identification Security
- 4G: Trigger of IMSI
    - When Mobile connect to the Network: (New connection or roaming)
    - When Mobile connect to impersonate BS  	 
- 5G: Use of SUPI (Permanent Id)& SUCI ( Concealed Id)
    - SIDF: Decrypt of SUCI and get SUPI
- But still attacker may force UEs to communicate in non-5G mode (Bidding Down Attack)

----

### Subscription Identification Security
![](https://i.imgur.com/S3eCZjg.png)

----

### Subscription Identification Security

![](https://i.imgur.com/TZdHp2E.png)

---

### Privacy Solution
- Requirement of better mechanisms for **accountability, data minimization, transparency, and access control**
- **Hybrid cloud-based** approach, which mobile operators are able to store and process highly **sensitive data locally** and **less sensitive data in public** clouds
- **Encryption-based** system, a message can be encrypted before sending to a location-based services (LBS) provider
- **Location-cloaking-based** algorithms and **Obfuscation** for location privacy

---

### Security Challenges in 5G Technologies
![](https://i.imgur.com/QIK0ivN.png)

---

### Security Solutions for Targeted Threats
![](https://i.imgur.com/waMQSZz.png)

--- 

### 5G Visibility

- Reason:  Huge Network traffic
- Network Packet Broker(NPB) : **Efficiently manage traffic** to the monitoring tools. 
- NBP Cut the Band in to small part(segmentation) which makes each part easily managed
- 5G -> **Small Cells** -> Small cell backhaul requires many more **high-speed links** connecting to the wireline network -> All  Links should be protected and monitored	

---

### NPB

- Used to use  DPI(Tap or Port Mirror) to inspect the packet, which break and rebuild packet from layer 2 to layer 7 when pass through each device.
- NPB benefit:
    - Efficient Traffic Filtering
    - Secure Removal of Repetitive Data
    - Network Packet Brokers Optimize Packets
    - Capacity for Fault Tolerance
    - Network Packet Brokers for Load Balancing

----

### NPB
![](https://i.imgur.com/DTCmavR.png)

---

# The End 