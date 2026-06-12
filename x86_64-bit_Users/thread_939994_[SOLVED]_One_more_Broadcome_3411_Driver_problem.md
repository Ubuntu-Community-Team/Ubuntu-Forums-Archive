---
title: "[SOLVED] One more Broadcome 3411 Driver problem"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by conway.federico on 2008-10-06
I am new to Linux. I just installed ubuntu 64bit on my Presario v6030US.  All works on my new Ubuntu installation except my wireless driver card, bcm4311.  I have scoured the internet for days seeking out every tutorial and thread I could find... and did finally get a driver to complete successfully and for a while allow me to view other wireless networks, but although I was connected to my own... I could not access the internet. Today my system - administration - network won't display any network at all.  

here is my: 

sudo lshw -C network 
  *-network                
       description: Wireless interface 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 01 
       serial: 00:14:a5:b0:af:d4 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g


The driver was created a tutorial I found which described this as a bcm3411 64bit ubuntu driver.. its the only thing that has allowed my wireless card's light to come on.  The original windows driver would install fine, but not allow any connectivity, or show any found networks... 

Help!

---

### Post by conway.federico on 2008-10-07
Glad to see that nobody else had this problem... I fixed it with this great wnetwork manager...  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

