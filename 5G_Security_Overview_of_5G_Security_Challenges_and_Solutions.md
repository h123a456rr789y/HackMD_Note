# 5G Security (Overview of 5G Security Challenges and Solutions)
## Overview of 5G Security Challenges and Solutions
- MEC, SDN, and (NFV) are sought out to meet the growing user and service demands with-in the constraints of capital expenditures
-  Capital expenditures (CapEx) and operational expenses (OpEx) through flexible network operation and management

- **Multi-tenant** shared cloud infrastructures among multiple virtual network operators require strict **isolation at multiple levels** to avoid illegal resource consumption and maintain integrity of users’ information of different operators 
- Network slicing:security isolation of network slices and security of inter-slice communications
-  SDN: require **strong authentication and authorization** for applications to **avoid misuse** of the network resources exposed to applications through the control plane. 
- VNFs can lead to inter-federated conflicts creating jeopardy in the whole network

### Key Security Challenges in 5G
- Flash network traffic: There will be a high number of end-user devices and new things (IoT).
- Security of radio interfaces: Radio interface encryption keys are sent over insecure channels
- User plane integrity: There is no cryptographic integrity protection for the user data plane
-  Mandated security in the network: Service-driven constraints on the security architecture lead to the optional use of security measures.
- Roaming security: User-security parameters are not updated with roaming from one operator network to another, leading to security compromises with roaming.
- Denial of service (DoS) attacks on the infrastructure: There are visible network control elements and unencrypted control channels.

- Signaling storms: Distributed control systems require coordination, for example, non-access stratum (NAS) layer of (3GPP) protocols.
- DoS attacks on end-user devices: There are no security measures for operating systems,applications, and configuration data on user devices.


### Security Challenges in SDN
- SDN enabling **programmability** and **logically centralizing** the network control planes
- Programmable SDN controller **updates or modifies flow rules** in the data forwarding elements. This control information traffic can **easily be identified**, making it a visible entity in the network and rendering it a favorite choice for DoS attacks.
- Centralization of network control can also make the controller a bottleneck for the whole network in the case of saturation(飽和) attacks
- If malicious application are access or API are exposed can cause havoc DoS

- Current SDN architecture (i.e., OpenFlow) requires the **data forwarding** elements to **store traffic flow** requests until the controller **updates the flow forwarding rules**.->prone to saturation attacks(due to limited flow buffer) 
- Dependence on the controller requires the **control-data planes channel** to be **resilient to security attacks** unlike the current optional use of security protocols and long restoration delays in large networks

- Solution:
    - **Multiple controllers** may solve the challenge of controller availability or increase **resilience** to security attacks. However, misconfiguration of forwarding or inter-federated conflict may also hinder network security policys

### Security Challenges in NFV
- it has basic security challenges such as confidentiality, integrity,authenticity, and non-repudiation

- NFV in mobile networks is the **dynamic** nature of VNFs that leads to configuration errors and thus security lapses
- VNFs are vulnerable to typical cyber-attacks such as spoofing, sniffing, and DoS

-  NFV is also vulnerable to a special set of virtualization threats, such as side-channel attacks, flooding attacks, hypervisor hijacking, malware injection, and virtual machine (VM) migration related attacks, as well as cloud-specific attacks
- Private deployments of NFV are vulnerable only to malicious **insiders** (e.g., a malicious administrator), since remote access to the system is prevented.
- Due to the **common accessibility** of the infrastructure, a malicious user or a compromised provider of VNF can inserting malware or manipulating network traffic by **interfere with the operations**.
- Operational interference and misuse of shared resources are infrastructure-level attacks on NFV
- VNFs fetch dynamically from the cloud, some level of **trust mechanism**(of physical network devices) is needed to prevent malicious VNFs.

### Security Challenges in Mobile Clouds and MEC
- cloud computing systems comprise various resources. It is possible that a user spreads **malicious traffic** to tear down the performance of the whole system, or stealthily access resource of other users.

- **Multi-tenant** cloud networks where tenants run their own control logic, interactions can cause conflicts in network configurations.
- MEC's level of protection is lower than the traditional cloud data center.
- Mobile cloud computing (MCC) migrated edge computing in to 5G ( architectural and infrastructural modifications)
- We catagorize MCC threats according to targeted cloud segments into frontend, back-end, and network-based mobile security threats.
- Front-end Threat
    - range from physical threats to application-based threats
- Back-end Threat
    - targeted toward the mobile cloud servers
- network- based mobile Threat
    - potential attacks include Wi- Fi sniffing, DoS attacks, address impersonation, and session hijacking

- Main MEC concern: **cloud-enabled IoT environment** as well as the **open APIs** through which developers and creators serve contents to MEC applications and end users.
- Third parties can launch various attacks on the MEC environment(with open API).
- DoS attack, man-in-the-middle(MitM) attack, malicious mode problems, privacy leakages, and VM manipulation (security channeled toward the MEC nodes, which include the **MEC server** and other **IoT nodes**)

### Privacy Challenges in 5G
- Concern of user's data, location, and identity
- The application developers andcompanies rarely mention how the data is stored and for what purposes it is going to be used.
- Threats(targeted on location privacy)
    - semantic information attacks(人電腦資訊不對等)
    - timing attacks(通過裝置運算的用時來推斷出所使用的運算操作，通過運算時間推定資料的儲存裝置，或者利用通訊時間差進行資料竊取)
    - boundary attacks
- IMSI catching (fake BS)
- 5G have **different actors** such as virtual mobile network operators (VMNOs), communication service providers (CSPs), and network infrastructure providers ->**synchronization** of mismatching privacy policies among these actors will be a challenge
- Thus, 5G operators will lose full governance of security and privacy.
- No physical boundaries of 5G networks as they use cloud-based data storage and NFV features -> 5G operators have **no direct control of the data storage** place in cloud environments.


## Potential Security Solutions
- SDN and NFV can solve huge network traffic challenges more cost effectively
- SDN:
    - has the capability to enable runtime **resource (e.g., bandwidth)assignment** to particular parts of the network as the need arises. 
    - The SDN controller can **gather network stats(visibility)** through the southbound API from network equipment to see if the traffic levels increase.
- NFV:
    - services from the core network cloud can be transferred toward the **edge** to meet the user requirements.
    - enables the provision of **virtual slices** or resources at runtime to meet the growing traffic demands or surges in traffic at different network locations.
- End-to-end encryption protocol can be used for user plane integrity.
- Roaming security and network- wide mandated security policies can be achieved using **centralized systems** that have global visibility of the users activities and behaviors (e.g., SDN)
- **Signaling storms** will be more challenging due to the excessive   UEs, small BS, and high user mobility. (cloud radio access network **(C-RAN)** and **edge** computing are the potential solutions)

### Security Solutions for SDN
- Having **visiblity** of the network, **centralized control**, and programmability in network elements, SDN enables consistent security **policies** and facilitates **quick threat identification** through a cycle of harvesting intelligence from the network resources, states, and flows.
- Solution:
    - SDN architecture supports **highly reactive** and **proactive security monitoring**, traffic analysis, and response systems to facilitate network forensics, the alteration of security policies, and security service insertion

- SDN is flow- or packet-level granularity that provides **transparency** in terms of packet origin or **source**, the **route** it takes, and even the **content**. 
- Solution:
    - Security applications can **gather samples of flows or packets through** the **control plane** from **any network perimeter** to check their content regardless of the network ingress or egress ports, unlike traditional networks in which the security appliances normally reside in the entry points.
    - This capability of SDN lays the foundation for **network-wide consistent security policies**, early threat identification at any network location, and **quick response** by updating the flow tables to route traffic to **intrusion detection systems (IDSs)** or **firewalls** at runtime.

### Security Solutions for NFV
- The proposed architecture (prsent by European Telecommunications Standards Institute (ETSI))provides security not only to the **virtual functions** in a **multi-tenant environment**, but also to the **physical** entities of a telecommunication network.
- Hypervisors is proposed in to provide **hardware-based protection** to **private information** and **detect corrupt software** in virtualized environments.
- In NFV systems, security protection solutions such as **firewalls** and **IDSs** can be used to prevent **outside** attacks.
- **Identity and access management mechanisms** (e.g., role-based access control) can be used to mitigate the impact of **insider** attacks
- **Infrastructure-level** attacks can be prevented by **monitoring of the resource consumption of each user** and **preventing malicious requests** according to a blacklist of IP addresses.
- In order to increase the trust between different entities,a  chain of **trust relationships** needs to be created and maintained in NFV.
- Solutions based on **cryptographic** techniques, such as **message stream encryption**, can be used to guarantee the confidentiality of VNFs
- Secure outsourcing is another viable solution in NFV to transfer the sensitive information to external networks.(protect sensitive information & validate the integrity of data)

### Security Solutions for Mobile Clouds and MEC
- Main security measures in MCC 
    - **Virtualization** technologies
    - **Redesign of encryption methods**
    - **Dynamic allocation of data processing points.**
- Virtualization comes as a natural option for securing cloud services, since each **end node** connects to a **specific virtual instance** in the cloud via a VM.
- **Isolation** of each user’s virtual connection 
- For specific security threats such as HX-DoS, **learning-based systems** are beter solution.

- To secure the mobile end devices ->anti-malware
- In MCC data and storage, the security framework will consist of **energy-efficient** mechanisms for the **integrity verification** of data and storage services in conjunction with a public provable data possession scheme and some lightweight compromise-resilient storage outsourcing
- Application security, some proposed frameworks are based on securing elastic applications on **mobile devices** for cloud computing, a **lightweight dynamic credential generation mechanism** for user identity protection, an in-device** spatial cloaking mechanism** for privacy protection
- Strategy
    - Use of gateways at strategic points on the networks is highly recommended.(ex. IoT gateway)
    - Ensuring that the application hosted at the edge server **authenticates any user attempting to access the application resources**

- MEC platform should give assurance of data integrity 

### Security Solutions for Privacy in 5G
- 5G will require better mechanisms for accountability, data minimization, transparency, openness, and access control
- A hybrid cloud-based approach is alsorequired where mobile operators are able to store and process **highly sensitive data locally** and **less sensitive data in public clouds**
- Encryption-based system, a message can be encrypted before sending to a location-based services (LBS) provider

- Obfuscation(模糊化) are also crucial, where the quality of location information is reduced in order to protect location privacy.
- Location-cloaking-based(隱藏地點) algorithms are quite useful to handle some major location privacy attacks such as timing and boundary attacks
- IMSI catching attacks(Sloved by SUPI and SUCI)
- Level of privacy security:
    - government-level regulation
    - industry level regulation
    - consumer-level regulation




























































