---
title: "VLANs in Ubuntu 8.10 x86_64"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by NWPerfGuy on 2008-11-16
Hi All,

Anyone having a working VLAN config in the 64 bit version of Ubuntu 8.10?
I have an ASUS P5KC mobo. While trying to isolate the problem I tested
different Ubuntu versions on the same HW. It seems that the 8021q module
works in the following versions:
- 8.0.4.1 i386
- 8.0.4.1 amd64
- 8.10 i386
but it does not work in the 8.10 amd64 version. Based on the packet
captures taken the problem is that the ARP packets are sent out
without the 802.1Q header so they do not find their way to the correct
VLAN in the switch. This breaks any IP communications in other than the
native VLAN.

Regards,

Zoltan

---

### Post by NWPerfGuy on 2008-11-18
After some debugging it turned out that there is a problem with the VLAN tagging hardware acceleration of the atl1 module if compiled for 64 bit.
As a quick fix I simply disabled it in atl1.c by commenting out the following line:

```
netdev->features |= (NETIF_F_HW_VLAN_TX | NETIF_F_HW_VLAN_RX);
```

Regards,

Zoltan

---

### Post by felker2 on 2008-11-18
> **NWPerfGuy said:**
> After some debugging it turned out that there is a problem with the VLAN tagging hardware acceleration of the atl1 module if compiled for 64 bit.
As a quick fix I simply disabled it in atl1.c by commenting out the following line:

```
netdev->features |= (NETIF_F_HW_VLAN_TX | NETIF_F_HW_VLAN_RX);
```

Regards,

Zoltan

Impressive! Have you reported this as a (kernel) bug / patch? Could be useful.

---

### Post by jcliburn on 2008-11-22
> **NWPerfGuy said:**
> After some debugging it turned out that there is a problem with the VLAN tagging hardware acceleration of the atl1 module if compiled for 64 bit.
As a quick fix I simply disabled it in atl1.c by commenting out the following line:

```
netdev->features |= (NETIF_F_HW_VLAN_TX | NETIF_F_HW_VLAN_RX);
```


This bug has been fixed as of kernel version 2.6.27.5.

---

### Post by whistlercanada on 2008-12-17
I might have similar problem. VLAN on eth0 doesn't work even when ifconfig eth0.1 shows everything fine. tcpdump -i eth0.1 doesn't show anything.
However, for testing purpose, if I create VLAN between two similar machines installed with ubuntu 8.10, it works.

If the header issue mentioned here applies to my machines, it would still cause failure for the vlan crossover between two machines, wouldn't it?

I am trying to find a way to solve this VLAN issue. 

```
$ sudo ethtool -i eth0
driver: e1000e
version: 0.3.3.3-k6
firmware-version: 5.6-2
bus-info: 0000:0a:00.0


$ uname -a
Linux s 2.6.27-7-server #1 SMP Tue Nov 4 20:16:57 UTC 2008 x86_64 GNU/Linux


$ lsmod |grep 802
8021q                  32032  0
garp                   17920  1 8021q

```

---

### Post by whistlercanada on 2008-12-24
This problem still haunts me. I didn't try the fix suggested by NWPerfGuy because I am otherwise happy with the CD installation, among other reasons/difficulties. I am using kernel 2.6.27-7 which Jay suggests is free from the problem.

I do not see 8021q tag in the outgoing packets using tcpdump. However I am not sure this is supposed to be visible according to [http://wiki.wireshark.org/CaptureSetup/VLAN]("http://wiki.wireshark.org/CaptureSetup/VLAN") 
> "If you are capturing on the host system where the VLANs are configured, you will probably not see the VLAN tags in the captured frames -- even if you capture on the physical device."

Jay, NWPerfGuy, others, any advice?

---

