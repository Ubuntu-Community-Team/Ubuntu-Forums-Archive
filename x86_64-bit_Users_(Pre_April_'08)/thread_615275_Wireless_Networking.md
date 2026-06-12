---
title: "Wireless Networking"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghettosamson on 2007-11-16
Good Day. I just installed ubuntu gutsy gibbons, 64bit. Yeah, i got flash player to work. now i wanna connect to my wireless network. How can i do this? I can connect thru mu ethernet adapter, but i need to be able to connect to various networks as this is a laptop and i am a college student that uses wifi a heck of alot. I dual booted this with xp, but i wanna get more familiarity with linux, so if anyone can please help me to connect to the internet or configure my wireless. Gracias everyone. im semi new to linux and i like it.  like the command prompt.

---

### Post by saru411 on 2007-11-17
it would help to post your laptops specs and network card make/model

---

### Post by ghettosamson on 2007-11-17
*-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:67:91:f8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:7d:d2:70
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=10.1.1.54 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
Alright, that is what it says when it type sudo lshw -C network in the command prompt.
I have an inspiron 1501, amd 64x2 turion, 1gb ram, 60gb hd, anything else needed.Also, im running gutsy gibbons

---

### Post by binary_bob on 2007-11-17
Hi ghettosamson,
Have you installed the proprietary driver for the broadcom card?
system>admin>restricted drivers manager.
Enable firmware for Broadcom 43xx family chipset.
when asked; choose the online install, and the preset location.
When this has finished, click on the network connection applet on the top bar and available networks should be shown.
Let me know what you get.

---

### Post by ghettosamson on 2007-11-17
ok, so the firmware was installed and so was the driver. I can now see my available wireless networks. my friend, who has the password for the network is bathing so i will see if it actually connects in a sec. im betting it will. thank you binary bob. i will update on connectivity

---

### Post by ghettosamson on 2007-11-17
alright my man. i am connected sweet. thank you for your help.

---

### Post by binary_bob on 2007-11-17
Glad to be of service ghettosamson.
Welcome to the 64bit world.

---

### Post by saru411 on 2007-11-18
congrats on your first ubuntu install! and welcome to the land of 64 bit processing!

---

