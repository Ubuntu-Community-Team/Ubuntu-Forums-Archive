---
title: "wireless network drops out"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by smallmouth sam on 2009-02-02
wierd thing I got a broadcom wireless card in my hp lptop. wireless drops signal will not connect with until I reboot computer. hh for while there only happened after I closed the lid sleep. now happens intermitintly in use??

---

### Post by Crafty Kisses on 2009-02-02
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```

You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
/var/log/messages
```

I also want to see the results of this command:
```
lshw -C network
```
I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

---

### Post by smallmouth sam on 2009-02-02
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth530
       version: a2
       serial: 00:1d:72:47:65:4b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:ee:b5:8e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.0.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11
smallmouth@smallmouth-laptop:~$

---

### Post by smallmouth sam on 2009-02-02
smallmouth@smallmouth-laptop:~$ ifconfig
eth530    Link encap:Ethernet  HWaddr 00:1d:72:47:65:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10300 (10.0 KB)  TX bytes:10300 (10.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:ee:b5:8e  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:feee:b58e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14557 errors:0 dropped:0 overruns:0 frame:4182
          TX packets:11663 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15235289 (14.5 MB)  TX bytes:1945395 (1.8 MB)
          Interrupt:20

---

