---
title: "No network found on Breezy Badger install"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by pgraber on 2005-10-17
Hi,

I've attempted to install Ubuntu 5.10 on my Powerbook Pismo (it supports 5.04, only had problems with wireless ZD1211 "Trendnet TEW-424UB").

The problem is that the install process don't find any network hardware : no eth0, nor wlan0 :( .

dhclient: Internet Software Consortium DHCP Client 2.0p15
[...]
kernel: [  126.905965] eth0: Link is up at 100 Mbps, full-duplex.
kernel: [  126.905992] eth0: Pause is disabled
dhclient: Listening on LPF/eth0/00:65:6a:65:7c
dhclient: Sending on  LPF/eth0/00:65:6a:65:7c
dhclient: Sending on  Socket/fallback/fallback-net
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
dhclient: No DHCPOFFERS received.
dhclient: No working leases in persistent database.

The same thing appears with Ubuntu PPC 5.10 and Kubuntu PPC 5.10.

What can I do ?

Many thanks for your help !

Pierre

---

### Post by pgraber on 2005-10-18
I've found the trick...

It was my router's fault !!!

I've restarted it and all works now !

Pierre

---

