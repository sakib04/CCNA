# SSH কনফিগার
Cisco switch-এ SSH কনফিগার করার জন্য নিচের স্টেপগুলো অনুসরণ করুন:

### ১. **হোস্টনেম এবং ডোমেইন নাম সেট করুন:**
SSH ব্যবহারের জন্য সুইচের হোস্টনেম এবং ডোমেইন নাম কনফিগার করা প্রয়োজন।

```bash
Switch# configure terminal
Switch(config)# hostname YourSwitchName
Switch(config)# ip domain-name yourdomain.com
```

### ২. **RSA কী জেনারেট করুন:**
SSH এনক্রিপশন ব্যবহৃত হয়, তাই নিরাপদ যোগাযোগের জন্য RSA কী জেনারেট করতে হবে।

```bash
Switch(config)# crypto key generate rsa
```
আপনি যখন কী সাইজের জন্য প্রম্পট পাবেন, তখন কমপক্ষে ১০২৪ বিট নির্বাচন করুন (২০৪৮ বিট নিরাপত্তার জন্য ভালো)।

```bash
The key modulus size is 2048
```

### ৩. **SSH সংস্করণ ২ সক্রিয় করুন:**
Cisco সুইচগুলি SSH সংস্করণ ১ এবং সংস্করণ ২ উভয়ই সাপোর্ট করে, তবে সংস্করণ ২ নিরাপদ। SSH সংস্করণ ২ সক্রিয় করতে নিচের কমান্ড ব্যবহার করুন:

```bash
Switch(config)# ip ssh version 2
```

### ৪. **একটি ব্যবহারকারীর নাম এবং পাসওয়ার্ড তৈরি করুন:**
SSH লগইন অ্যাক্সেসের জন্য একটি ব্যবহারকারীর নাম এবং পাসওয়ার্ড তৈরি করতে হবে।

```bash
Switch(config)# username yourusername privilege 15 secret yourpassword
```
- `privilege 15` পুরো প্রশাসনিক অ্যাক্সেস দেয়।
- `yourusername` এবং `yourpassword` পরিবর্তন করে আপনার পছন্দসই ব্যবহারকারীর নাম এবং পাসওয়ার্ড দিন।

### ৫. **VTY লাইনগুলিকে SSH অ্যাক্সেসের জন্য সক্ষম করুন:**
VTY লাইনগুলিতে SSH অ্যাক্সেস সক্ষম করতে হবে।

```bash
Switch(config)# line vty 0 15
Switch(config-line)# transport input ssh
Switch(config-line)# login local
```
এখানে, `line vty 0 15` মানে ০ থেকে ১৫ পর্যন্ত সকল VTY লাইন কনফিগার করা হবে।

### ৬. **SSH এর জন্য সুইচ রিবুট করুন:**
সব কনফিগারেশন করার পর, SSH অ্যাক্সেস পরীক্ষা করতে সুইচ রিবুট করতে পারেন বা শুধু SSH ব্যবহার করে সুইচে লগইন করার চেষ্টা করুন।

এখন আপনি SSH দিয়ে সুইচে লগইন করতে পারবেন। SSH ক্লায়েন্টের মাধ্যমে আপনার সুইচের IP ব্যবহার করে লগইন করুন:

```bash
ssh yourusername@Switch_IP_address
```

 ### উদাহরণ

```bash
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#
Switch(config)#hostname ? [হোস্টনেম]
  WORD  This system's network name
Switch(config)#hostname cisco
cisco(config)#
cisco(config)#ip domain?
domain  domain-lookup  domain-name  
cisco(config)#ip domain-n
cisco(config)#ip domain-name ? [ ডোমেইন নাম]
  WORD  Default domain name
cisco(config)#ip domain-name cisco.com?
WORD  
cisco(config)#ip domain-name cisco.com
cisco(config)#
cisco(config)#crypto ? [*RSA কী জেনারেট]
  key  Long term key operations
cisco(config)#crypto key ?
  generate  Generate new keys
  zeroize   Remove keys
cisco(config)#crypto key gene
cisco(config)#crypto key generate ?
  rsa  Generate RSA keys
cisco(config)#crypto key generate rs
cisco(config)#crypto key generate rsa ?
  general-keys  Generate a general purpose RSA key pair for signing and
                encryption
  <cr>
cisco(config)#crypto key generate rsa 
The name for the keys will be: cisco.cisco.com
Choose the size of the key modulus in the range of 360 to 4096 for your
  General Purpose Keys. Choosing a key modulus greater than 512 may take
  a few minutes.

How many bits in the modulus [512]: 512
% Generating 512 bit RSA keys, keys will be non-exportable...[OK]

cisco(config)#
cisco(config)# ip ?
*Mar 1 0:4:30.372: RSA key size needs to be at least 768 bits for ssh version 2
*Mar 1 0:4:30.372: %SSH-5-ENABLED: SSH 1.5 has been enabled
  access-list      Named access-list
  arp              IP ARP global configuration
  default-gateway  Specify default gateway (if not routing IP)
  dhcp             Configure DHCP server and relay parameters
  domain           IP DNS Resolver
  domain-lookup    Enable IP Domain Name System hostname translation
  domain-name      Define the default domain name
  ftp              FTP configuration commands
  host             Add an entry to the ip hostname table
  name-server      Specify address of name server to use
  scp              Scp commands
  ssh              Configure ssh options
cisco(config)# ip ssh ?  [SSH ]
  authentication-retries  Specify number of authentication retries
  time-out                Specify SSH time-out interval
  version                 Specify protocol version to be supported
cisco(config)# ip ssh ver
cisco(config)# ip ssh version ?
  <1-2>  Protocol version
cisco(config)# ip ssh version 2
Please create RSA keys (of at least 768 bits size) to enable SSH v2.
cisco(config)#username ?  [username & Password]
  WORD  User name
cisco(config)#username cisco?
WORD  
cisco(config)#username cisco ?
  password   Specify the password for the user
  privilege  Set user privilege level
  secret     Specify the secret for the user
  <cr>
cisco(config)#username cisco se
cisco(config)#username cisco secret ? 
  0     Specifies an UNENCRYPTED secret will follow
  5     Specifies a HIDDEN secret will follow
  LINE  The UNENCRYPTED (cleartext) user secret
cisco(config)#username cisco secret cisco
cisco(config)#
cisco(config)#do show run
Building configuration...

Current configuration : 1178 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname cisco
!
!
!
ip ssh version 1
ip domain-name cisco.com
!
username cisco secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0   [username & passsowrd]
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
 --More-- 
cisco(config)#do show ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual up                    up 
FastEthernet0/2        unassigned      YES manual down                  down 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual down                  down 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual down                  down 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  unassigned      YES manual administratively down down

cisco(config)#interface
cisco(config)#interface vlan 1
cisco(config-if)#no shutdown

cisco(config-if)#
%LINK-5-CHANGED: Interface Vlan1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up

cisco(config-if)#do show ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual up                    up 
FastEthernet0/2        unassigned      YES manual down                  down 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual down                  down 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual down                  down 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  unassigned      YES manual up                    up

cisco(config-if)#ip address 192.168.0.2 255.255.255.0
cisco(config-if)#do show ip interface brief
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual up                    up 
FastEthernet0/2        unassigned      YES manual down                  down 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual down                  down 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual down                  down 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  192.168.0.2     YES manual up                    up
cisco(config)#ip default-gateway 192.168.0.1
cisco(config)#line vty 0 15
cisco(config-line)#password ?
  7     Specifies a HIDDEN password will follow
  LINE  The UNENCRYPTED (cleartext) line password
cisco(config-line)#password cisco
cisco(config-line)#login
cisco(config-line)#exit
cisco(config-line)#password ?
  7     Specifies a HIDDEN password will follow
  LINE  The UNENCRYPTED (cleartext) line password
cisco(config-line)#password cisco
cisco(config-line)#login
cisco(config-line)#exit
cisco(config)#enable secret cisco
cisco(config)#service passw
cisco(config)#service password-encryption 
cisco(config)#do show run 
Building configuration...

Current configuration : 1320 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname cisco
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
ip ssh version 1
ip domain-name cisco.com
!
username cisco secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 ip address 192.168.0.2 255.255.255.0
!
ip default-gateway 192.168.0.1
!
!
!
!
line con 0
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 password 7 0822455D0A16
 login
!
!
!
!
end

cisco(config)#line vty 0 15  [ssh/telnet allow]
cisco(config-line)#trans
cisco(config-line)#tra
cisco(config-line)#transport ?
  input   Define which protocols to use when connecting to the terminal server
  output  Define which protocols to use for outgoing connections
cisco(config-line)#transport inpu
cisco(config-line)#transport input ?
  all     All protocols
  none    No protocols
  ssh     TCP/IP SSH protocol
  telnet  TCP/IP Telnet protocol
cisco(config-line)# transport input all 
cisco(config-line)# do show run
Building configuration...

Current configuration : 1320 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname cisco
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
ip ssh version 1
ip domain-name cisco.com
!
username cisco secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 ip address 192.168.0.2 255.255.255.0
!
ip default-gateway 192.168.0.1
!
!
!
!
line con 0
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 password 7 0822455D0A16
 login
!
!
!
!
end
```

এই ছিলো SSH কনফিগারেশন প্রক্রিয়া!
# পোর্ট সিকিউরিটি
সিস্কো পোর্ট সিকিউরিটি কনফিগার করার জন্য নিম্নলিখিত স্টেপগুলি অনুসরণ করতে পারেন:

### 1. পোর্ট সিকিউরিটি সক্রিয় করা
প্রথমে, আপনাকে পোর্টটি সিলেক্ট করতে হবে যেটি সিকিউরিটি কনফিগার করতে চান। এরপর, আপনি সেই পোর্টে সিকিউরিটি অ্যাক্টিভেট করবেন। উদাহরণস্বরূপ, যদি আপনি ইথারনেট পোর্ট 0/1 ব্যবহার করেন, তাহলে:

```bash
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# switchport port-security
```
### Violation Shutdown
**Port Security Violation Shutdown** হল একটি পোর্ট সিকিউরিটি অ্যাকশন যা তখন কার্যকর হয় যখন পোর্টে কোনো **অননুমোদিত** MAC অ্যাড্রেস সংযুক্ত হয়, অথবা যদি পোর্টে ব্যবহৃত MAC অ্যাড্রেসের সংখ্যা সীমার বাইরে চলে যায়। এই অবস্থায়, পোর্টটি **অটোমেটিক্যালি বন্ধ (shutdown)** হয়ে যায় এবং সেই পোর্টে আর কোনো ট্র্যাফিক পাস করতে পারে না যতক্ষণ না ম্যানুয়ালি পুনরায় পোর্টটি চালু করা হয়।

### Violation Shutdown এর কার্যপ্রণালী:
1. **অননুমোদিত MAC অ্যাড্রেস সংযুক্ত হলে**: যদি কোনো ডিভাইসের MAC অ্যাড্রেস পোর্ট সিকিউরিটি কনফিগারেশনের সাথে মেলেনা, তবে পোর্টটি **shutdown** হয়ে যাবে।
2. **MAC অ্যাড্রেস সীমা অতিক্রম হলে**: যদি পোর্টে অনুমোদিত MAC অ্যাড্রেসের সংখ্যা সীমা ছাড়িয়ে যায়, তবে পোর্টটি বন্ধ হয়ে যাবে।
3. **পোর্ট বন্ধ হওয়ার পর**: পোর্টটি **err-disable (error-disabled)** হয়ে যাবে, অর্থাৎ পোর্টটি ডাউন হয়ে যাবে এবং নতুন সংযোগ গ্রহণ করবে না।

### Violation Shutdown কনফিগারেশন:
আপনি যদি চান যে, যখন কোনো violation (ভায়োলেশন) ঘটবে তখন পোর্টটি বন্ধ হয়ে যাবে, তাহলে নিম্নলিখিত কমান্ডটি ব্যবহার করবেন:

```bash
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security violation shutdown
```

### কনফিগারেশন ব্যাখ্যা:
- `switchport port-security`: পোর্ট সিকিউরিটি সক্রিয় করে।
- `switchport port-security violation shutdown`: যদি কোনো violation ঘটে (যেমন, কোনো অননুমোদিত MAC অ্যাড্রেস সংযুক্ত হলে), তখন পোর্টটি **shutdown** হয়ে যাবে।

### পোর্টটি পুনরায় চালু করা:
যদি পোর্টটি **shutdown** হয়ে যায়, তাহলে আপনাকে ম্যানুয়ালি পোর্টটি পুনরায় **up** করতে হবে। আপনি এটি `shutdown` এবং `no shutdown` কমান্ড দিয়ে করতে পারেন:

```bash
Switch(config-if)# shutdown
Switch(config-if)# no shutdown
```

### Violation Shutdown এর সুবিধা:
- **সুরক্ষা**: পোর্ট সিকিউরিটি ভায়োলেশন হলে পোর্টটি বন্ধ হয়ে যাওয়ায়, অননুমোদিত ডিভাইস বা মালিসিয়াস ডিভাইস নেটওয়ার্কে প্রবেশ করতে পারে না।
- **স্বয়ংক্রিয় প্রতিক্রিয়া**: পোর্টটি বন্ধ হয়ে যাওয়ায় আপনি দ্রুত সমস্যার চিহ্নিত করতে পারবেন এবং ডিভাইসটির সাথে সম্পর্কিত কোনো সমস্যা সমাধান করতে পারবেন।

### Violation Shutdown Troubleshooting:
যদি পোর্টটি **err-disable** হয়ে যায়, তাহলে এটি চেক করতে পারেন:

```bash
Switch# show interface status err-disabled
```

এবং পোর্টটি পুনরায় সক্রিয় করতে:

```bash
Switch# show port-security interface fastEthernet 0/1
Switch# clear port-security sticky interface fastEthernet 0/1
```

এভাবে, **Violation Shutdown** পোর্ট সিকিউরিটির একটি গুরুত্বপূর্ণ অংশ যা নেটওয়ার্কের নিরাপত্তা নিশ্চিত করে।
### 2. পোর্ট সিকিউরিটির নিয়ম সেট করা
আপনার পোর্ট সিকিউরিটির জন্য কিছু প্যারামিটার কনফিগার করতে হবে, যেমন:

- **ম্যাক অ্যাড্রেস সীমা**: কতটি MAC অ্যাড্রেস পোর্টে অনুমোদিত হবে
- **অ্যাকশন**: যদি কোনো নিষিদ্ধ ডিভাইস পোর্টে সংযুক্ত হয় তাহলে কি হবে (সেটআপ করা যেতে পারে "restrict", "protect", বা "shutdown" অ্যাকশন)
- **MAC অ্যাড্রেস লক করা**: পোর্টে ম্যানুয়ালি নির্দিষ্ট MAC অ্যাড্রেস সেট করা।
- **Port Security Sticky Mode** সিস্কো সুইচে একটি ফিচার যা পোর্টে সংযুক্ত MAC অ্যাড্রেসগুলোকে **স্বয়ংক্রিয়ভাবে সুরক্ষিত** করে রাখে। এই মোডে, যখন একটি ডিভাইস প্রথমবারের মতো একটি পোর্টে সংযুক্ত হয়, তখন পোর্টটি ঐ ডিভাইসের MAC অ্যাড্রেসটিকে "sticky" হিসেবে স্মরণ করে রাখে। এর মানে হলো, সিস্কো সুইচ ঐ MAC অ্যাড্রেসটিকে পোর্ট সিকিউরিটির তালিকায় অস্থায়ীভাবে যোগ করে এবং ভবিষ্যতে ঐ MAC অ্যাড্রেসটি শুধুমাত্র ঐ পোর্টে ব্যবহৃত হতে পারে।

Sticky মোডে কনফিগার করলে, ডিভাইসটির MAC অ্যাড্রেসটি সেই পোর্টে স্টোর হয়ে যায় এবং পুনরায় সুইচ রিস্টার্ট হলে, সিস্টেম ঐ MAC অ্যাড্রেসগুলো আবারও স্বয়ংক্রিয়ভাবে পুনরুদ্ধার করে, এর ফলে নতুন করে MAC অ্যাড্রেস যুক্ত করার প্রয়োজন হয় না।

#### Sticky Mode-এর সুবিধা:
1. **স্বয়ংক্রিয় MAC অ্যাড্রেস সংরক্ষণ**: আপনি যখন কোনো ডিভাইস সংযুক্ত করেন, তখন ঐ ডিভাইসের MAC অ্যাড্রেস পোর্টে স্বয়ংক্রিয়ভাবে যুক্ত হয়ে যায়।
2. **সুরক্ষা**: এটি পোর্টে শুধুমাত্র অনুমোদিত MAC অ্যাড্রেসগুলো সংযুক্ত থাকতে নিশ্চিত করে, ফলে নকল বা অননুমোদিত ডিভাইসের সংযোগ বন্ধ হয়ে যায়।
3. **কনফিগারেশন সহজ করা**: আপনি ম্যানুয়ালি MAC অ্যাড্রেস কনফিগার না করে, শুধুমাত্র Sticky মোড ব্যবহার করে সমস্ত MAC অ্যাড্রেস কনফিগার করতে পারেন।

#### Sticky Mode-এর কাজের পদ্ধতি:
- যখন একটি ডিভাইস প্রথমবার পোর্টে সংযুক্ত হয়, তখন ঐ MAC অ্যাড্রেসটি সিস্কো সুইচে `sticky` হিসেবে সংরক্ষিত হয়ে যায়।
- ঐ MAC অ্যাড্রেসটির পরে যদি পোর্টে আরেকটি ডিভাইস সংযুক্ত করা হয় যার MAC অ্যাড্রেসটি আগে থেকেই স্টোর করা থাকে, তবে ঐ ডিভাইসটি পোর্টে কাজ করবে।
- যদি ঐ MAC অ্যাড্রেসটির সীমা পার হয়ে যায় বা অন্য কোনো অননুমোদিত MAC অ্যাড্রেস সংযুক্ত হয়, তখন নির্দিষ্ট অ্যাকশন যেমন `restrict`, `shutdown`, বা `protect` কার্যকর হয়।

#### Sticky Mode কনফিগার করার উদাহরণ:
```bash
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security mac-address sticky
Switch(config-if)# switchport port-security maximum 2
Switch(config-if)# switchport port-security violation restrict
```

এভাবে, **Sticky Mode** পোর্ট সিকিউরিটির মাধ্যমে আপনাকে স্বয়ংক্রিয়ভাবে সুরক্ষিত MAC অ্যাড্রেস ব্যবস্থাপনা করতে সাহায্য করে।
#### উদাহরণ:
1. পোর্টে একমাত্র একটি MAC অ্যাড্রেস অনুমোদিত হবে:
```bash
Switch(config-if)# switchport port-security maximum 1
Switch(config-if)# switchport port-security violation restrict
```

2. একটি নির্দিষ্ট MAC অ্যাড্রেস কনফিগার করা:
```bash
Switch(config-if)# switchport port-security mac-address 0010.1234.5678
```

3. পোর্ট সিকিউরিটি নিষিদ্ধ করার জন্য:
```bash
Switch(config-if)# switchport port-security violation shutdown
```

#### 3. পোর্ট সিকিউরিটি স্ট্যাটাস চেক করা
আপনি পোর্ট সিকিউরিটির বর্তমান স্ট্যাটাস দেখতে চাইলে নিচের কমান্ড ব্যবহার করতে পারেন:

```bash
Switch# show port-security interface fastEthernet 0/1
```

#### 4. পোর্ট সিকিউরিটি ডিএকটিভেট করা
যদি আপনি পোর্ট সিকিউরিটি নিষ্ক্রিয় করতে চান:

```bash
Switch(config-if)# no switchport port-security
```
```
Switch>
Switch>enable
Switch#config
Switch#configure te
Switch#configure terminal 
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#interface fas
Switch(config)#interface fastEthernet 0/1
Switch(config-if)#switchport port-security
Command rejected: FastEthernet0/1 is a dynamic port.
Switch(config-if)#switchport mode access
Switch(config-if)#switchport port-security
```
এটি মানে যে, আপনি যে ইন্টারফেসে পোর্ট সিকিউরিটি কনফিগার করতে চাচ্ছেন, সেই ইন্টারফেসটি ডাইনামিক পোর্ট হিসেবে কনফিগার করা আছে, যা ভলেটাইল বা পরিবর্তনযোগ্য। Cisco সুইচে কিছু পোর্টে ডাইনামিক পোর্ট কনফিগারেশন থাকতে পারে, এবং এই ধরনের পোর্টে পোর্ট সিকিউরিটি প্রয়োগ করা যায় না।

**সমস্যা সমাধানের জন্য সমাধান:**
- ইন্টারফেসটিকে Access Mode এ স্যুইচ করুন:

 - প্রথমে আপনাকে ইন্টারফেসটিকে access mode এ সেট করতে হবে। এরপর আপনি পোর্ট সিকিউরিটি কনফিগার করতে পারবেন।
   নির্দেশনা:
   ```bash
      Switch(config)#interface FastEthernet0/1
      Switch(config-if)#switchport mode access
   ```
- পোর্ট সিকিউরিটি কনফিগার করুন:
     এখন, আপনি সহজেই পোর্ট সিকিউরিটি কনফিগার করতে পারবেন।
  ```bash
      Switch(config-if)#switchport port-security
  ```
```bash
Switch(config-if)#switchport port-security ?
  aging        Port-security aging commands
  mac-address  Secure mac address
  maximum      Max secure addresses
  violation    Security violation mode
  <cr>
Switch(config-if)#switchport port-security maxi
Switch(config-if)#switchport port-security maximum ?
  <1-132>  Maximum addresses
Switch(config-if)#switchport port-security maximum 1
```
switchport port-security maximum 1 কমান্ডটি ব্যবহার করে আপনি একটি পোর্টে সর্বাধিক 1টি MAC ঠিকানা অনুমোদিত করতে পারেন।

এটির মাধ্যমে আপনি নির্দিষ্ট করে দেন যে, ঐ পোর্টে কেবল 1টি ডিভাইসের MAC ঠিকানা কানেক্ট হতে পারবে। যদি অন্য কোনো MAC ঠিকানা ওই পোর্টে সংযুক্ত হয়, তবে এটি একটি ভায়োলেশন সৃষ্টি করবে, এবং সেটি নির্ধারিত ভায়োলেশন অ্যাকশন অনুযায়ী (যেমন: Shutdown, Protect, বা Restrict) কাজ করবে।

আইপি টেলিফোন এবং পিসির জন্য  ঐ পোর্টে কেবল 2টি ডিভাইসের MAC ঠিকানা কানেক্ট হতে পারবে।
```bash
Switch(config-if)#switchport port-security maximum 2
```
**পোর্ট সিকিউরিটি ভায়োলেশন (Port Security Violation)** হলো সেই ঘটনা যখন কোনো পোর্টে অনুমোদিত MAC ঠিকানা ছাড়া অন্য কোনো ডিভাইস সংযুক্ত হয়। এটি **নেটওয়ার্ক সিকিউরিটি** বাড়ানোর জন্য গুরুত্বপূর্ণ, কারণ এটি অপ্রত্যাশিত বা অবাঞ্ছিত ডিভাইসগুলোকে পোর্টে সংযোগ করতে বাধা দেয়।

- **পোর্ট সিকিউরিটি ভায়োলেশন কিভাবে কাজ করে?**

যখন একটি ডিভাইস একটি পোর্টে সংযুক্ত হয়, সিস্কো সুইচ **MAC ঠিকানা** শনাক্ত করে। যদি ঐ পোর্টের জন্য কনফিগার করা MAC ঠিকানার সাথে নতুন কোনো MAC ঠিকানা মিল না খায়, তবে সেটি **ভায়োলেশন** হিসেবে গণ্য হয়। এবং এরপর স্যুইচ যেই **ভায়োলেশন অ্যাকশন** কনফিগার করা থাকে, তা অনুযায়ী ব্যবস্থা নেয়।

- **পোর্ট সিকিউরিটি ভায়োলেশন অ্যাকশন**

সিস্কো সুইচে পোর্ট সিকিউরিটি ভায়োলেশন ঘটলে তিন ধরনের অ্যাকশন নেয়া যায়:

1. **Protect**:
   - অজানা MAC ঠিকানার প্যাকেট ড্রপ করা হয়, তবে কোনো নোটিফিকেশন পাঠানো হয় না।
   
   কনফিগারেশন:
   ```bash
   switchport port-security violation protect
   ```

2. **Restrict**:
   - অজানা MAC ঠিকানার প্যাকেট ড্রপ করা হয় এবং স্যুইচ একটি নোটিফিকেশন (syslog) পাঠায়।
   
   কনফিগারেশন:
   ```bash
   switchport port-security violation restrict
   ```

3. **Shutdown (ডিফল্ট অপশন)**:
   - পোর্টটি স্বয়ংক্রিয়ভাবে **শাটডাউন** হয়ে যায় এবং কোন প্যাকেট পাস করতে পারে না। এটি সবচেয়ে কড়া নিরাপত্তা।
   
   কনফিগারেশন:
   ```bash
   switchport port-security violation shutdown
   ```

**উদাহরণ কনফিগারেশন:**
ধরা যাক, আপনি যদি FastEthernet0/1 পোর্টে পোর্ট সিকিউরিটি কনফিগার করতে চান এবং ভায়োলেশন ঘটলে পোর্টটি বন্ধ (shutdown) করতে চান, তাহলে কনফিগারেশন হবে:

```bash
Switch(config)#interface FastEthernet0/1
Switch(config-if)#switchport mode access
Switch(config-if)#switchport port-security
Switch(config-if)#switchport port-security maximum 1
Switch(config-if)#switchport port-security violation shutdown
Switch(config-if)#switchport port-security mac-address sticky
```

এখানে:
- **`switchport port-security violation shutdown`**: যদি অন্য কোনো অজানা MAC ঠিকানা পোর্টে যুক্ত হয়, পোর্টটি বন্ধ হয়ে যাবে (shutdown)।
- **`switchport port-security maximum 1`**: একে সীমিত করা হবে ১টি MAC ঠিকানায়।
- **`switchport port-security mac-address sticky`**: যেই MAC ঠিকানা প্রথমে সংযুক্ত হবে, সেগুলো সিস্টেমে অটোমেটিক্যালি সংরক্ষিত হবে।

**পোর্ট সিকিউরিটি ভায়োলেশন চেক করা:**
ভায়োলেশন ঘটে থাকলে তার বিস্তারিত জানার জন্য আপনি নিচের কমান্ডটি ব্যবহার করতে পারেন:
```bash
show port-security
show port-security interface FastEthernet0/1
```

এটি আপনাকে পোর্ট সিকিউরিটির বর্তমান স্ট্যাটাস এবং ভায়োলেশন তথ্য দেখাবে।

### ভায়োলেশন সম্পর্কে সচেতনতা:
- **পোর্ট শাটডাউন** (shutdown) অবস্থায়, পোর্টটি পুনরায় **enable** করতে হবে। এটি করতে:
  ```bash
  Switch(config)#interface FastEthernet0/1
  Switch(config-if)#shutdown
  Switch(config-if)#no shutdown
  ```

এইভাবে আপনি পোর্ট সিকিউরিটি ভায়োলেশন কনফিগার এবং ম্যানেজ করতে পারবেন।

আপনার যদি আরো কোনো প্রশ্ন থাকে বা কোনো অংশে সাহায্য প্রয়োজন হয়, তাহলে আমাকে জানাতে পারেন! 😊
এই স্টেপগুলি ব্যবহার করে আপনি সিস্কো সুইচে পোর্ট সিকিউরিটি কনফিগার করতে পারেন।
