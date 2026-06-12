---
title: "Wireless Network Problems after Restricted Driver install"
date: 2007-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by idgas15 on 2007-11-26
Hi I'm a new user to Ubuntu. I finally got the OS to install with** noapic**. After installing the Restricted drivers, I cannot connect to the Internet. I right-click on the network icon and there are no available signals. I did a sudo lshw -C network to see if the network card was still disabled and this was the output:

  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:00:00:1a:73:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

Is there anything that you guys suggest that could help me get connected. I'm a college student and I depend on wireless to survive. I hate not being able to use this sweet OS just because of wireless.

Thank you.

---

### Post by hackount on 2007-11-30
i haven't got a wireless connection but what i suggest (reading here and there) it's to install WICD instead of network-manager, it should solve your wireless troubles (remember to uninstall network-manager BEFORE you install wicd)

---

### Post by saru411 on 2007-11-30
[http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390)

a simple point and click option to fix your issues....i would unistall any drives you may have tried beforehand though

---

### Post by Psychoslim on 2007-11-30
I was haven trouble with this as well. Applications>Add/Remove> use your password if promt, then click internet on the left side. At the top type wifi and put a check mark into wifi-radar(install it yes). I figured that out after tinkering for about a hour or so. Hope it helps :)

---

### Post by idgas15 on 2007-12-03
>  Re: Wireless Network Problems after Restricted Driver install
[http://ubuntuforums.org/showthread.p...highlight=1390]](http://ubuntuforums.org/showthread.p...highlight=1390])

a simple point and click option to fix your issues....i would unistall any drives you may have tried beforehand though

Thanks guys for all the help. The information to finally getting it to work I found it on this thread: [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=405990[/COLOR]]("http://ubuntuforums.org/showthread.php?t=405990")  Thanks again... Ubuntu ROCKS!!!

---

