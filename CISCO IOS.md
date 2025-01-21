# কনসোল কেবল এবং রোল-ওভার কেবল

একটি **কনসোল কেবল** হল এমন একটি কেবল যা কম্পিউটার (অথবা টার্মিনাল) এবং একটি নেটওয়ার্ক ডিভাইস যেমন রাউটার বা সুইচের কনসোল পোর্ট সংযোগ করতে ব্যবহৃত হয়। এটি ব্যবহারকারীদের নেটওয়ার্ক ডিভাইসগুলি সরাসরি কনসোল পোর্টের মাধ্যমে পরিচালনা এবং কনফিগার করতে সাহায্য করে, এমনকি ডিভাইসটির যদি কোনও নেটওয়ার্ক সংযোগ না থাকে।

একটি **রোল-ওভার কেবল** হল একটি বিশেষ ধরনের কনসোল কেবল যার একটি অনন্য তারের স্কিম রয়েছে। এই কেবলে, পিনআউটগুলি বিপরীত বা "রোলড ওভার" হয়। উদাহরণস্বরূপ, যেটি একটি প্রান্তে পিন ১-এ সংযুক্ত থাকে, সেটি অন্য প্রান্তে পিন ৮-এ সংযুক্ত থাকে। এটি একটি স্ট্রেইট-থ্রু কেবলের থেকে আলাদা, যেখানে একটি প্রান্তে প্রতিটি পিন অন্য প্রান্তের সমান পিনের সাথে সরাসরি সংযুক্ত থাকে।

এগুলি কীভাবে আলাদা এবং কেন ব্যবহার করা হয় তা এখানে দেওয়া হল:

### **কনসোল কেবল:**
- এটি একটি কম্পিউটার বা টার্মিনালকে একটি নেটওয়ার্ক ডিভাইসের কনসোল পোর্টের সাথে সংযোগ করতে ব্যবহৃত হয়।
- মূলত এমন ডিভাইসগুলির প্রাথমিক কনফিগারেশন বা সমস্যার সমাধানের জন্য ব্যবহৃত হয়, যখন ডিভাইসটির কোনও নেটওয়ার্ক সংযোগ উপলব্ধ থাকে না।
- এর একটি প্রান্তে **DB9** অথবা **RJ-45** কনেক্টর থাকতে পারে, এটি ডিভাইসের কনসোল পোর্টের উপর নির্ভর করে। অন্য প্রান্তটি সাধারণত **USB** অথবা **সিরিয়াল** কনেক্টর থাকে কম্পিউটারের জন্য।

![](Images/cosnole1.jpg)
![](Images/console2.jpg)

### **রোল-ওভার কেবল:**
- এটি একটি বিশেষ ধরনের কনসোল কেবল, যা "সিস্কো কনসোল কেবল" হিসাবেও পরিচিত।
- এর একটি প্রান্তে **RJ-45** কনেক্টর (ডিভাইসের জন্য) এবং অন্য প্রান্তে **DB9** বা **DB25** কনেক্টর (কম্পিউটারের জন্য) থাকে।
- রোল-ওভার কেবলের তারের কনফিগারেশনটি বিশেষ, যেখানে এক প্রান্তে প্রতিটি পিন বিপরীতভাবে অন্য প্রান্তে সংযুক্ত থাকে।


### **সংযোগ সেটআপ:**
- রোল-ওভার কেবলটি ডিভাইসের **কনসোল পোর্ট** (রাউটার বা সুইচ) থেকে কম্পিউটারের **সিরিয়াল পোর্ট** (DB9) এ সংযুক্ত করা হয়।
- যদি কম্পিউটারে সিরিয়াল পোর্ট না থাকে, তবে একটি **USB-টু-সিরিয়াল** অ্যাডাপ্টার ব্যবহার করা যেতে পারে।
- একবার সংযুক্ত হলে, আপনি **PuTTY**, **Tera Term**, অথবা **HyperTerminal** মতো টার্মিনাল সফটওয়্যার ব্যবহার করে ডিভাইসের সাথে সংযোগ স্থাপন এবং কনফিগারেশন শুরু করতে পারেন।

### **রোল-ওভার কেবলের ব্যবহার কেন?**
- রোল-ওভার কেবলের মাধ্যমে নেটওয়ার্ক ডিভাইসগুলির সাথে সরাসরি অ্যাক্সেস পাওয়া যায়, যা কনফিগারেশন এবং সমস্যার সমাধান করতে সহায়ক হয়, যখন অন্য কোনো নেটওয়ার্ক সংযোগ উপলব্ধ থাকে না।
- এগুলি বিশেষভাবে গুরুত্বপূর্ণ **সিস্কো ডিভাইস** এবং অন্যান্য নেটওয়ার্কিং সরঞ্জামগুলির জন্য, যেখানে কনসোল ম্যানেজমেন্ট প্রাথমিক সেটআপ বা রক্ষণাবেক্ষণের জন্য প্রয়োজন।

# Cisco IOS Mode
Cisco IOS (Internetwork Operating System) এ কিছু নির্দিষ্ট মোড রয়েছে, যেগুলির মাধ্যমে আপনি বিভিন্ন স্তরের কার্যক্রম সম্পাদন করতে পারেন। প্রতিটি মোডের নিজস্ব ফিচার এবং প্রিভিলেজ (অধিকার) থাকে। সাধারণত, সিসকো IOS এ মোট চারটি প্রধান মোড রয়েছে, যেগুলি হল:

1. **User EXEC Mode (ইউজার এক্সিকিউট মোড)**
প্রম্পট: > (যেমন: Router1>)
ব্যাখ্যা: এটি সিসকো ডিভাইসে প্রবেশের প্রথম মোড। এই মোডে, আপনি কেবলমাত্র ডিভাইসের স্ট্যাটাস দেখতে পারবেন, এবং কিছু কমান্ড (যেমন ping, traceroute, show কমান্ড) চালাতে পারবেন। আপনি কনফিগারেশন পরিবর্তন বা সিস্টেমের গুরুত্বপূর্ণ কাজ করতে পারবেন না।
কমান্ড উদাহরণ: show ip interface brief, ping, show version
2. **Privileged EXEC Mode (প্রিভিলেজড এক্সিকিউট মোড)**
প্রম্পট: # (যেমন: Router1#)
ব্যাখ্যা: এই মোডে, আপনি আরও উন্নত কমান্ড ব্যবহার করতে পারেন এবং ডিভাইসের কনফিগারেশন পরিবর্তন করতে পারবেন। আপনি ইউজার মোড থেকে enable কমান্ড দিয়ে এই মোডে প্রবেশ করতে পারেন। এটি কনফিগারেশন মোডে যাওয়ার জন্য একটি ধাপের পূর্ববর্তী মোড।
কমান্ড উদাহরণ: show running-config, configure terminal, copy, reload
3. **Global Configuration Mode (গ্লোবাল কনফিগারেশন মোড)**
প্রম্পট: (config) (যেমন: Router1(config)#)
ব্যাখ্যা: এই মোডে, আপনি ডিভাইসের কনফিগারেশন পরিবর্তন করতে পারবেন। আপনি বিভিন্ন কনফিগারেশন অপশন যেমন ইন্টারফেস, রাউটিং প্রোটোকল, এবং অন্যান্য সেটিংস কনফিগার করতে পারেন।
কমান্ড উদাহরণ: interface GigabitEthernet0/1, ip address 192.168.1.1 255.255.255.0, hostname Router2
4. **Interface Configuration Mode (ইন্টারফেস কনফিগারেশন মোড)**
প্রম্পট: (config-if) (যেমন: Router1(config-if)#)
ব্যাখ্যা: এই মোডে, আপনি একক ইন্টারফেসের জন্য কনফিগারেশন পরিবর্তন করতে পারেন। উদাহরণস্বরূপ, আপনি একটি ইন্টারফেসে IP ঠিকানা সেট করতে পারেন অথবা কোনো ইন্টারফেসের স্ট্যাটাস পরিবর্তন করতে পারেন।
কমান্ড উদাহরণ: ip address 192.168.1.1 255.255.255.0, no shutdown

# Console Cable connection to pc
Windows-এ Cisco ডিভাইসের সাথে কনসোল কেবল সংযোগ এবং টার্মিনাল চালানোর জন্য নিম্নলিখিত ধাপগুলি অনুসরণ করতে হবে:

১. কনসোল কেবল সংযোগ করুন:
কনসোল কেবল ( RJ-45 to DB9 বা RJ-45 to USB) ব্যবহার করে আপনার Cisco ডিভাইস (যেমন রাউটার বা সুইচ) এবং কম্পিউটার এর মধ্যে সংযোগ স্থাপন করুন।
যদি আপনি RJ-45 to DB9 কেবল ব্যবহার করেন, তবে DB9 পোর্টটি কম্পিউটারের পুরনো সিরিয়াল পোর্টে (COM port) সংযুক্ত হবে।
যদি আপনি RJ-45 to USB কেবল ব্যবহার করেন, তবে USB পোর্টের মাধ্যমে ডিভাইসটি সংযুক্ত হবে এবং আপনাকে একটি নতুন COM পোর্ট ড্রাইভার ইনস্টল করতে হতে পারে।

২. টার্মিনাল সিস্টেম ইন্সটল করুন:
Windows-এ কনসোল পোর্টের মাধ্যমে Cisco ডিভাইসের সাথে যোগাযোগ করতে PuTTY বা Tera Term মতো টার্মিনাল সফটওয়্যার ব্যবহার করা হয়। এখানে আমরা PuTTY ব্যবহার করার পদ্ধতি দেখাব:

- PuTTY ডাউনলোড করুন:
- PuTTY ইনস্টল করুন:

  **Different Terminal Pogram**
     - Putty (free)
     - Tera Term (free)
     - Hyper Term (free)
     - SecureCRT (paid and best)
     - Minicom  (free for linux,apple)
       
৩. PuTTY দিয়ে সংযোগ স্থাপন:
- PuTTY ওপেন করুন।
- Serial অপশনটি সিলেক্ট করুন।
- Serial line (COM port) এ সঠিক COM পোর্ট নম্বর দিন:
- আপনি Device Manager এ গিয়ে দেখতে পারবেন যে কোন COM পোর্টটি সংযুক্ত হয়েছে। সাধারণত এটি COM1, COM2 ইত্যাদি হতে পারে।
যেমন: COM1, COM2 ইত্যাদি।
- Speed (baud rate) সেট করুন: 9600 (এটি সাধারণত ডিফল্ট থাকে, তবে আপনি আপনার ডিভাইসের কনফিগারেশন চেক করে এটি নিশ্চিত করতে পারেন)।
- Data bits: 8
- Parity: None
- Stop bits: 1
- Flow control: None
- এরপর Open ক্লিক করুন।

৪. Cisco ডিভাইসে লগইন করুন:
আপনি যদি সবকিছু সঠিকভাবে সেটআপ করেন, তবে PuTTY টার্মিনাল উইন্ডোটি খুলবে এবং Cisco ডিভাইসের কনসোল থেকে লগইন প্রম্পট আসবে। আপনি তখন ডিভাইসে লগইন করতে পারবেন।
# Cisco IOS Booting Process
Cisco IOS (Internetwork Operating System) একটি প্রপারাইটরি অপারেটিং সিস্টেম যা Cisco ডিভাইসের (যেমন রাউটার এবং সুইচ) জন্য ব্যবহৃত হয়। Cisco IOS বুটিং প্রক্রিয়া নিম্নলিখিত ধাপগুলোতে সম্পন্ন হয়:

### ১. POST (Power-On Self-Test)
ডিভাইস চালু হলে প্রথমে POST চালু হয়, যা সিস্টেমের হার্ডওয়্যার চেক করে এবং নিশ্চিত করে যে সব কিছু সঠিকভাবে কাজ করছে। যদি কোনো সমস্যা থাকে, তখন লগ রিপোর্ট করা হয় এবং বুট প্রক্রিয়া থেমে যেতে পারে।

### ২. ROM (Read-Only Memory) লোডিং
POST পরীক্ষার পর, ডিভাইসটি ROM থেকে একটি মৌলিক বুটলোডার লোড করে। ROM মূলত একটি ছোট ফার্মওয়্যার যা সিস্টেম চালু করার জন্য প্রাথমিক কোড প্রদান করে।

### ৩. IOS লোডিং
বুটলোডার তারপরে একটি স্থানীয় বা রিমোট সার্ভার থেকে Cisco IOS সিস্টেমের মূল কোডটি লোড করে। এটি সাধারণত Flash মেমরিতে সঞ্চিত থাকে। যদি সিস্টেমটি রিমোট সার্ভার থেকে লোড করতে চায়, তাহলে TFTP বা অন্যান্য প্রোটোকল ব্যবহার করা হতে পারে।

### ৪. স্বয়ংক্রিয় কনফিগারেশন লোডিং
IOS লোড হওয়ার পর, সিস্টেমটি কনফিগারেশন ফাইলটি লোড করতে শুরু করে। কনফিগারেশন ফাইলটি সাধারাণত "startup-config" নামে Flash মেমরিতে থাকে। যদি কোনো কনফিগারেশন ফাইল পাওয়া না যায়, তাহলে ডিভাইসটি "initial configuration dialog" মোডে চলে যেতে পারে, যেখানে ব্যবহারকারীকে কনফিগারেশন সেটআপ করতে বলা হয়।

### ৫. চালু হওয়া এবং লগইন
সব কিছু লোড হওয়ার পর, ডিভাইসটি প্রস্তুত হয় এবং আপনাকে লগইন করার জন্য প্রম্পট দেখায়। এটি সাধারণত একটি CLI (Command Line Interface) যা আপনি কমান্ড দিতে পারেন।

### ৬. রুটিন প্রসেস
সবশেষে, ডিভাইসটি নেটওয়ার্ক কার্যক্রম পরিচালনা করতে শুরু করে এবং আপনি এটি পরিচালনা করতে বিভিন্ন নেটওয়ার্ক কনফিগারেশন পরিবর্তন করতে পারেন।

এভাবেই Cisco IOS বুটিং প্রক্রিয়া সম্পন্ন হয়।

# Hostname configure
Cisco IOS-এ hostname কনফিগার করার জন্য আপনাকে নিম্নলিখিত ধাপগুলি অনুসরণ করতে হবে:

1. **রাউটার বা সুইচে লগইন করুন:**
   - প্রথমে আপনার ডিভাইসে লগইন করুন।
```bash
<swhtch> ?

connect       Open a terminal connection
disable       Turn off privileged commands
disconnect    Disconnect an existing network connection
enable        Turn on privileged commands
exit          Exit from the EXEC
logout        Exit from the EXEC
ping          send echo messages
resume 	      Resume an active network connection
show          Show running system information
telnet        Open a telnet connection
terminal	    Set terminal line parameters
traceroute    Trace route to destination
<switch> 

```
2. **গ্লোবাল কনফিগারেশন মোডে প্রবেশ করুন:**
   - প্রম্পট থেকে `enable` টাইপ করুন এবং Enter চাপুন।
     ```cmd
     enable
     ```
   - তারপর `configure terminal` টাইপ করুন এবং Enter চাপুন।
     ```cmd
     configure terminal 
     ```

```bash
<switch> en
<switch> enable
Switch#
Switch#?
Exec          commands:
clear         Reset functions
clock         Manage the system clock
configure     Enter configuration mode
connect       Open a terminal connection
copy          Copy from one file to another
debug         Debugging functions (see also 'undebug')
delete        Delete a file
dir           List files on a filesystem
disable       Turn off privileged commands
disconnect    Disconnect an existing network connection
enable        Turn on privileged commands
erase         Erase a filesystem
exit          Exit from the EXEC
logout        Exit from the EXEC
more          Display the contents of a file
no            Disable debugging informations
ping          Send echo messages
reload        Halt and perform a cold restart
resume        Resume an active network connection
setup         Run the SETUP command facility
show          Show running system information
ssh           Open a secure shell client connection
telnet        Open a telnet connection
terminal      Set terminal line parameters
traceroute    Trace route to destination
undebug       Disable debugging functions (see also 'debug')
vlan          Configure VLAN parameters
write Write   running configuration to memory, network, or terminal
```
```bash
Switch# configure terminal 
Enter configuration commands, one per line. End with CNTL/Z.
```
3. **hostname কনফিগার করুন:**
   - `hostname` কমান্ড ব্যবহার করে আপনার ডিভাইসের নতুন নাম সেট করুন। উদাহরণস্বরূপ:
     ```cmd
     hostname ciscoswitch1
     ```
```css
Switch(config)# hostname ?
WORD This system's network name

Switch(config)# hostname ciscoswitch1

ciscoswitch1(config)# exit

ciscoswitch1#
%SYS-5-CONFIG_I: Configured from console by console

ciscoswitch1# exit

<ciscoswitch1>

```
4. **কনফিগারেশন সেভ করুন:**
   - কনফিগারেশন সংরক্ষণ করতে `write memory` বা `copy running-config startup-config` কমান্ড ব্যবহার করুন।

এভাবে আপনি Cisco IOS ডিভাইসে hostname কনফিগার করতে পারবেন।

# Negetive Command
Cisco IOS-এ no কমান্ড ব্যবহার করা হয় কোনো কনফিগারেশন অপশনকে নিষ্ক্রিয় (disable) বা মুছে ফেলার জন্য। এর মাধ্যমে আপনি কোনো সেটিংস বা কনফিগারেশন পরিবর্তন করতে পারেন। এই কমান্ডটি সাধারণত কোনো পূর্ববর্তী কনফিগারেশন বা অপশনকে বিপরীত করতে ব্যবহৃত হয়।

no কমান্ডের উদাহরণ:
হোস্টনেম (Hostname) পরিবর্তন: যদি আপনি আগে হোস্টনেম সেট করে থাকেন এবং সেটি মুছে দিতে চান, তাহলে no hostname কমান্ড ব্যবহার করতে পারেন।
```cmd
no hostname
```
```bash
ciscoswitch1(config)# no hostname
switch(config)# exit
switch# exit
switch> 
```
# Console Password
Cisco ডিভাইসে console password কনফিগার করার মাধ্যমে আপনি console পোর্টের মাধ্যমে রাউটার বা সুইচে প্রবেশ করার সময় পাসওয়ার্ড সুরক্ষা যোগ করতে পারেন। এই পাসওয়ার্ড শুধুমাত্র যখন আপনি কনসোল পোর্টের মাধ্যমে ডিভাইসে লগইন করবেন তখনই কার্যকর হবে। নিচে কিভাবে console password কনফিগার করবেন, তা বিস্তারিতভাবে দেওয়া হলো:

### Console Password কনফিগার করার ধাপ:
- **সুইচে কনফিগারেশন মোডে প্রবেশ করুন:**
      Console Password কনফিগার করার ধাপ:
রাউটারের কনফিগারেশন মোডে প্রবেশ করুন:
   ```cmd
      enable
      configure terminal
   ```
```bash
switch> enable
switch# configure terminal
Enter configuration commands, one per line. End with CNTL/Z.

```
- **Console পোর্ট নির্বাচন করুন:**
  ```cmd 
      line console 0
   ```
```bash

switch(config)# line ?
<0-16>      First Line number
  console   Primary terminal line
  vty       Virtual terminal
<0-0>       First Line number

switch(config)#line console ?
<0-0>  First Line number

switch(config)#line console 0
switch(config-line)#
switch(config-line)# ?
Line configuration commands:
   access-class           Filter connections based on an IP access list
  autocommand             Automatically execute an EXEC command
  autocommand-options     Autocommand options
  data-character-bits     Size of characters being handled
  databits                Set number of data bits per character
  default                 Set a command to its defaults
  domain-lookup           Enable domain lookups in show commands
  editing                 Enable command line editing
  escape-character        Change the current line's escape character
  exec                    Configure EXEC
  exec-banner             Enable the display of the EXEC banner
  exec-character-bits     Size of characters to the command exec
  exec-timeout            Set the EXEC timeout
  exit                    Exit from line configuration mode
  flowcontrol             Set the flow control
  full-help               Provide help to unprivileged user
  help                    Description of the interactive help system
  history                 Enable and control the command history function
  international           Enable international 8-bit character support
  ip                      IP options
  ipv6                    IPv6 options
  length                  Set number of lines on a screen
  location                Enter terminal location description
  logging                 Modify message logging facilities
  login                   Enable password checking
  media-type              Console connection media type
  modem                   Configure the Modem Control Lines
  monitor                 Copy debug output to the current terminal line
  motd-banner             Enable the display of the MOTD banner
  no                      Negate a command or set its defaults
  notify                  Inform users of output from concurrent sessions
  padding                 Set padding for a specified output character
  parity                  Set terminal parity
  password                Set a password
  prc                     PRC commands
  privilege               Change privilege level for line
  refuse-message          Define a refuse banner
  rotary                  Add line to a rotary group
  rxspeed                 Set the receive speed
  session-timeout         Set interval for closing connection when there is no
                          input traffic
  special-character-bits  Size of the escape (and other special) characters
  speed                   Set the transmit and receive speeds
  start-character         Define the start character
  stop-character          Define the stop character
  stopbits                Set async line stop bits
  terminal-type           Set the terminal type
  timeout                 Timeouts for the line
  transport               Define transport protocols for line
  txspeed                 Set the transmit speeds
  usb-inactivity-timeout  Inactivity timeout for USB media type
  vacant-message          Define a vacant banner
  width                   Set width of the display terminal

```
- **Console পাসওয়ার্ড সেট করুন:**
   ```cmd
      password cisco
   ```
```bash

Switch(config-line)#password ?
7             Specifies a HIDDEN password will follow
LINE          The UNENCRYPTED (cleartext) line password
0             specified unencrypted password
encryption    Encrypt system passwords

Switch(config-line)# password cisco
Switch(config-line)# end

Switch# show running-config 
Building configuration...

Current configuration : 1096 bytes
!
version 12.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
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
no ip address
shutdown
!
!
line con 0               [console port]
password cisco             
!
line vty 0 4
login
line vty 5 15
login
!
!
end
```
  
- **Login প্রম্পট এনাবল করুন (যাতে পাসওয়ার্ড চাওয়া হয়):**
   ```cmd
      login
   ```
```bash
switch> enable
switch# configure terminal
Enter configuration commands, one per line. End with CNTL/Z.


switch(config)#line console 0

Switch(config-line)#
Switch(config-line)# login
Switch(config-line)# end

switch# exit

Press RETURN to get started!

User Access Verification

Password: 
switch>   enable
Switch#

Switch# show running-config | ?
   begin          Begins unfiltered output of the show command with the first line
                    that contains the regular expression.
  exclude         Displays output lines that do not contain the regular expression.
  include         Displays output lines that contain the regular expression.	
  section         Filter a section of output

Switch# show running-config | begin ?
  LINE  Regular expression.

Switch# show running-config | begin line con
line con 0
password cisco
login
!
line vty 0 4
login
line vty 5 15
login
!
end 
```
- **কনফিগারেশন সেভ করুন:**
```bash
Switch# write memory
```
ব্যাখ্যা:
- **line console 0:** কনসোল পোর্টের জন্য কনফিগারেশন মোডে প্রবেশ করা হয়।
- **password <your_password>:** console পোর্টের জন্য পাসওয়ার্ড নির্ধারণ করা হয়।
- **login:** পাসওয়ার্ড চাওয়ার জন্য login প্রম্পট সক্রিয় করা হয়।
- **write memory:** আপনার কনফিগারেশন পরিবর্তনগুলি সেভ করা হয়।
# Telnet Password
Cisco switch-এ Telnet password কনফিগার করার মাধ্যমে আপনি সুইচের দূরবর্তী (remote) অ্যাক্সেস নিরাপদ করতে পারবেন। Telnet একটি প্রোটোকল যা আপনাকে সুইচ বা রাউটার থেকে দূরবর্তী অবস্থান থেকে কনফিগারেশন করতে দেয়। তবে, Telnet প্রটোকল সিকিউরিটি ক্ষেত্রে তেমন নিরাপদ নয়, তাই সাধারণত SSH ব্যবহারের পরামর্শ দেওয়া হয়। তবে এখানে আমরা Telnet password কনফিগারেশন দেখব।
Switch-এ প্রবেশ করুন:

-**প্রথমে, সুইচের enable মোডে প্রবেশ করুন।**
```bash
Switch> enable
Switch# configure terminal
Switch(config)#
```
- **VTY লাইনের কনফিগারেশন করুন:**
Telnet সেশনের জন্য VTY (Virtual Terminal) লাইনের কনফিগারেশন করতে হবে:
```bash
Switch(config)# line vty 0 15
```
- **Telnet পাসওয়ার্ড সেট করুন:**
এবার আপনি Telnet সেশনের জন্য পাসওয়ার্ড সেট করতে পারেন:
```bash
Switch(config-line)# password <your_password>
উদাহরণস্বরূপ, পাসওয়ার্ড cisco123 সেট করতে:
```bash
Switch(config-line)# password cisco123
Login প্রম্পট সক্রিয় করুন:
```
- **Telnet লগইন প্রম্পট সক্রিয় করার জন্য login কমান্ডটি ব্যবহার করুন:**
```bash
Switch(config-line)# login
```
**Telnet অ্যাক্সেসের জন্য সিসকো সুইচকে Telnet পোর্ট চালু করুন:**

যদি আপনার switch-এ IP address না থাকে, তবে আপনাকে একটি IP address কনফিগার করতে হবে যাতে আপনি Telnet এর মাধ্যমে অ্যাক্সেস করতে পারেন:

```bash
Switch(config)# interface vlan 1
Switch(config-if)# ip address 192.168.1.1 255.255.255.0
Switch(config-if)# no shutdown
```
কনফিগারেশন সেভ করুন:

এখন কনফিগারেশন শেষ হয়ে গেলে, সেগুলি সেভ করুন:
```bash
Switch(config-line)# exit
Switch(config)# exit
Switch# write memory
```

ব্যাখ্যা:
- line vty 0 15: ১৬টি VTY লাইনের কনফিগারেশন নির্বাচন করা হয়েছে (সুইচে ১৬টি ভ্যারচুয়াল টার্মিনাল সেশন অনুমোদিত থাকে)।
- password <your_password>: Telnet পাসওয়ার্ড সেট করা হচ্ছে।
- login: পাসওয়ার্ড প্রম্পট সক্রিয় করা হচ্ছে।
- ip address: সুইচের জন্য একটি IP address কনফিগার করা হচ্ছে যাতে Telnet অ্যাক্সেস করা যায়।

# Enable Password
Cisco switch-এ enable password কনফিগার করার মাধ্যমে আপনি সুইচের privileged EXEC mode (enable mode) নিরাপদ করতে পারবেন। এটি সুইচে enable মোডে প্রবেশ করার সময় পাসওয়ার্ড চাওয়ার ব্যবস্থা করবে। নিচে enable password কনফিগার করার সম্পূর্ণ প্রক্রিয়া বাংলা ভাষায় ব্যাখ্যা করা হলো।

- **Enable Password কনফিগারেশন করার ধাপ:**
Switch-এ প্রবেশ করুন:

প্রথমে, সুইচে privileged EXEC mode (enable mode) এ প্রবেশ করুন:
```bash
Switch> enable
Switch# configure terminal
Enable পাসওয়ার্ড সেট করুন:
```
- **enable password কমান্ড ব্যবহার করে আপনি একটি পাসওয়ার্ড সেট করতে পারবেন:**
```bash
Switch(config)# enable password <your_password>
```
উদাহরণস্বরূপ, যদি আপনি পাসওয়ার্ড হিসেবে cisco123 ব্যবহার করতে চান:

```bash
Switch(config)# enable password cisco123
```
- **Enable Secret Password সেট করুন (এটি আরো সুরক্ষিত):**

enable password সাধারণত সাদাসিধে পাসওয়ার্ড হিসেবে ব্যবহার করা হয়, কিন্তু এটি এনক্রিপ্টেড নয়। তাই সুরক্ষিতভাবে পাসওয়ার্ড রাখতে enable secret ব্যবহার করা ভালো।

```bash
Switch(config)# enable secret <your_secret_password>
```
### enable secrete
```bash
Switch(config)#enable ?
  password  Assign the privileged level password
  secret    Assign the privileged level secret

Switch(config)#enable secret ?
  0      Specifies an UNENCRYPTED password will follow
  5      Specifies an ENCRYPTED secret will follow
  LINE   The UNENCRYPTED (cleartext) 'enable' secret
  level  Set exec level password

Switch(config)#enable secret cisco
Switch(config)#exit
Switch#
%SYS-5-CONFIG_I: Configured from console by console
show r
Switch#show running-config 
Building configuration...

Current configuration : 1154 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
enable password cisco123
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
 --More-- 

```
- **কনফিগারেশন সেভ করুন:**

কনফিগারেশন শেষ হলে, পরিবর্তনগুলো সেভ করে ফেলুন:
```bash
Switch(config)# exit
Switch# write memory
```
পূর্ণ উদাহরণ:
ধরা যাক, আপনি cisco123 পাসওয়ার্ড দিয়ে enable password এবং cisco123secret দিয়ে enable secret password কনফিগার করতে চান। তাহলে পুরো কমান্ডগুলো হবে:

```bash
Switch> enable
Switch# configure terminal
Switch(config)# enable password cisco123
Switch(config)# enable secret cisco123secret
Switch(config)# exit
Switch# write memory
```
ব্যাখ্যা:
- enable password <your_password>: এটি enable মোডে প্রবেশের জন্য একটি পাসওয়ার্ড সেট করবে, কিন্তু এই পাসওয়ার্ডটি প্লেইন টেক্সটে সেভ হবে।
- enable secret <your_secret_password>: এটি enable মোডে প্রবেশের জন্য একটি পাসওয়ার্ড সেট করবে এবং এই পাসওয়ার্ডটি এনক্রিপ্টেড থাকবে, যা অধিক সুরক্ষিত।
- write memory: আপনার কনফিগারেশন সেভ করে ফেলতে এই কমান্ডটি ব্যবহার করা হয়।

# Cisco সুইচের timeout time পরিবর্তন
Cisco সুইচের **timeout time** পরিবর্তন করতে হলে আপনাকে কিছু নির্দিষ্ট পদ্ধতি অনুসরণ করতে হবে। এটি সাধারণত **console session timeout** বা **inactive timeout** হিসেবে পরিচিত, যা সুইচের CLI-তে লগ ইন করার পর কত সময় পর কনসোল সেশনটি স্বয়ংক্রিয়ভাবে বন্ধ হবে তা নিয়ন্ত্রণ করে।

### ১. **Console Timeout পরিবর্তন:**

আপনি যদি **console timeout** পরিবর্তন করতে চান, তাহলে নিচের ধাপগুলো অনুসরণ করতে পারেন:

1. **Global Configuration Mode**-এ প্রবেশ করুন:
   ```bash
   Switch# configure terminal
   ```

2. **Console Line Configuration Mode**-এ প্রবেশ করুন:
   ```bash
   Switch(config)# line con 0
   ```

3. **Timeout পরিবর্তন করুন**:  
   এখানে `exec-timeout` কমান্ড ব্যবহার করা হবে, যার মাধ্যমে আপনি সেশনটির ইনঅ্যাকটিভিটি টাইম আউট সময় সেট করতে পারবেন। 
   উদাহরণস্বরূপ, যদি আপনি টাইম আউট সময় ১০ মিনিট (১০০ মিনিট) সেট করতে চান, তাহলে এই কমান্ড ব্যবহার করুন:
   ```bash
   Switch(config-line)# exec-timeout 10 0
   ```
   এখানে:
   - প্রথম সংখ্যা (১০) মিনিটের জন্য,
   - দ্বিতীয় সংখ্যা (০) সেকেন্ডের জন্য।

4. **কনফিগারেশন সেভ করুন**:
   ```bash
   Switch(config-line)# end
   Switch# write memory
   ```

এটি আপনার কনসোল সেশনটির টাইমআউট সময় ১০ মিনিটে সেট করবে। অর্থাৎ, ১০ মিনিট ইনঅ্যাকটিভ থাকার পর সেশনটি স্বয়ংক্রিয়ভাবে বন্ধ হয়ে যাবে।

### ২. **VTY (Virtual Terminal) Timeout পরিবর্তন:**

যদি আপনি VTY (Telnet বা SSH) সেশনের জন্য টাইমআউট সময় পরিবর্তন করতে চান, তাহলে নিচের পদ্ধতি অনুসরণ করুন:

1. **Global Configuration Mode**-এ প্রবেশ করুন:
   ```bash
   Switch# configure terminal
   ```

2. **VTY Line Configuration Mode**-এ প্রবেশ করুন:
   ```bash
   Switch(config)# line vty 0 4
   ```

3. **Timeout পরিবর্তন করুন**:
   উদাহরণস্বরূপ, আপনি যদি VTY সেশনের জন্য ১৫ মিনিট টাইম আউট সেট করতে চান, তাহলে এই কমান্ডটি ব্যবহার করুন:
   ```bash
   Switch(config-line)# exec-timeout 15 0
   ```

4. **কনফিগারেশন সেভ করুন**:
   ```bash
   Switch(config-line)# end
   Switch# write memory
   ```

### ৩. **Never Timeout পরিবর্তন (Optional)**:

  ```bash
   Switch# configure terminal
   Switch(config)# line con 0
   Switch(config-line)# exec-timeout 0 0
   ```

এভাবে আপনি Cisco সুইচের টাইম আউট সময় পরিবর্তন করতে পারবেন।
# Logging synchronous
**Logging synchronous** কমান্ডটি Cisco সুইচ বা রাউটারের CLI-তে ব্যবহৃত হয় যাতে যখন কোনো লগ মেসেজ আসে, তখন সেটি আপনার কনসোল বা টেলনেট/SSH সেশনের মধ্যে পূর্বের কমান্ড বা আউটপুটের সঙ্গে মিশে না যায়। এটি CLI-তে নতুন লগ মেসেজগুলিকে সঠিকভাবে সিঙ্ক্রোনাইজ করার জন্য ব্যবহৃত হয়, যাতে কমান্ড প্রম্পটটি পরিষ্কারভাবে প্রদর্শিত হয় এবং লগ মেসেজের কারণে আপনার কাজ বিরক্ত না হয়।

### **Logging synchronous কিভাবে ব্যবহার করবেন:**

1. **Global Configuration Mode**-এ প্রবেশ করুন:
   ```bash
   Switch# configure terminal
   ```

2. **Line Configuration Mode**-এ প্রবেশ করুন (যেখানে আপনি কনসোল বা VTY সেশন কনফিগার করবেন):
   - কনসোল সেশন জন্য:
     ```bash
     Switch(config)# line con 0
     ```
   - VTY সেশন (Telnet বা SSH) জন্য:
     ```bash
     Switch(config)# line vty 0 4
     ```

3. **Logging synchronous কমান্ডটি ব্যবহার করুন**:
   ```bash
   Switch(config-line)# logging synchronous
   ```

4. **কনফিগারেশন সেভ করুন**:
   ```bash
   Switch(config-line)# end
   Switch# write memory
   ```

### **বিস্তারিত ব্যাখ্যা:**
- যখন আপনি `logging synchronous` কমান্ডটি কনফিগার করেন, তখন যেকোনো লগ মেসেজ আপনার কমান্ড প্রম্পট বা আপনার শেষ কমান্ডের পরে সঠিকভাবে সিঙ্ক্রোনাইজ হয়ে প্রদর্শিত হবে।
- এর মাধ্যমে আপনি আউটপুটে ফ্লাশিং লগ মেসেজগুলির কারণে কনসোল বা VTY সেশনের মধ্যে বিভ্রান্তিকর বা অপ্রত্যাশিত ফলাফল এড়াতে পারবেন।

এটি বিশেষত তখন ব্যবহারযোগ্য যখন আপনার ডিভাইসটি একটি বড় নেটওয়ার্কে এবং অনেক লগ মেসেজ জেনারেট করছে, যেমন যখন কিছু ত্রুটি বা সতর্কতা বার্তা আসে। `logging synchronous` নিশ্চিত করবে যে লগ মেসেজগুলির কারণে আপনার কাজের ক্ষেত্রে কোনো বিঘ্ন সৃষ্টি হবে না।
# service password-encryption
**`service password-encryption`** কমান্ডটি Cisco সুইচ বা রাউটারে ব্যবহৃত হয় যাতে ডিভাইসের কনফিগারেশন ফাইলে থাকা পাসওয়ার্ডগুলি এনক্রিপ্ট (গোপন) হয়ে যায়। এই কমান্ডটি সক্রিয় করার মাধ্যমে, সুইচের কনফিগারেশন ফাইলে লেখা পাসওয়ার্ডগুলি সরাসরি পাঠযোগ্য না হয়ে একটি এনক্রিপ্টেড ফর্মে সেভ হয়, যা সুরক্ষা বাড়ানোর জন্য গুরুত্বপূর্ণ।

### **`service password-encryption` কমান্ড ব্যবহারের উপকারিতা:**
- **পাসওয়ার্ড নিরাপত্তা:** এটি কনফিগারেশন ফাইলে থাকা পাসওয়ার্ডকে নিরাপদ করে তোলে, যাতে কেউ যদি কনফিগারেশন ফাইলটি পড়তে পারে, তবে পাসওয়ার্ডগুলি পড়া যাবে না।
- **এনক্রিপ্টেড পাসওয়ার্ড:** এনক্রিপ্ট করা পাসওয়ার্ডগুলি আরও সুরক্ষিত, কারণ এগুলি কেবল একটি এনক্রিপশন কী ব্যবহার করে ডিকোড করা যায়।

### **`service password-encryption` কিভাবে ব্যবহার করবেন:**

1. **Global Configuration Mode**-এ প্রবেশ করুন:
   ```bash
   Switch# configure terminal
   ```

2. **`service password-encryption` কমান্ড ব্যবহার করুন**:
   ```bash
   Switch(config)# service password-encryption
   ```

3. **কনফিগারেশন সেভ করুন**:
   ```bash
   Switch(config)# end
   Switch# write memory
   ```

### **উদাহরণ:**
ধরা যাক, আপনি `enable` পাসওয়ার্ড সেট করেছেন:
```bash
Switch(config)# enable secret cisco123
```
```bash
Switch>
Switch>ena
Switch>enable 
Switch#conf
Switch#configure t
Switch#configure terminal 
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#line co
Switch(config)#line console 0
Switch(config-line)#pass
Switch(config-line)#password cisco
Switch(config-line)#login
Switch(config-line)#exit
Switch(config)#line vty
Switch(config)#line vty ?
  <0-15>  First Line number
Switch(config)#line vty 0 15
Switch(config-line)#passw
Switch(config-line)#password cisc
Switch(config-line)#password cisc
Switch(config-line)#login
Switch(config-line)#exit
Switch(config)#
Switch(config)#enable secret cisco123

Switch(config)#end
Switch#
%SYS-5-CONFIG_I: Configured from console by console
show running-config 
Building configuration...

Current configuration : 1204 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname Switch
!
enable secret 5 $1$mERr$5.a6P4JqbNiMX01usIfka/
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 --More-- 

Switch#
%SYS-5-CONFIG_I: Configured from console by console
show running-config | begin  line
line con 0
 password 7 0822455D0A16
 login
!
line vty 0 4
 password 7 0822455D0A
 login
line vty 5 15
 password 7 0822455D0A
 login
!
!
end
```

এখন, যদি আপনি `service password-encryption` কমান্ডটি ব্যবহার করেন, তাহলে `enable secret` পাসওয়ার্ডটি কনফিগারেশন ফাইলে সরাসরি `cisco123` হিসেবে না থেকে, এনক্রিপ্টেড আকারে থাকবে।

### **এনক্রিপ্টেড পাসওয়ার্ডের উদাহরণ:**
যখন আপনি `service password-encryption` ব্যবহার করেন, তখন কনফিগারেশন ফাইলে পাসওয়ার্ডের মান এমন কিছু হতে পারে:
```bash
enable secret 5 $1$S0y7$FqP5Szh79fZCk/ghvWFAow
```

এটি দেখাচ্ছে যে পাসওয়ার্ডটি এনক্রিপ্ট করা হয়েছে এবং আর সরাসরি পড়া সম্ভব নয়।

### **সারাংশ:**
`service password-encryption` কমান্ডটি Cisco সুইচের কনফিগারেশন ফাইলে পাসওয়ার্ডগুলি এনক্রিপ্ট করতে ব্যবহৃত হয়, যা ডিভাইসের নিরাপত্তা উন্নত করতে সহায়ক। service password encryption decrypt এই সাইট থেকে [Cisco Type 7 Password Decrypt]( https://www.firewall.cx/cisco/cisco-routers/cisco-type7-password-crack.html).

Cisco switch-এ VLAN এবং তার IP ঠিকানা সেটআপ করার জন্য আপনাকে কিছু নির্দিষ্ট পদক্ষেপ অনুসরণ করতে হবে। নিচে আমি সেটআপ করার প্রক্রিয়া বাংলায় ব্যাখ্যা করছি।

# VLAN তৈরি ও IP ঠিকানা সেট করা:

1. **Switch-এ লগ ইন করুন:**
   প্রথমে আপনাকে Cisco switch-এ লগ ইন করতে হবে। যদি আপনি console বা SSH ব্যবহার করে সুইচে প্রবেশ করেন, তাহলে আপনাকে প্রম্পট থেকে নিচের মতো কমান্ড ব্যবহার করতে হবে।

2. **Global Configuration Mode এ প্রবেশ করুন:**
   সুইচের প্রিভিলেজড EXEC মোড থেকে (যেখানে প্রম্পট `Switch#` থাকে) টাইপ করুন:
   ```
   configure terminal
   ```
   অথবা সংক্ষেপে:
   ```
   conf t
   ```

3. **VLAN তৈরি করুন:**
   এখন আপনি যে VLAN তৈরি করতে চান, সেটি তৈরি করতে হবে। ধরুন আপনি VLAN 10 তৈরি করতে চান, তাহলে কমান্ড হবে:
   ```
   vlan 10
   ```
   এরপর VLAN 10-এ একটি নাম দিতে চাইলে টাইপ করুন:
   ```
   name VLAN10
   ```

4. **VLAN Interface Configuration Mode এ প্রবেশ করুন:**
   VLAN 10-এর জন্য একটি ভ্ল্যান ইন্টারফেস (SVI - Switched Virtual Interface) কনফিগার করতে হবে যাতে আপনি VLAN এর জন্য IP ঠিকানা সেট করতে পারেন। এজন্য কমান্ড হবে:
   ```
   interface vlan 10
   ```

5. **VLAN Interface-এ IP ঠিকানা সেট করুন:**
   এখন VLAN 10 এর ইন্টারফেসে একটি IP ঠিকানা সেট করতে হবে। উদাহরণস্বরূপ, যদি আপনি VLAN 10-এ IP ঠিকানা 192.168.10.1/24 দিতে চান, তাহলে কমান্ড হবে:
   ```
   ip address 192.168.10.1 255.255.255.0
   ```

6. **VLAN Interface সক্রিয় করুন (No Shutdown):**
   এখন এই VLAN ইন্টারফেসটি সক্রিয় করতে হবে। এটি করতে নিচের কমান্ড ব্যবহার করুন:
   ```
   no shutdown
   ```

7. **কনফিগারেশন সংরক্ষণ করুন:**
   সব কিছু করার পর, কনফিগারেশনটি সংরক্ষণ করতে `end` কমান্ড ব্যবহার করুন এবং তারপর `write memory` বা `copy running-config startup-config` দিয়ে কনফিগারেশন সেভ করুন।

   ```
   end
   write memory
   ```

### সম্পূর্ণ প্রক্রিয়ার উদাহরণ:

```bash
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name VLAN10
Switch(config-vlan)# exit
Switch(config)# interface vlan 10
Switch(config-if)# ip address 192.168.10.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# end
Switch# write memory
```
এখন আপনার VLAN 10-এ IP ঠিকানা 192.168.10.1/24 সেট হয়ে গেছে এবং এটি সক্রিয় আছে।
```bash

Switch>
Switch>
Switch>enable
Switch#show ip interface brief
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual down                  down 
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
Switch#
Switch#show vlan 

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                Fa0/9, Fa0/10, Fa0/11, Fa0/12
                                                Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                Fa0/17, Fa0/18, Fa0/19, Fa0/20
                                                Fa0/21, Fa0/22, Fa0/23, Fa0/24
                                                Gig0/1, Gig0/2
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0
1002 fddi  101002     1500  -      -      -        -    -        0      0   
1003 tr    101003     1500  -      -      -        -    -        0      0   
1004 fdnet 101004     1500  -      -      -        ieee -        0      0   
1005 trnet 101005     1500  -      -      -        ibm  -        0      0   

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------

Remote SPAN VLANs
------------------------------------------------------------------------------

Primary Secondary Type              Ports
------- --------- ----------------- ------------------------------------------

Switch#conf
Switch#configure t
Switch#configure terminal 
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#interface ?
  Ethernet         IEEE 802.3
  FastEthernet     FastEthernet IEEE 802.3
  GigabitEthernet  GigabitEthernet IEEE 802.3z
  Port-channel     Ethernet Channel of interfaces
  Vlan             Catalyst Vlans
  range            interface range command
Switch(config)#interface vla
Switch(config)#interface vlan ?
  <1-4094>  Vlan interface number
Switch(config)#interface vlan 1
Switch(config-if)#?
Interface configuration commands:
  arp          Set arp type (arpa, probe, snap) or timeout
  description  Interface specific description
  exit         Exit from interface configuration mode
  ip           Interface Internet Protocol config commands
  no           Negate a command or set its defaults
  shutdown     Shutdown the selected interface
  standby      HSRP interface configuration commands
Switch(config-if)#ip ?
  address         Set the IP address of an interface
  helper-address  Specify a destination address for UDP broadcasts
Switch(config-if)#ip address ?
  A.B.C.D  IP address
  dhcp     IP Address negotiated via DHCP
Switch(config-if)#ip address 192.168.0.2 ?
  A.B.C.D  IP subnet mask
Switch(config-if)#ip address 192.168.0.2 255.255.255.0
Switch(config-if)#^Z
Switch#
%SYS-5-CONFIG_I: Configured from console by console

Switch#show ip inter
Switch#show ip interface brie
Switch#show ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual down                  down 
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
Vlan1                  192.168.0.2     YES manual administratively down down
Switch#show ru
Switch#show running-config 
Building configuration...

Current configuration : 1103 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
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
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end

Switch#conf
Switch#configure t
Switch#configure terminal 
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#i?
interface  ip  
Switch(config)#?
Configure commands:
  aaa                Authentication, Authorization and Accounting.
  access-list        Add an access list entry
  banner             Define a login banner
  boot               Boot Commands
  cdp                Global CDP configuration subcommands
  clock              Configure time-of-day clock
  crypto             Encryption module
  default            Set a command to its defaults
  do-exec            To run exec commands in config mode
  dot1x              IEEE 802.1X Global Configuration Commands
  enable             Modify enable password parameters
  end                Exit from configure mode
  exit               Exit from configure mode
  hostname           Set system's network name
  interface          Select an interface to configure
  ip                 Global IP configuration subcommands
  line               Configure a terminal line
  lldp               Global LLDP configuration subcommands
  logging            Modify message logging facilities
  mac                MAC configuration
  mls                mls global commands
  monitor            SPAN information and configuration
  no                 Negate a command or set its defaults
  ntp                Configure NTP
  port-channel       EtherChannel configuration
  privilege          Command privilege parameters
  sdm                Switch database management
  service            Modify use of network based services
  snmp-server        Modify SNMP engine parameters
  spanning-tree      Spanning Tree Subsystem
  tacacs-server      Modify TACACS query parameters
  username           Establish User Name Authentication
  vlan               Vlan commands
  vtp                Configure global VTP state
Switch(config)#interfa
Switch(config)#interface vlan 1
Switch(config-if)#no shutdown

Switch(config-if)#
%LINK-5-CHANGED: Interface Vlan1, changed state to up

Switch(config-if)#ip address 192.168.0.2 255.255.255.0^Z
Switch#
%SYS-5-CONFIG_I: Configured from console by console
show ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual down                  down 
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
Vlan1                  192.168.0.2     YES manual up                    down
Switch#

Switch#
%LINK-5-CHANGED: Interface FastEthernet0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up
 
Switch#show ip interface brief 
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
Switch#ping 192.168.0.5

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.0.5, timeout is 2 seconds:
.....
Success rate is 0 percent (0/5)

Switch#ping 192.168.0.5

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.0.5, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/0 ms
```

VLAN switch-এ **default gateway** সেট আপ করার জন্য, আপনাকে VLAN এর জন্য একটি IP ঠিকানা কনফিগার করতে হবে এবং সেই IP ঠিকানাটি সুইচের জন্য ডিফল্ট গেটওয়ে হিসেবে সেট করতে হবে। সাধারণত, সুইচের জন্য ডিফল্ট গেটওয়ে সেট করা হয় যখন সুইচটি বিভিন্ন VLAN-এর মধ্যে রাউটিং বা অন্যান্য নেটওয়ার্কের সাথে যোগাযোগ করবে।

# Steps to Set Default Gateway on a Cisco Switch:

1. **Global Configuration Mode এ প্রবেশ করুন:**
   প্রথমে আপনাকে **Global Configuration Mode**-এ যেতে হবে। সুইচে লগ ইন করে নিচের কমান্ড দিন:
   ```
   enable
   configure terminal
   ```

2. **Default Gateway সেট করুন:**
   সুইচের ডিফল্ট গেটওয়ে সেট করতে, নিচের কমান্ডটি ব্যবহার করুন (ধরি, ডিফল্ট গেটওয়ে 192.168.0.1):
   ```
   ip default-gateway 192.168.0.1
   ```

   এখানে `192.168.0.1` হল সেই রাউটার বা গেটওয়ে ডিভাইসের IP ঠিকানা যা সুইচটি ব্যবহার করবে ডেটা ট্রাফিকের জন্য।

3. **কনফিগারেশন সংরক্ষণ করুন:**
   সব কিছু সম্পন্ন হলে, কনফিগারেশন সংরক্ষণ করতে `end` এবং পরে `write memory` অথবা `copy running-config startup-config` ব্যবহার করুন:
   ```
   end
   write memory
   ```

### Example Configuration:

```bash
Switch> enable
Switch# configure terminal
Switch(config)# ip default-gateway 192.168.0.1
Switch(config)# end
Switch# write memory
```

এখন আপনার সুইচের ডিফল্ট গেটওয়ে সফলভাবে সেট হয়ে গেছে। এই গেটওয়ে IP ঠিকানার মাধ্যমে সুইচটি অন্য নেটওয়ার্ক বা ইন্টারনেটে যোগাযোগ করতে সক্ষম হবে।


