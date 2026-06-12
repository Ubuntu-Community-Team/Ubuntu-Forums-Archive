---
title: "Please Help Me :Linux Trouble -Connect to Internet Using Lan"
date: 2006-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by bonnei on 2006-03-20
I Dual-Boot WinXP and Ubuntu 5.10 64Bit, 
I connect to Internet using LAN of my system and use the following parameters in WinXP 

IP- 192.168.1.240 
Subnet- 255.255.255.0 
Gateway- 192.168.1.254 
Pri. DNS- 203.145.184.13 
Sec. DNS- 202.56.250.5 

I Used the Same in the Network Options in Ubuntu, I Cant Seem to Connect to Internet. 

I Cant Even Ping the Gateway (but I Can Ping the IP Address) 
It Gives an error that the Host is Unreachable 

When i type "ifconfig eth0" , I Get 



eth0 Link encap:Ethernet HWaddr 00:0B:6A:CF:DE:B7 
inet addr:192.168.1.240 Bcast:192.168.1.255 Mask:255.255.255.0 
inet6 addr: fe80::20b:6aff:fecf:deb7/64 Scope:Link 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:1140 (1.1 KiB) TX bytes:537 (537.0 b) 
Interrupt:17 Base address:0xe400 


Please Help Me to make it work.Thanks a lot.
 
BTW: My  Ethernet Controller is ULi M5263 10/100M Ethernet Controller.

---

### Post by dermotti on 2006-03-20
Could be a DNS issue.


See if you can ping googles ip 64.223.107.99

---

### Post by bonnei on 2006-03-20
[QUOTE=dermotti]Could be a DNS issue.


See if you can ping googles ip 64.223.107.99[/QUOTE]

I can't even ping the gateway.But I can ping my ip.

When I ping the gateway , it gives me an error that The Host is Unreachable.

---

### Post by drl on 2006-03-20
Hi, bonnei.

Read the man page quickly on **route**.  Then run it.  For that I get:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
209.98.96.0     *               255.255.255.0   U     0      0        0 eth1
default         209.98.96.254   0.0.0.0         UG    0      0        0 eth1
```
I'm guessing that you might not have the gateway specified.  I use static IPs, so I needed to configure that in the Network part of System Admin, as I recall.

Another file to look at might be the *interfaces *file, so
```
cat /etc/network/interfaces
```
might provide some information.

If you're using DHCP, I will defer to others who know more about that ... cheers, drl

---

### Post by mishranurag on 2006-03-20
The gateway values are different in WinXP and UBUNTU. Could that be an issue? Look at the bold items below.
[quote=bonnei]
IP- 192.168.1.240 
Subnet- 255.255.255.0 
** Gateway- 192.168.1.254** 
Pri. DNS- 203.145.184.13 
Sec. DNS- 202.56.250.5 

eth0 Link encap:Ethernet HWaddr 00:0B:6A:CF:DE:B7 
inet addr:192.168.1.240 **Bcast:192.168.1.255** Mask:255.255.255.0 
inet6 addr: fe80::20b:6aff:fecf:deb7/64 Scope:Link 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:1140 (1.1 KiB) TX bytes:537 (537.0 b) 
Interrupt:17 Base address:0xe400 


Please Help Me to make it work.Thanks a lot.
 
BTW: My  Ethernet Controller is ULi M5263 10/100M Ethernet Controller.[/quote]

---

### Post by drl on 2006-03-20
Hi.

The reply by mishranurag made me see that indeed you did have a gateway specified.

My ifconfig output looks the same, 255 in place of the 254 in the Bcast field, so I don't think that is the problem.

Let's start really simply: is the ethernet cable plugged in? If so, to where? ... cheers, drl

---

### Post by bonnei on 2006-03-20
How kind you are!Thank you guys to reply my messege.
As drl say, i don't think the gateway setting is the problem,because I use the same setting in the winxp and it works.The cable is good too.I think the ethernet controller driver perhaps isn't perfect.I find it can only recieve data ,but canot transmit data.
drl,I will try your method tonight,and post it .Thanx a lot.

---

### Post by bonnei on 2006-03-21
I have googled it,and find there some guy have the same problem.I think perhaps the driver doesn't work,but I can't find the ULi M5263 driver  for kernel 2.6.x.
Please help me.Thanx a lot!

---

### Post by drl on 2006-03-21
Hi, bonnei.

It is possible that this is one of those cases where the software just hasn't caught up yet.

If you are reasonably sure that it is the driver, you could install the 32-bit version and see if that works.  If this is quite new hardware, you will often see that drivers especially are often the last to arrive.  The 64-bit stuff also will be slow to catch up until there are enough such computers to justify the effort needed to do two versions of software.

Best wishes; keep us posted ... cheers, drl

---

### Post by bonnei on 2006-03-23
HI, drl

I install the ubuntu 6.04 flight 5,all promblem is solute.Now I'm sure it is the driver.
Thanks for your help 

cheers, bonnei

---

### Post by drl on 2006-03-23
Hi, bonnei.

OK, glad to hear it.  Thanks for posting the conclusion of your quest ... cheers, drl

---

### Post by true_friend on 2006-07-26
HI folkx
i have the same problem as bonnie had. i have just installed ubuntu DD LTS. before i also used kubuntu DD LTS. both had same problem i could not connect to internet throuhg my LAN. static ip is used by our network. i gussed my internet communication is blocked by the server why?? i dont know. 
[http://kubuntuforums.net/forums/index.php?topic=6895.0](http://kubuntuforums.net/forums/index.php?topic=6895.0)
here u can see all the discussion made. all command line outputs are fine and now i can also access my server's shared data with out samba in ubuntu 6.06. 
using dual boot with xp. before it i had xp with kubuntu 6.06 now xp with ubuntu 6.06. more all input is alright the DNS, default gateway, subnet mask etc. i gurantee it is alright. but if some buddy asked i will provide u the details. 
plz now help me how i access to internet through cabel net.(intel pro 100 ve netwokr adapter is used by me.) i think it is a driver problem. can any friend help me???
there may a driver i install and my problem solve....
plz plz plz help me.

---

### Post by true_friend on 2006-07-26
clearing that i am using pentium based machine p4 1.8 GHz processor 256 MB memory .... although it is 64 discussion forum but my problem is same so plz do not mind.

---

