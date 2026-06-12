---
title: "Losing IP Configuration, time and again!"
date: 2009-05-15
forum: x86 64-bit Users
---

### Post by tuffgong on 2009-05-15
Hi I keep losing my ip configuration for eth1, which shares my internet connection with an XBOX360 console. I found this happening many times when i switch off and switch on my XBOX360.

To be precise when i ifconfig the line below just disappears:
inet addr:192.168.0.1 Bcast:192.168.0.255 Mask:255.255.255.0

The rest all appear as below.

eth1 Link encap:Ethernet HWaddr 00:15:f2:c3:53:ff
inet6 addr: fe80::215:f2ff:fec3:53ff/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:49994 errors:0 dropped:0 overruns:0 frame:0
TX packets:82300 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3459424 (3.4 MB) TX bytes:109058549 (109.0 MB)
Interrupt:23 Base address:0xe000


When I do sudo ifconfig eth1 192.168.0.1;, then inet address appears for ifconfig, everything becomes alright again, and the internet is shared properly also.

Please help me out.

---

### Post by Arup on 2009-05-15
Instead of eth1, try giving your connection a name and then see.

---

### Post by cariboo on 2009-05-15
I would check to make sure that the Xbox and the computer are not using the same ip address.

---

### Post by dcstar on 2009-05-16
> **cariboo907 said:**
> I would check to make sure that the Xbox and the computer are not using the same ip address.

Or there is a DHCP server that hands out that address because it does not expect someone to already be using it.

---

