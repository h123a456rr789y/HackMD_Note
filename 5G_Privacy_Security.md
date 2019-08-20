---
title: 5G Privacy Security
tags: Intern, 5G Security
description: 5g privacy
---




# 5G Privacy Security

## Challenges
- Semantic information attacks (ex: App)
    - 人電信商電腦資訊不對等，APP 要求需要位置，不知道拿去幹嘛
- Timing attacks
    - 通過裝置運算的用時來推斷出所使用的運算操作，通過運算時間推定資料的儲存裝置，或者利用通訊時間差進行資料竊取
- IMSI catching attack (fake BS)
- 5G have different actors such as virtual mobile network operators (VMNOs), communication service providers (CSPs)  synchronization of privacy polices

## IMSI-Catcher Attack solution in 5G
### 3/4G  IMSI
![](https://i.imgur.com/H6XY7RD.png)

- IMSI碼，全球唯一，就像身分證，如果要連接時需要大喊自己的身分證(IMSI)就會變得很容易被追蹤
- 實際上，IMSI不會在每次發訊息都傳，會由臨時的GUTI/TMSI來當暫時身分證，只有在下面的兩個情況會傳自己的IMSI
    - 當手機連到一個新的正常網路
        - 手機會先傳電信營運商分配的臨時身份信息GUTI/TMSI給BS請求接入營運商網路，BS隨後會轉發給Core Network 中的MME，並在MME查詢對應真實身分，才可連線。如果查不到，就請手機發 Identity request，此時手機就傳 IMSI(發生於連接到**新網路**和**roaming到不同MME服務範圍時**)
    - 當手機連到假基地站
        - 手機會自動連到訊號強的BS，透過這樣假基地站可以跟手機要Identity Request ，手機就一直傳IMSI
        
- Q:為什麼IMSI不加密傳輸呢?
ANS:因為在建立安全連接時，一開始網絡不知道手機的身分，要先知道它是誰，才開始交換密鑰，核心網在加密信息前要確定對方的身分沒問題。

### 5G Solution for IMSI Catcher


- 5G決定引入公鑰私鑰的機制，公鑰用來公開並加密(在手機端)，私鑰用來保留並解密(在電信商端)
- 5G裡稱為SUPI（SUbscription Permanent Identifier)類似IMSI，SUCI (SUbscription Concealed Identifier）就是類是公鑰加密過後的IMSI
![](https://i.imgur.com/1C3wmxq.png)
1. 手機向基站gNB發起接入網絡的請求，發送SUCI（即加密的SUPI）或是GUTI
2. gNB收到信息後，轉發至核心網的SEAF（SEcurity Anchor Function）
3. SEAF收到信令後解析後看是GUTI還是SUCI，若是GUTI就匹配到對應的SUPI，若為SUCI則不解密，繼續向AUSF（Authentication Server Function）發起鑑權申請Nausf_UEAuthentication_Authenticate Request，並攜帶對應的網絡服務信息SN-Name，方便AUSF調用對應鑑權算法AV（Authentication Vector，包含RAND, AUTN, HXRES*和K_seaf） 
4. AUSF通過分析SEAF攜帶的網絡信息SN-Name，確定手機是否在網絡服務範圍內，並保存手機需要的網絡服務信息，接下來繼續將SUCI或SUPI和服務網絡信息SN-Name轉發給UDM（Unified Data Management）
5. 在UDM中調用SIDF(Subscription identifier de-concealing function)將SUCI解密得到SUPI，然後通過SUPI來配置手機對應所需的鑑權算法
6. 接下來便會根據手機的鑑權方式一步步提取對應的鑑權秘鑰與鑑權結果，直至最後將結果反饋給手機，手機端USIM會校驗網絡側所發送鑑權結果的真偽

![](https://i.imgur.com/Mtxbrqo.png) 



### But still attacker may force UEs to communicate in non-5G mode (Bidding Down Attack)
