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

### 2. পোর্ট সিকিউরিটির নিয়ম সেট করা
আপনার পোর্ট সিকিউরিটির জন্য কিছু প্যারামিটার কনফিগার করতে হবে, যেমন:

- **ম্যাক অ্যাড্রেস সীমা**: কতটি MAC অ্যাড্রেস পোর্টে অনুমোদিত হবে
- **অ্যাকশন**: যদি কোনো নিষিদ্ধ ডিভাইস পোর্টে সংযুক্ত হয় তাহলে কি হবে (সেটআপ করা যেতে পারে "restrict", "protect", বা "shutdown" অ্যাকশন)
- **MAC অ্যাড্রেস লক করা**: পোর্টে ম্যানুয়ালি নির্দিষ্ট MAC অ্যাড্রেস সেট করা।

### উদাহরণ:
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

### 3. পোর্ট সিকিউরিটি স্ট্যাটাস চেক করা
আপনি পোর্ট সিকিউরিটির বর্তমান স্ট্যাটাস দেখতে চাইলে নিচের কমান্ড ব্যবহার করতে পারেন:

```bash
Switch# show port-security interface fastEthernet 0/1
```

### 4. পোর্ট সিকিউরিটি ডিএকটিভেট করা
যদি আপনি পোর্ট সিকিউরিটি নিষ্ক্রিয় করতে চান:

```bash
Switch(config-if)# no switchport port-security
```

এই স্টেপগুলি ব্যবহার করে আপনি সিস্কো সুইচে পোর্ট সিকিউরিটি কনফিগার করতে পারেন।
