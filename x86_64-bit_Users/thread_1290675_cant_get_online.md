---
title: "cant get online"
date: 2009-10-13
forum: x86 64-bit Users
---

### Post by white-zilla on 2009-10-13
I just put together my new system which has a Intel DP55WB Motherboard which uses a 82578DC Gigabit Ethernet Controller.  At this moment I cannot get online and I haven't a clue where to begin. any help is much appreciated

---

### Post by Databit on 2009-10-13
Can you get a copy of sudo lshw -C network and post it

---

### Post by white-zilla on 2009-10-13
dont mind if i do

```
yt@Lucy:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3160 (3.1 KB)  TX bytes:3160 (3.1 KB)

yt@Lucy:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:ef:12:67:4a:6e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by white-zilla on 2009-10-13
i looked into the 70-persistent-net.rules and there was nothing in there. So i put in 
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="9a:ef:12:67:4a:6e", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

still no luck.  lshw -c network still claims my network is disabled

---

### Post by white-zilla on 2009-10-14
after stumping everyone I work with. My motherboard started giving me 4 beeps. According to intel, this means its timers are dead. in short, its a dead mobo.

---

### Post by Yellow Pasque on 2009-10-14
It looks like you needed a driver. Moot point now, I guess (unless you're getting an identical replacement).

> the Intel DP55KG, the motherboard had worked with Ubuntu 9.04 and its Linux 2.6.28 kernel except for the Gigabit Ethernet adapter was not detected. When upgrading to Ubuntu 9.10 Alpha 5 with the Linux 2.6.31 kernel, the network adapter was now supported.
[http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=4](http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=4)

---

