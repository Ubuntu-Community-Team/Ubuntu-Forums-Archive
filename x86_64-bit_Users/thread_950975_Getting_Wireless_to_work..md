---
title: "Getting Wireless to work."
date: 2008-10-17
forum: x86 64-bit Users
---

### Post by MXIIA on 2008-10-17
Ok, so my story starts, I had Ubuntu 8.04 installed since the day it came out, which was the day I switched to Ubuntu, from Vista. Wireless worked out of the box and I never had any problems with it. Until recently, when a packaging error caused ubuntu-desktop and a bunch of other important packages to be deleted, causing me to have to reinstall Ubuntu. I reinstalled Ubuntu 8.04 from the Live CD. On the Live CD wireless worked fine. On the day of reinstallation wireless worked fine. 

Now, the wireless does not work at all. I cannot edit it through network admin, the eth0 interface does not exist, nm-editor does not allow me to add a network. 
I've tried /etc/network/intefaces , /etc/init.d/networking restart   and ifconfig eth0 up none work

Edit: I realize I should have posted this in the wireless forum, if a mod or admin could move it and delete this comment that would be great :)

---

### Post by Yellow Pasque on 2008-10-17
The interface for wireless connections is usually named wlan0 (or ath0). Please post output of:
```
sudo lshw -C network
cat /etc/network/interfaces
iwconfig
```

---

### Post by MXIIA on 2008-10-17
Ok, the output was
 ```

mxiia@MXIIA-Desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:18:f3:10:9e:10
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
mxiia@MXIIA-Desktop:~$ cat /etc/network/interfaces
mxiia@MXIIA-Desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



```
Also, I remember that it was an eth0 setup last time, but it may have been ath0, I have slight dyslexia and could have confused them, but I did try the same set of commands for ath0 knowing that it was possible that I had gone dyslexic.

I noticed that the /etc/network/interfaces files is blank, although I remember it saying 
```
auto eth0
iface eth0 inet dhcp
``` 
yesterday, and the wireless internet hasn't worked for a few days.

---

### Post by Yellow Pasque on 2008-10-17
You don't have a driver loaded for your wireless card. If you don't know how to fix this, boot the livecd and run the lshw command to see what module Ubuntu uses for your wifi.

---

### Post by MXIIA on 2008-10-17
Ok, I will run the liveCD and do what you said. But why would the Wifi work the day after installation and stop working the next day?

---

### Post by Yellow Pasque on 2008-10-17
> **MXIIA said:**
> Ok, I will run the liveCD and do what you said. But why would the Wifi work the day after installation and stop working the next day?
Did you install updates (especially a kernel update)? That can cause driver issues.

---

### Post by MXIIA on 2008-10-17
Well it started installing updates, and when it hit about half it stopped, I assumed it was my router but I guess it was the drivers.



I ran the LiveCD and got this output from lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:18:f3:10:9e:10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: wifi0
       version: 01
       serial: 00:18:e7:29:b1:c3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


```

---

### Post by Yellow Pasque on 2008-10-17
Try to load that module manually (on your installed system):
```
sudo modprobe ath_pci
```
Does it work?

---

