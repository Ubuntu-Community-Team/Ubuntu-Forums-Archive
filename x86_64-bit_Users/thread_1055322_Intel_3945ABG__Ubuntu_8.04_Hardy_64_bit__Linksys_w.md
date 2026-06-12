---
title: "Intel 3945ABG / Ubuntu 8.04 Hardy 64 bit / Linksys with SRX200 (WRT54GX2) Router"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by davidonlaptop on 2009-01-30
Ubuntu Wifi adapter works with other networks/router; router works with Windows Vista but not with Ubuntu, what can be the problem?

My wifi network is listed in Ubuntu GUI, but when clicking on connect I see a loading icon for 2 minutes and it fails without errors. Changing the encryption in the router (WPA, WPA2, WPA/WPA2, WEP, unsecured) does not work either.

I tried using Network Manager and WICD, but I don't know how to try via command line and/or view errors in the log.

Could it be a 64 bit issue?

Help!

Details :

Compaq V3710TX Laptop

dlauzon@Bangkok:~$ lspci -nn |grep Wireless
07:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

dlauzon@Bangkok:~$ lsmod |grep wl
iwl3945               100468  0 
iwlwifi_mac80211      251876  1 iwl3945
cfg80211               17680  1 iwlwifi_mac80211

dlauzon@Bangkok:~$  sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:4a:23:88
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=66.131.243.231 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:9a:c7:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by superjavi on 2009-01-30
I think it is a bug in the 3945 driver. I remember that this card has some issues in Ubuntu until recently (it has been fixed in recent 8.10 updates).
Check launchpad for the bug.

---

### Post by davidonlaptop on 2009-01-30
> **superjavi said:**
> I think it is a bug in the 3945 driver. I remember that this card has some issues in Ubuntu until recently (it has been fixed in recent 8.10 updates).
Check launchpad for the bug.

You're right, [this website]("https://bugs.launchpad.net/ubuntu/+bug/178530") talks about a similar bug. I'll give a go.

But how come I can use the same wifi driver to connect to other wireless?

---

### Post by davidonlaptop on 2009-02-05
SOLVED!

It works with Xubuntu 8.10 - 32bits, with latest kernel 2.6.27-11. The driver for this wireless card can be found in kernels 2.6.24 and up ([source]("http://www.intellinuxwireless.org/?p=iwlwifi")).

Please note that updating my ubuntu hardy to the newest available kernel (2.6.24-23) did not work, perhaps it is an issue with 64bits.

---

