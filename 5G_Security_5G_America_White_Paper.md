---
title: 5G Security (5G America White Paper)
tags: Intern, 5G Security
description: 5g white paper
---


# 5G Security (5G America White Paper)
## Introduction
- **provide new cybersecurity safeguards to protect both Networks and Customers**

- **new cybersecurity consideration and responses**
    -  New attack vectors of cloud, edge computing and convergence of mobile and IT Network.
    -  Visibility: To get a picture of how application behave or network topology.
    -   Innovation: The way operator apply the extensive informaiton from application to mitigate threats
    -  The moblie industry provide an additional layer of security of constant learning emerging threat and reponse options.

### Overview of 5G use cases 
 ![](https://i.imgur.com/2k8v7gU.png)

### Secutrity functions for 5G DDOS
- Threat to MIoT which use Radio Access Network(RAN) may increase the risk of  RAN overload by DDoS.
    - strategy : commission a project that will examine a standard-based solution to automatically detect and mitigate the risk
    - solution : develop malicious signaling strom detection and migration function

## overview of 5G Architecture in 3GPP
### 3GPP 5G Security Standards
- Increased Home Control 
    - Home control: authentication of the device location when device is roaming.
    - Increase home control address the vulnerability of spoofed and send false signaling message tp the home network and request the Internaltional Mobile Subscriber Identity (IMSI) and location of the device. ->could use for intercept voice call or text messages.
    
- Unified Authentication framework
    -  authentication will be access agnostic
    -  Support Extensible Authentication Protocol(EAP) which allows for new plug-in authentication methods to be added.
    
- Security Anchor Function(SEAF)
    - SEAF allows for the re-authentication of the device when it moves in different access networks or even serving networks without having to run the full authentication method. -> reducing the signaling load during various moblility service.
    - SEAF could be seperate or co-located with Access and Mobility Management Function (AMF)
    
-  Subscriber  Identifier Privacy 
    -  Subscriber Permanent Identifier(SUPI) is globally unique and allocate for each subscriber.
    -  SUPI is never disclosed when the device is establishing a connection.(diffent form 3G and 4G)
    -  Subcription Concealed Identifier(SUCI) is disclose until the device is authenticated. -> prevent IMSI catcher.
    
-  3GPP 5G Security Architecture
![](https://i.imgur.com/EwXUTOM.png)
    - Network access security (I), the set of secuturity features that enables a UE to authenticate and access services
    - Network domain security (II), the set of security features that enable networknet securely exchange signalling  
    - User domain security (III), the set of security features that secures the user access to mobile equipment
    - Application domain security (IV), the set of security features that enables applications in the user domain and in the provider domain to exchange messages securely
    - **SBA domain security (V),set of security features about the SBA security**.
    - Visibility and configurability of security (VI), which is the set of features that enables the user to be informed whether a security feature is in operation
    **Security Edge Protection Proxy (SEPP)**
    ![](https://i.imgur.com/WEM0l1N.png)
    To protect messages that are sent over the N32 interface,5G architecture introduces (SEPP) as the entity sitting at the perimeter of the Public Land Mobile Network (PLMN) network that:
    - Receives all service layer messages from the Network Function and protects them before sending them out of the network on the N32 interface
    - Receives all messages on the N32 interface and forwards them to the appropriate network function after verifying security, where present
- Role of the SEPP in the security architechture
    - The application layer traffic comprises all the IEs in the HTTP message payload, sensitive information in HTTP message header and Request URI. Not all IEs get the same security treatment in SEPP.(e.g. e2e encryption, e2e integrity protection and e2e integrity protection but modifiable by intermediate IPX provider while in-transit)
    - Sensitive information such as authentication vectors are fully e2e confidentiality protected between two SEPPs.(no node in IPX can view information while in-transit)
    - IEs that are subject to modification by intermediary IPX nodes are integrity protected and can only be modified in a verifiable way by authorized IPX nodes
    - Receiving SEPP can detect modification by unauthorized IPX nodes
- Requirements for E2E Core Network interconnection security
    - A solution for e2e core network interconnection security requirements:
        - Shall support aplication layer mechanisms for addition, deletion and modification of message elements by intermediate nodes except for specific message elements described in the present document
        - shall provide confidentiality and/or integrity e2e between the source and destination networks for specific message elements identified in the present document
        - The destination network shall be able to determine the authenticity of the source network that sent the specific message elements protected according to the preceding bullet
- Authentication framework
- GRANULARITY OF ANCHOR KEY BINDING TO SERVING NETWORK
    - The primary authentication and key agreement procedures shall bind the anchor key KSEAF to the serving network.
    - Binding prevents one serving network from claiming to be a different serving network, which provides implicit serving network authentication to the UE
- MITIGATION OF BIDDING DOWN ATTACKS
- SERVICE REQUIREMENTS
    - A UE shall support
        -  a man-machine interface setting for the user to disable use of one or more of the ME’s radio technologies for RAN access, regardless of PLMNs
        -  a man-machine interface setting enabling the user to re-enable use of one or more of the ME’s radio technologies for RAN access, regardless of PLMNs.
        - secure mechanism for the home operator to re-allow selection of one or more of the ME’s radio technologies for RAN access, regardless of PLMNs

- 5G IDENTIFIERS
    - Each subscriber in the 5G system shall be allocated one 5G  (SUPI) for use within the 3GPP system. 
    - The (SUCI) is a privacy-preserving identifier containing the concealed SUPI.
- SUPI
    - is globaly unique and shall be allocated to each subscriber in the 5G system and provisioned in the UDM/UDR
    - In order to enable roaming scenarios, the SUPI shall contains the address of the home network
- SUCI
    - The UE shall generate a SUCI using a protection scheme with the raw public key that was securely provisioned in control of the home network

- SUBSCRIPTION IDENTIFICATION SECURITY
    - The subscriber identification mechanism should be used when the serving network cannot retrieve the SUPI based on the 5G-GUTI
    ![](https://i.imgur.com/kj8UOuD.png)
- PERMANENT EQUIPMENT IDENTIFIER(PEI)
    - shall be securely stored in the UE to ensure the integrity of the PEI
    - The UE shall only send the PEI in the NAS protocol after NAS security context is established
    
- SUBSCRIPTION IDENTIFIER DE-CONCEALING FUNCTION
    - The Subscription Identifier De-Concealing Function (SIDF) is responsible for de-concealing the SUPI from the SUCI

- 5G GLOBALLY UNIQUE TEMPORARY IDENTIFIER
    - The AMF shall allocate a 5G Globally Unique Temporary Identifier (5G-GUTI) to the UE that is common to both 3GPP and non-3GPP access

- SECURE STEERING OF ROAMING
    - Secure Steering of Roaming (SoR) enables the home network operator to steer its roaming customers to its preferred VPLMN networks to enhance roaming customers’ experience and reduce roaming charges

- NETWORK REDUNDANCY IN 5G CORE AND NETWORK SLICING 
    - segmentation through network slicing.
    - In 3GPP, network slicing is being defined in TS 23.501
    - re-designed based on a service-oriented architecture by breaking everything down into detailed functions and sub-functions.
    -  network operators will be the ability to deploy only the functions necessary to support particular customers and particular market segments 
    ![](https://i.imgur.com/89tShVK.png)

    -  benefit is the ability to deploy 5G systems more quickly because fewer functions need to be deployed
    ![](https://i.imgur.com/7rilSWj.png)
    - The Edge Site been created which allows some of the 4G control capabilities to be deployed with 5G user plane.
    ![](https://i.imgur.com/2JqQpog.png)
    - single physical network can be partitioned into multiple virtual networks.
    - nables operators to offer optimal support for different types of services for different types of customer segments
    - service basis provided network ->operators can select NFs using multiple different criteria
    - Network OAM can be made simpler and flexible as service providers can utilize automated tools to provide the network services with the predefined redundancy, capacity and other capabilities
    - Automation can also optimize the unnecessary need for extra hardware


## 5G THREAT SURFACE
- IoT Threat Surface with 5G
    - troubling fact: 
        - The majority of organizations cannot provide a complete accounting of all their network-connected devices
        - Even for identified IoT entities,the ownership from a security point of view frequently remains murky
        - expetation for increasing volume of conneted devices 
    -  worthy principles for securing IoT infrastructure
        -  Securing IoT should not be an afterthought.
        - healthcare, automotive, energy, IoT intrinsically involves multiple layers of security: hardware, software, in-transit data, storage, network, application, and etcetera.
        - IoT security can only be as strong as its weakest link
        - Complex IoT devices (ex.industrial equipment, connected cars) are the most difficult IoT environments to secure
        - IoT Security Level
        ![](https://i.imgur.com/rWtoOvb.png)
- 5G Threat surface for Massive IoT
    - Using edge computing and having support of Ultra Reliable Low Latency Communication(URLLC)
    - Scenario where hackers exploit zero-day vulnerabilities in MIoT devices to launch a DDoS attack on a 5G RAN
    ![](https://i.imgur.com/nGdZYpR.png)
    - High-level view of 5G threat landscape
    ![](https://i.imgur.com/zffLwXd.png)

    - UEs, the RAN, the core network and operator-hosted or third-party applications and services could be targets from different threat actors

    - UE threat 
        - 4 main catagories:
            - Mobile to Infrastructure: Mobile botnets  controlled by attacker’s (C&C) servers launch DDoS attacks on 5G *infrastructure* aiming to make 5G network services unavailable
            - Mobile to Internet: Mobile botnets controlled by C&C servers launch DDoS attacks on *public websites* through the 5G network
            - Mobile to Mobile: Infected devices launch attacks on other mobile customers with the aim of causing DOS or spreading of malware
            - Internet to Mobile:A malicious server on the internet targets each UE with malware embedded inside.
    - RAN THREATS
        - 5G technology and standards are expected to address the known threats(ex.IMSI paging attack,RBS) at this layer at all access types, including the licensed RAN and unlicensed Wi-Fi.
        - Use of MIMO anttena and operate in millimeter wave  spectrum(less secure than other spectrum) -> The date transmitted and recieve in radio layer expected to be encrypted and integrity protected in higher layer if possible.
        - ROGUE BASE STATION(RBS) THREAT
            - existed since GSM
            - RBS masquerades as a legitimate base station to facilitate a Man-in-The-Middle (MiTM) attack between the mobile user equipment (UE) and the mobile network (include stealing user information, tampering with transmitted information, tracking users, compromising user privacy or causing DoS for 5G services)
        - 5G networks could still have RBS-based threats in following factor
            - A compromised 5G small cell can create an RBS threat to 5G networks and customers
            - An attacker can exploit 5G/LTE interworking requirement to launch a downgrade attack
            - An attacker can exploit a lack of gNB authentication in an idle mode to force the user to camp on an RBS which could lead to a denial of services
    - SUBSCRIBER PRIVACY THREATS
        - potential exposure points for compromising subscriber privacy in 5G networks, using protocol attacks, malware attacks on 5G NFs and insider threats
        ![](https://i.imgur.com/jPIMHMc.png)
        - In 4G IMSI catcher can impersonate BS and capture IMIS meanwhile even force UEs to user no encryption during calls, or use easily breakble encryption to eaversdropping.
        - In 5G SUPI and SUCI are used to slove the problem above, but the attacker may force UEs to communicate in non-5G mode (ex. 3G) which nullify there mitigation.
    - CORE NETWORK THREATS
        - Due to their IP-based service architecture, 5G networks could be vulnerable to IP attacks common over the internet, including DDoS attacks.
        - Infected mobile devices,controlled by malicious (C&C) servers, can launch both user plane and signaling plane attacks on 5G core network functions to degrade or make critical services unavailable 
        - AMF: UE authentication, authorization and mobility management services
        - AUSF: Stores data for authentication of UEs
        - UDM : Stores UE subscription data
        - a DDoS attack against these functions can potentially reduce the availability of 5G services significantly or even cause network outages
    - NETWORK SLICING THREATS
        - The UE needs to be authenticated and authorized for accessing the specific slice.
        - If this signaling is not secured, access to the slice itself may be denied, resulting in a DoS attack
    - NFV AND SDN THREATS 
        - NFV depend on the whole cloud software stack and vulnerabilities in such software components have quite often surfaced in the past.
        - SDN may wreak havoc on a large scale by erroneously or maliciously interacting with a central network controller.
    -  INTERWORKING AND ROAMING THREATS
        -  5G architecture has introduced the SEPP node as the entity to terminate signaling messages between PLMNs through inter-exchange/roaming links
        -  The embedded application layer encryption at the SEPP will provide protection against the known inter-exchange/roaming vulnerabilities that exist in SS7 and DIAMETER protocols
## MITIGATION CONTROLS FOR 5G NETWORK, IOT THREAT MITIGATION & DETECTION AND MITIGATION OF DDOS ATTACKS
- 5G NETWORK THREAT MITIGATION
    - Edge Computing Vulnerability
        ![](https://i.imgur.com/kVRke3x.png)

        ![](https://i.imgur.com/laZ2hYH.png)
        - End point protection (anti-malware)
        - Visualize the network behavior and use policy and segmentation to ensure that we know what is abnormal or an anomaly to avoid threats from spreading and compromising other functions or workloads    
    - Distibuted Core Vulnerability
        - layers of orchestration, NFV, containers, micro-services and virtualized ->packet core
        ![](https://i.imgur.com/n9ggTRL.png)
        - visibility points and the mitigation controls
        ![](https://i.imgur.com/Q4z5l1Y.png)
    - Vitualiztion vulnerability
        - Virtualized workloads bring a new set of threats that include
            - Trust and compromised VNFs
            - VM hopping and sprawl
            - Compromised micro-services
            - Container image vulnerabilities
            ![](https://i.imgur.com/PdhQdQl.png)
        - Visibility, segmentation, DNS level security and detection of abnormal flow
        ![](https://i.imgur.com/RkMz07g.png)
        - visibility 
            - flow analysis
            - ledger of flows and traffic
            - threat feed integration updated in real time
            - application dependencies all on a network segmentation
        - behavior analysis
    - **Mitigation controls, segmentation tools and visibility tools are the key elements of 5G network security**

- IOT THREAT MITIGATION
    - IOT DEVICE 
        - Sensitive data in non-secure device needs to be encrypted and its integrity protected 
        - provided for automatic rollback when update 
        - security isolation between device-resident applications
    - NETWORK/TRANSPORT
        - Mobile networks can enhance IoT security by providing device management and secure bootstrapping, and by verifying device location or platform trustworthiness.
    - NODE/PLATFORM
    