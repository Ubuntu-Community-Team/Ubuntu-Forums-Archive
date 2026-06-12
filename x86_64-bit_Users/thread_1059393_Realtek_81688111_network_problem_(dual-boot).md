---
title: "Realtek 8168/8111 network problem (dual-boot)"
date: 2009-02-03
forum: x86 64-bit Users
---

### Post by metalclaw on 2009-02-03
Hi,
first of all i'm a noob concerning linux. Now that we got that out of way lets proceed with the problem. My configuration is:

MSI K9A2 Platinum
AMD Athlon X2 6000+
GeForce 9600GT
4GB Transcend DDR2 1066Mhz
HDD-s don't concern you i believe.

Now as stated in title i have problem with network. It's the famous "Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC". I've read most of the posts from people with same problem, but they dont seem to work. Now either i've done something wrong or their solutions just dont work for me. Anyway here is the problem. 

I'm running dual-boot (xp/ubuntu on two different hard drives of course) and in xp network works perfectly when it wont work in ubuntu. Actually when i log in it connects to ADSL router, but no packages are sent or recieved. If i try to reconnect it, i loose connection completely and cant connect any more. I believe i need not mention that its x64 ubuntu in question here. Any help or insight would be greatly appreciated!

and for the end if you need it here is output of 'lspci -v'

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. 
 RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 376c
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	I/O ports at c800 [size=256]
	Memory at fe9ff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8168
	Kernel modules: r8168


if you need anything else please say.

Thank you in advance.

---

### Post by sanderj on 2009-02-04
Can you post the output of 'ifconfig'?
Have you used DHCP for the ethernet-card?
Can you ping the IP-address of the ethernet-interface?
Can you ping the IP-address of the router?

---

### Post by metalclaw on 2009-02-04
Here is ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:1d:92:af:d3:74  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2563 (2.5 KB)  TX bytes:1800 (1.8 KB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15132 (15.1 KB)  TX bytes:15132 (15.1 KB)

i cant ping router, well actually i cant ping anything since connection isn't working. as i said when i try to refresh connection, it disconnects completely and wont connect anymore. and yes i'm using DHCP, router should choose ip for my machine but nothing happens...

---

### Post by sanderj on 2009-02-04
OK, clear: your ethernet hardware is recognized, but there's no IP address on your ethernet interface. 

Can you manually (via the GUI) assign an IP addres and mask and default gateway, which matches with your LAN? So if your gateway is 192.168.0.1, give your ethernet interface 192.168.0.77 with mask 255.255.255.0 with gateway 192.168.0.1.

If so, can your ping your ethernet interface and the gateway?

---

### Post by metalclaw on 2009-02-04
yeah, actually i tried that, but same result. i get connected, but to what i dont know. cant ping anything, it says network unreachable. 

here in windows my ip is 10.0.0.3,
subnet 255.0.0.0 
and routers 10.0.0.2. 

in ubuntu when i try 10.0.0.3 or any other (even 192.168.1.1) it shows its connected, but i still cant ping anything. and one funy thing, when i go back to manual config, subnet is changed to 8 (automatically), and in connection information its clearly stated that its 255.0.0.0

oh and thank you for fast reply!


edit: i've noticed that realtek IRQ is 2300, that seems a bit out of the ordinary since all other components have IRQ up to 30. can that be causing the problem?
and while we're at that i also disabled/enabled lan driver and IRQ changed to 2301. Dont think thats normal, thought i mention it...

---

### Post by metalclaw on 2009-02-05
i installed 8.04 32bit and network is working perfectly. i guess the problem is with 8.10 build...

---

### Post by whansen02 on 2009-02-05
**metalclaw**, I think it might be a fluke that it worked for you ... not that I really know anything about anything, but I haven't heard one single positive review so far other than yours as far as the Realteck 8168/8111 goes.
That's great that you got it working. At least that's one positive feedback about it! ;)
Will

---

