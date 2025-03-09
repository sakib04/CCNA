# **Cisco Router কী?**  

**Router** হল একটি নেটওয়ার্ক ডিভাইস, যা বিভিন্ন নেটওয়ার্কের মধ্যে **ডাটা প্যাকেট রাউট** বা ফরওয়ার্ড করার কাজ করে। এটি একাধিক নেটওয়ার্কের মধ্যে সংযোগ স্থাপন করে এবং ডাটা ট্রান্সফারের জন্য **সর্বোত্তম পথ নির্বাচন** করে।  
**সহজভাবে:** Router হলো নেটওয়ার্কের **ট্রাফিক কন্ট্রোলার**— এটি ঠিক করে কে, কোথায়, কীভাবে ডাটা পাঠাবে।  

---

## **Cisco Router-এর কাজ**
1. **ডাটা ফরওয়ার্ডিং:** এক নেটওয়ার্ক থেকে অন্য নেটওয়ার্কে ডাটা পাঠানো।  
2. **IP Address ব্যবস্থাপনা:** ডিভাইসের মধ্যে সঠিক রুটিং নিশ্চিত করা।  
3. **DHCP Server হিসাবে কাজ:** ক্লায়েন্টদের **IP Address** প্রদান করা (যদি DHCP চালু থাকে)।  
4. **VLAN ট্রাঙ্কিং:** আলাদা VLAN-এর মধ্যে কমিউনিকেশন করা।  
5. **নিরাপত্তা (Security):** ACL (Access Control List) দিয়ে ট্রাফিক ফিল্টার করা।
6. **NAT (Network Address Translation):** Private IP-কে Public IP-তে রূপান্তর করা, ইন্টারনেট ব্যবহারের জন্য। 


---

## **Cisco Router কনফিগারেশন (বেসিক)**
💻 **Step 1: Privileged Mode-এ প্রবেশ করুন**  
```bash
enable
configure terminal
```

💻 **Step 2: Router-এর IP ঠিকানা সেট করুন**  
```bash
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
```

💻 **Step 3: Default Gateway সেট করুন (যদি প্রয়োজন হয়)**  
```bash
ip route 0.0.0.0 0.0.0.0 192.168.1.254
```

💻 **Step 4: কনফিগারেশন সংরক্ষণ করুন**  
```bash
write memory
```

---

## ** Cisco Router বনাম Switch পার্থক্য**  
| বিষয় | Router | Switch |
|---------|------------|------------|
| **কাজ** | নেটওয়ার্ক কানেক্ট করা | ডিভাইস কানেক্ট করা |
| **নেটওয়ার্ক টাইপ** | আলাদা নেটওয়ার্ক (WAN, LAN) সংযুক্ত করে | একই নেটওয়ার্কের ডিভাইস সংযুক্ত করে |
| **ডাটা ফরওয়ার্ডিং** | **IP Address** অনুযায়ী | **MAC Address** অনুযায়ী |
| **Security (নিরাপত্তা)** | ACL, Firewall, NAT সমর্থন করে | শুধুমাত্র VLAN ব্যবহার করে নিরাপত্তা দেয় |

---

## ** Cisco Router-এর ধরন**
- **Edge Router:** ইন্টারনেট সার্ভিস প্রোভাইডার (ISP) বা বড় নেটওয়ার্কে ব্যবহৃত হয়।  
- **Core Router:** বড় প্রতিষ্ঠানের মূল নেটওয়ার্ক পরিচালনার জন্য ব্যবহৃত হয়।  
- **Branch Router:** ছোট অফিস বা ব্রাঞ্চের জন্য ব্যবহৃত হয়।  
- **Wireless Router:** Wi-Fi সাপোর্ট করে এবং ছোট নেটওয়ার্কে ব্যবহৃত হয়।  

---

### ** সারসংক্ষেপ**
- **Router** হল একটি Layer 3 ডিভাইস যা **নেটওয়ার্কের মধ্যে ট্রাফিক ফরওয়ার্ড** করে।  
- এটি **IP Address ব্যবহার করে ডাটা পাঠায়** এবং **NAT, ACL, DHCP** এর মতো ফিচার সাপোর্ট করে।  
- **Cisco Router** সাধারণত কর্পোরেট, ISP, এবং বড় নেটওয়ার্কে ব্যবহৃত হয়।  

---

## **Cisco Router-এ একাধিক IP Address কনফিগার করার পদ্ধতি**  
## **Secondary IP Address ব্যবহার করে**
**একই ফিজিক্যাল ইন্টারফেসে একাধিক IP Address যোগ করতে নিচের স্টেপগুলো অনুসরণ করুন:**

### **কনফিগারেশন স্টেপ**
```bash
Router> enable  
Router# configure terminal  
Router(config)# interface gigabitEthernet 0/1  
Router(config-if)# ip address 192.168.1.1 255.255.255.0  
Router(config-if)# ip address 192.168.2.1 255.255.255.0 secondary  
Router(config-if)# exit  
Router(config)# write memory  
```
### **ব্যাখ্যা:**
- **192.168.1.1/24** → প্রথম IP (প্রাইমারি)  
- **192.168.2.1/24** → দ্বিতীয় IP (সেকেন্ডারি)  
- `secondary` **কমান্ডটি ব্যবহারের ফলে একই ইন্টারফেসে একাধিক IP সেট করা সম্ভব হয়।**  

---
### **একটি ফিজিক্যাল পোর্টে সর্বোচ্চ কতটি IP অ্যাড্রেস কনফিগার করা যায়?**  

একটি **Cisco Router-এর** একক **Physical Interface**-এ **Secondary IP Address** ব্যবহার করে **250+ IP Address** কনফিগার করা সম্ভব। তবে, সঠিক সীমা নির্ভর করে **Router Model, IOS Version এবং Hardware Limitations** এর উপর।  

---

## **Cisco Router-এ একক ইন্টারফেসে কতগুলো IP সেট করা সম্ভব?**
### **১. Secondary IP Address ব্যবহার করলে:**
Cisco IOS-এ, **প্রতি ইন্টারফেসে সাধারণত 250-500 পর্যন্ত IP Address** দেওয়া সম্ভব **(সাপোর্টেড মডেল অনুযায়ী ভিন্ন হতে পারে)**।  
 
**Example (Multiple IP Configuration)**:
```bash
Router(config)# interface gigabitEthernet 0/1  
Router(config-if)# ip address 192.168.1.1 255.255.255.0  
Router(config-if)# ip address 192.168.2.1 255.255.255.0 secondary  
Router(config-if)# ip address 192.168.3.1 255.255.255.0 secondary  
Router(config-if)# ip address 192.168.4.1 255.255.255.0 secondary  
Router(config-if)# ip address 192.168.5.1 255.255.255.0 secondary  
...
Router(config-if)# exit  
Router# write memory  
```
**এই পদ্ধতিতে অনেকগুলো সাবনেট একসাথে ব্যবহার করা যায়, তবে অনেক বেশি IP অ্যাড্রেস অ্যাড করলে পারফরম্যান্স কমতে পারে।**  

---

### **২. VLAN Sub-Interfaces ব্যবহার করলে:**
VLAN **(802.1Q tagging)** ব্যবহার করে **1000+ IP Address** সেট করা সম্ভব, কারণ এখানে প্রতিটি VLAN আলাদা একটি **Sub-Interface** হিসেবে কাজ করে।  

**Example (Multiple VLAN Sub-Interfaces)**:
```bash
Router(config)# interface gigabitEthernet 0/1.10  
Router(config-subif)# encapsulation dot1Q 10  
Router(config-subif)# ip address 192.168.10.1 255.255.255.0  
Router(config-subif)# exit  

Router(config)# interface gigabitEthernet 0/1.20  
Router(config-subif)# encapsulation dot1Q 20  
Router(config-subif)# ip address 192.168.20.1 255.255.255.0  
Router(config-subif)# exit  

Router(config)# interface gigabitEthernet 0/1.30  
Router(config-subif)# encapsulation dot1Q 30  
Router(config-subif)# ip address 192.168.30.1 255.255.255.0  
Router(config-subif)# exit  
```
**এই পদ্ধতিতে হাজারের বেশি VLAN এবং IP অ্যাড্রেস সেট করা সম্ভব, কারণ এখানে প্রতিটি VLAN আলাদা ভাবে কাজ করে।**  

---

## **Cisco Router-এর Hardware Limitations**
| **Router Model** | **Secondary IP Support** | **VLAN Sub-Interfaces Support** |
|-----------------|--------------------------|---------------------------------|
| **Cisco 2800/2900** | 250+ | 1000+ VLAN |
| **Cisco 3900/4000** | 500+ | 4000+ VLAN |
| **Cisco ASR Routers** | 1000+ | 8000+ VLAN |

**High-end Cisco routers (e.g., ASR series) অনেক বেশি IP অ্যাড্রেস এবং VLAN Sub-Interfaces হ্যান্ডেল করতে পারে।**  

---

## **উপসংহার:**
  - **Secondary IP Address** পদ্ধতিতে **250+ IP Address** ব্যবহার করা যায়।  
  - **VLAN Sub-Interfaces** ব্যবহার করলে **1000+ IP Address** সেট করা সম্ভব।  
  - **Router Model এবং Hardware Capacity অনুযায়ী সর্বোচ্চ লিমিট ভিন্ন হতে পারে।**  

আপনি যদি **বড় নেটওয়ার্ক** পরিচালনা করতে চান, তাহলে **VLAN এবং Sub-Interface** পদ্ধতিই সবচেয়ে ভালো।  


# **Static Route (স্ট্যাটিক রুট) কি?**  

**Static Route** হল এমন একটি **Routing Method**, যেখানে ম্যানুয়ালি **IP Route** নির্ধারণ করা হয়। **Router** বা **Layer 3 Switch** স্বয়ংক্রিয়ভাবে পথ খোঁজার পরিবর্তে **Network Administrator**-ই **Routes** নির্দিষ্ট করে দেয়।  

**সহজ ভাষায়:** Static Route মানে **নিজ হাতে নির্দিষ্ট করা পথ** যেখানে ডাটা যাবে।  

---

## **Static Route-এর বৈশিষ্ট্য**  
✔ **Manual Configuration:** নেটওয়ার্ক অ্যাডমিনকে প্রতিটি রুট ম্যানুয়ালি কনফিগার করতে হয়।  
✔ **Fast & Secure:** ডাটা ফরোয়ার্ডিং দ্রুত হয় এবং অপ্রয়োজনীয় ট্রাফিক কম থাকে।  
✔ **Low CPU Usage:** Dynamic Routing Protocol (OSPF, EIGRP) এর তুলনায় কম CPU ব্যবহার করে।  
✔ **No Automatic Updates:** যদি নেটওয়ার্ক পরিবর্তন হয়, তাহলে রুট ম্যানুয়ালি আপডেট করতে হয়।  

---

## **Static Route কনফিগারেশন (Cisco Router)**  
ধরি, আমাদের নেটওয়ার্ক **Router A** এবং **Router B**-এর মধ্যে সংযোগ স্থাপন করতে হবে।  

**নেটওয়ার্ক টপোলজি:**  
- **Router A:** `192.168.1.1/24`  
- **Router B:** `192.168.2.1/24`  
- **সংযোগকারী নেটওয়ার্ক:** `10.0.0.0/30`  

---

### **Step 1: Router A-তে Static Route যোগ করুন**  
```bash
enable
configure terminal
ip route 192.168.2.0 255.255.255.0 10.0.0.2
exit
write memory
```
**মানে:** `192.168.2.0/24` নেটওয়ার্কে যেতে হলে **Router B-এর IP (10.0.0.2)** ব্যবহার করতে হবে।

---

### **Step 2: Router B-তে Static Route যোগ করুন**  
```bash
enable
configure terminal
ip route 192.168.1.0 255.255.255.0 10.0.0.1
exit
write memory
```
**মানে:** `192.168.1.0/24` নেটওয়ার্কে যেতে হলে **Router A-এর IP (10.0.0.1)** ব্যবহার করতে হবে।

---

## **Static Route চেক ও ডিবাগ করা**  
**Static Route গুলো ঠিকমতো কাজ করছে কিনা চেক করতে:**  
```bash
show ip route
```
**নেটওয়ার্ক রিচেবল কিনা পিং করে টেস্ট করুন:**  
```bash
ping 192.168.2.1
```
**রাউটিং প্রসেস ডিবাগ করতে:**  
```bash
debug ip routing
```

---

## **Static Route vs Dynamic Routing**  

| বিষয় | **Static Route** | **Dynamic Route (OSPF, EIGRP)** |
|---------|----------------|------------------|
| **কনফিগারেশন** | ম্যানুয়ালি নির্ধারণ করতে হয় | স্বয়ংক্রিয়ভাবে Route শিখতে পারে |
| **নেটওয়ার্ক পরিবর্তন** | ম্যানুয়ালি আপডেট করতে হয় | নিজে নিজে আপডেট হয় |
| **সুবিধা** | দ্রুত ও নিরাপদ | বড় নেটওয়ার্কের জন্য সহজ |
| **অপসারণ** | নেটওয়ার্ক পরিবর্তন হলে কাজ নাও করতে পারে | নতুন রুট স্বয়ংক্রিয়ভাবে শিখতে পারে |

---

## **কবে Static Route ব্যবহার করবো?**  
- **ছোট নেটওয়ার্কে, যেখানে Route পরিবর্তন হয় না।**  
- **সিকিউরিটি দরকার হলে, যাতে Router অপ্রয়োজনীয় Route না শেখে।**  
- **Backup Route হিসেবে, Dynamic Routing ব্যর্থ হলে।**  

---

### **সারসংক্ষেপ**  
- **Static Route** হল **ম্যানুয়ালি নির্ধারিত রাউটিং**।  
- এটি **দ্রুত, নির্ভরযোগ্য, এবং কম CPU ব্যবহার করে।**  
- কিন্তু **বড় নেটওয়ার্কের জন্য Dynamic Routing বেশি কার্যকর।**  
- **Cisco Router-এ "ip route" কমান্ড দিয়ে Static Route সেট করা যায়।**  


### রাউটার 0 আইপি কনফিগার
```
enable
config ter
interface loopback 0 
no shut
ip address 1.1.1.1 255.255.255.255
exit
interface gigabitEthernet 0/0
no shut
ip address 10.1.1.1 255.255.255.0
exit
exit
sh ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     1.0.0.0/32 is subnetted, 1 subnets
C       1.1.1.1/32 is directly connected, Loopback0
     10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.1.1.0/24 is directly connected, GigabitEthernet0/0
L       10.1.1.1/32 is directly connected, GigabitEthernet0/0

sh ip int brief
Interface              IP-Address      OK? Method Status                Protocol 
GigabitEthernet0/0     10.1.1.1        YES manual up                    up 
GigabitEthernet0/1     unassigned      YES unset  administratively down down 
Loopback0              1.1.1.1         YES manual up                    up 
Vlan1                  unassigned      YES unset  administratively down down

```


### রাউটার 1 আইপি কনফিগার
```
enable
config ter
interface loopback 0 
no shut
ip address 2.2.2.2 255.255.255.255
exit
interface gigabitEthernet 0/0
no shut
ip address 10.1.1.2 255.255.255.0
exit
interface gigabitEthernet 0/1
no shut
ip add 10.1.2.1 255.255.255.0
exit
do sh ip int brief

Interface              IP-Address      OK? Method Status                Protocol 
GigabitEthernet0/0     10.1.1.2        YES manual up                    up 
GigabitEthernet0/1     10.1.2.1        YES manual up                    down 
Loopback0              2.2.2.2         YES manual up                    up 
Vlan1                  unassigned      YES unset  administratively down down

do sh ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     2.0.0.0/32 is subnetted, 1 subnets
C       2.2.2.2/32 is directly connected, Loopback0
     10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.1.1.0/24 is directly connected, GigabitEthernet0/0
L       10.1.1.2/32 is directly connected, GigabitEthernet0/0
```

### রাউটার 2 আইপি কনফিগার
```
enable
config ter
interface loopback 0 
no shut
ip address 3.3.3.3 255.255.255.255
exit
interface gigabitEthernet 0/0
no shut
ip address 10.1.2.2 255.255.255.0
exit
do sh ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     3.0.0.0/32 is subnetted, 1 subnets
C       3.3.3.3/32 is directly connected, Loopback0
     10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.1.2.0/24 is directly connected, GigabitEthernet0/0
L       10.1.2.2/32 is directly connected, GigabitEthernet0/0

do sh ip int brief
Interface              IP-Address      OK? Method Status                Protocol 
GigabitEthernet0/0     10.1.2.2        YES manual up                    up 
GigabitEthernet0/1     unassigned      YES unset  administratively down down 
Loopback0              3.3.3.3         YES manual up                    up 
Vlan1                  unassigned      YES unset  administratively down down
```
### রাউটার 0 রুট কনফিগার 
```
ip route 10.1.2.0 255.255.255.0 10.1.1.2
ip route  2.2.2.2 255.255.255.255 10.1.1.2
ip route 3.3.3.3 255.255.255.255 10.1.1.2
do sh ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     1.0.0.0/32 is subnetted, 1 subnets
C       1.1.1.1/32 is directly connected, Loopback0
     2.0.0.0/32 is subnetted, 1 subnets
S       2.2.2.2/32 [1/0] via 10.1.1.2
     3.0.0.0/32 is subnetted, 1 subnets
S       3.3.3.3/32 [1/0] via 10.1.1.2
     10.0.0.0/8 is variably subnetted, 3 subnets, 2 masks
C       10.1.1.0/24 is directly connected, GigabitEthernet0/0
L       10.1.1.1/32 is directly connected, GigabitEthernet0/0
S       10.1.2.0/24 [1/0] via 10.1.1.2
```

### রাউটার 1 রুট কনফিগার 
```
ip route 3.3.3.3 255.255.255.255 10.1.2.2
ip route 1.1.1.1 255.255.255.255 10.1.1.1

 do sh ip cef
Prefix               Next Hop             Interface
0.0.0.0/0            no route
0.0.0.0/8            drop                 
0.0.0.0/32           receive              
2.2.2.2/32           receive              Loopback0
3.3.3.3/32             next hop 10.1.2.2 GigabitEthernet0/1
10.1.1.0/24          attached             GigabitEthernet0/0
10.1.1.0/32          receive              GigabitEthernet0/0
10.1.1.1/32          10.1.1.1             GigabitEthernet0/0
10.1.1.2/32          receive              GigabitEthernet0/0
10.1.1.255/32        receive              GigabitEthernet0/0
10.1.2.0/24          attached             GigabitEthernet0/1
10.1.2.0/32          receive              GigabitEthernet0/1
10.1.2.1/32          receive              GigabitEthernet0/1
10.1.2.2/32          10.1.2.2             GigabitEthernet0/1
10.1.2.255/32        receive              GigabitEthernet0/1
127.0.0.0/8          drop                 
224.0.0.0/4          drop                 
224.0.0.0/24         receive              
240.0.0.0/4          drop                 
255.255.255.255/32   receive      


do sh ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     1.0.0.0/32 is subnetted, 1 subnets
S       1.1.1.1/32 [1/0] via 10.1.1.1
     2.0.0.0/32 is subnetted, 1 subnets
C       2.2.2.2/32 is directly connected, Loopback0
     3.0.0.0/32 is subnetted, 1 subnets
S       3.3.3.3/32 [1/0] via 10.1.2.2
     10.0.0.0/8 is variably subnetted, 4 subnets, 2 masks
C       10.1.1.0/24 is directly connected, GigabitEthernet0/0
L       10.1.1.2/32 is directly connected, GigabitEthernet0/0
C       10.1.2.0/24 is directly connected, GigabitEthernet0/1
L       10.1.2.1/32 is directly connected, GigabitEthernet0/1

```

### রাউটার 2 রুট কনফিগার 
```

ip route 10.1.1.0 255.255.255.0 10.1.2.1
ip route 1.1.1.1 255.255.255.255 10.1.2.1
ip route  2.2.2.2 255.255.255.255 10.1.2.1
do sh ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     1.0.0.0/32 is subnetted, 1 subnets
S       1.1.1.1/32 [1/0] via 10.1.2.1
     2.0.0.0/32 is subnetted, 1 subnets
S       2.2.2.2/32 [1/0] via 10.1.2.1
     3.0.0.0/32 is subnetted, 1 subnets
C       3.3.3.3/32 is directly connected, Loopback0
     10.0.0.0/8 is variably subnetted, 3 subnets, 2 masks
S       10.1.1.0/24 [1/0] via 10.1.2.1
C       10.1.2.0/24 is directly connected, GigabitEthernet0/0
L       10.1.2.2/32 is directly connected, GigabitEthernet0/0


```
### এখন চেকআপের জন্য
```enable
debug ip icmp
debug ip packet
```
### undebug জন্য
```
undebug all
```
