---
title: "Network troubles with HP dv 8051"
date: 2006-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by aalex77 on 2006-02-03
Hello, I'm tring to install ubuntu 5.10 64 bit on my laptop but i've some troubles with my network. During the installation the system can't get DHCP adress even if my dhcp server is working properly. I choos to not configure network and i terminated the installation. I can use only text mode cause I've an ATI card. I tried to configure the network as follow:

```
ifconfig eth0 192.168.2.20/24 broadcasting 255.255.255.0

```
result
```

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:B9:17:BC
          inet addr:192.168.2.20  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0 B)  TX bytes:0 (0 B)
          Interrupt:17 Base address:0x8400

```

```
route add default gw 192.168.2.1
```

result 

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

but it doesn't work!!
I can only ping myself using lo interface...
Anyone can help me!!
Regards

---

### Post by aalex77 on 2006-02-05
No one?!?:rolleyes:

---

