# 5G Visibility
## The unsung hero of 5G visibility–the network packet broker (Reader Forum)
    Link: https://www.rcrwireless.com/20190328/5g/5g-visibility-reader-forum
- 5G is pushing line speeds toward 100G. As a result, network, application, and SIP monitoring solutions just aren’t prepared to capture the influx of the additional traffic (and upgrading those solutions is often cost prohibitive)

- simple solution to the problem of **increased traffic** due to 5G – using new **network packet broker** technology to load balance traffic across lower link speeds

- Stressful it will be for Mobile Network Operator(MNO) with high-loaded traffic
- 5G -> Small Cells -> Small cell backhaul requires many more high-speed links connecting to the wireline network -> All these Links should be protect and monitor
- Network packet brokers:Cut the Band in to small part(segmentation) which makes each part easily managed
- NPB:  efficiently manage traffic to the monitoring tools
- packet broker Consideration
    - Don’t disregard the importance of a TAP. TAPs provide the intermediary function that delivers a fail-safe connection that protects live traffic.
    - Load balancing is the 100G workaround.Divide to several ports
    - Look for packet brokers that “scale out” not “up.” When deploying 5G it’s vital to deploy solution that can scale quickly, without requiring hardware to be pulled for upgrades or swapped out with larger units.
    - Many of the advanced features such as load balancing, port mapping, and filtering are not a standard inclusion in today’s packet 
    - be aware of the movement toward hybrid cloud environments. Deploy a physical packet broker on-premises, use a software-based version of a packet broker on a white-box server, or leverage the basic data-sharing settings in a cloud-based service. 

## The Path to 5G is Paved with Network Visibility
    Link: https://www.extremenetworks.com/extreme-networks-blog/the-path-to-5g-is-paved-with-network-visibility
    
- 5G-capablility and what they must be able to handle:
    -  Mobile data throughput rates that are 1000 times faster 
    -  1000x more devices than are connected
    -  Peak data rates that are 100 times greater
    -  Service deployments that take 1/1000 the time
    -  One tenth the power consumption
    -  Five nines reliability, with much less the latency
     
    ![](https://i.imgur.com/kMsVg4s.png)
- Steering Traffic to Relevant Analytics
    - 5G is software-based, virtualized networks, their visibility and analytics infrastructure. Network packet brokers (NPBs) become critical.
    - Decisions that need to be made in order to properly handle these traffic flows include:
        - Are subscribers being treated fairly and according to their service level agreements?
        - Are the locations of all subscribers and other connected entities correctly identified?
        - Are subscribers and connected entities associated with the right cell towers?
        - Is all traffic secure and free from intrusion or DDoS attacks?
        - Is video and voice being handled properly, whether the requirements are real-time or asynchronous?
    
- Extreme Networks visibility solution.
    ![](https://i.imgur.com/Q2pkYvz.png)
    - Session Correlation
    
    
    
    
- Deployment alternatives for physical and virtual network visibility
    ![](https://i.imgur.com/QMoMUvf.png)
    - Virtual TAPs (deployed in a VM within the hypervisor environment that hosts VNFs) intercept inter-VM traffic and forward relevant traffic flows to centrally deployed physical or virtual network packet brokers for further processing.
    
- Session Director
    - Network Packet Brokers (NPBs) — to aggregate, replicate, and forward relevant network traffic flows to them for analysis   
    -  Session Director session-aware forwarding decisions that are then enforced by the packet broker nodes.
    -  enables operators to deploy best-of-breed analytics tools for each type of network traffic, and adapt to fast-changing monitoring needs


## Network Visibility Important to 5G Success
    Link:https://cadsourcing.com/network-visibility-important-5g-success/
- The network performance key is about pricing and network coverage.
    
## Embedded Network Visibility for Pervasive Real-Time Monitoring and Automated Actions
- Need **comprehensive visibility** into theoperational state of the network and into the traffic that is transiting the network

- The Visibility Challenge
    -  Routers and switches provide clear and comprehensive network visibility can **limit the ability** to quickly, flexibly, and cost-effectively extract the data organizations requirement to meet SLA
    -  Existing approaches to network visibility often suffer from limited comprehensiveness
    - Challenge:
        - Limited in scope : Difficult to address diverse operational needs
        - Inadequate ability:
        - Static
        - Finite capabilities
        - Complex and costly

- Embedded Visibility Solution 
    - **Comprehensive**, **real-time** visibility needed for network operations and automation
    - ability to address **end-user application** or **service needs**, analyze,automate, and generate reports on context-rich data, and provide the fine-grain targeted visibility needed to tune the network for specific device or service needs. 
- Comprehensive Visibility in theDigital Era
    - dynamic, rich, and scalable classification and actions at multiple layers from network to workloads as well as highly flexible, granular real-time visibility of specific flows. 
    - combines both software and hardware innovation
- Extreme SLX Insight Architecture
    - pervasive visibility architecture
    - Extreme SLX-OS software and Extreme SLX platform **hardware** features to provide organizations **unparalleled network visibility** **without impacting** normal network operation or performance. 
    ![](https://i.imgur.com/0DlpSwK.png)
    - Benefits: deploy high-performance and flexible visibility applications via dedicated resources on the platform
    - Dedicated internal and external bandwidth that **allows applications running in the open KVM environment** to extract data  without disrupting forwarding or control plane traffic
    -  KVM environment supports **Wireshark** and **tcpdump** can be accessed via pretested RESTful utilities such as Chrome and Curl

## Network Packet Broker (NPB)
    Link: https://www.netadmin.com.tw/netadmin/zh-tw/feature/AE19E93B821F4B5DBF015A25FC8B18BC
    Link: http://www.gcomtw.com/pro_view.php?id=218&ids=253&gclid=EAIaIQobChMItPPtrrSu4wIVhauWCh0sfQR7EAAYAiAAEgKYs_D_BwE
- NPB先行篩選配送封包 提升網管資安設備效率
- 深度封包檢測（DPI），拆解Layer 2至Layer 7，取出標頭、通訊協定、內容（Payload）等資訊，再利用系統內建工具執行比對、過濾和分析，經過一種設備平台，就需要被開拆解析後再重新封裝傳遞，node 增加就latency就爆炸
- 專司負責以深度封包檢測技術(DPI)對封包進行拆解，再派送到效能管理、資安偵測與防禦平台，以提升整體效能。 Gigamon、IXIA、Netscout、VSS Monitoring等，皆屬於網路封包中介技術供應商
- 以往是用流量複製器（**TAP**），或者仰賴交換器內建的**Port Mirror**功能，將網路流量複製一份送至網管或資安控管設備，再進行深入分析與偵查，但每個node所承受的封包流量均為一致，仍需各自解析封包並篩選資訊。
- PacketX提供的GRISM產品屬進階的網路封包中介方案，其技術可將封包的多層封裝拆解至最初狀態，或者直接透視至最內層封包進行篩選分配。
- Gigamon蒐集篩選流量，Flow Mapping技術，可先行從流量中掌握網路整體連線狀態，再執行分流、派送處理，連線封包有時重複，可先行刪除重複之處，再提供給後端分析，
- Gigamon亦有建構在Hypervisor之上的虛擬主機，也就是GigaVUE-VM軟體。不需要在虛擬主機中安裝任何程式，借助vSwitch機制即可導出流量。
- 但由於Port Mirror本身只負責傳送流量，**不具備確認送達的機制**，當網路流量變大，需要傳送的封包變多，Mirror流量的優先順序將自動被降低，如此一來即無法避免封包遺失問題。因此建議以TAP方式為主，可確保資料的完整性。

![](https://i.imgur.com/voegVk6.png)

- NPM(Network Performance Monitor)
- APM(Application Performance Management)
- CEM(Customer Experience Management)
- NPB功能
    -	Header Stripping: 省去後端分析工具在解析封包標頭時可能遇到的問題，支援: VLAN, MPLS, PPOE…等格式。
    -	Data Capture: 採集過濾後的資料生成PACP檔案供日後分析使用。
    -	De-duplication: 解決自實體網路或虛擬網路各線路中蒐集得的重複封包問題。
    -	Time Stamping: 替封包添加電子時戳，可協助鑑定網路延遲。
    -	Data Masking: 隱蔽封包內容的敏感及私人機密資料如信用卡卡號…等。
    -	Packet Slicing: 裁切封包省去封包內之不必要內容只保留重要資訊以提升後端分析工具的分析效率。
    -	Time Stamping: 替封包添加電子時戳，可協助鑑定網路延遲。



## 5 Reasons to Use a Network Packet Broker
       Link: https://blog.niagaranetworks.com/blog/5-reasons-to-use-a-network-packet-broker

-  Network Packet Broker (NPB) enhance network monitoring for superior network security.
-   NPBs are devices that receive network traffic as input from multiple SPAN ports, then manipulate the traffic by breaking it down into c**hunks of related data and transmitting the data chunks to their respective monitoring and security tools**.


- 5 reasons you should use a Network Packet Broker:
    - Efficient Traffic Filtering:
        -  Efficiently filters the network traffic it receives and routes it to the relevant monitoring tools
        -   NPBs ensures the efficiency, reliability, and effectiveness of each of the monitoring tools.
    -   Secure Removal of Repetitive Data
        - NPB removes all such packets that contain redundant data, which ultimately saves your monitoring tools from being overloaded
    - Network Packet Brokers Optimize Packets
        - Optimize the packets in a number of other ways, including conditional packet slicing and time stamping
    - Capacity for Fault Tolerance
        - support fault tolerance, i.e., the ability to minimize any unwanted downtime that might be caused by unfavorable events like power failures, malfunction
    - Network Packet Brokers for Load Balancing
        - **Load Balancing** is another reason that makes Network Packet Brokers the prime devices to enhance network security. 
        - Effectively divide all the network traffic to their relevant monitoring tools