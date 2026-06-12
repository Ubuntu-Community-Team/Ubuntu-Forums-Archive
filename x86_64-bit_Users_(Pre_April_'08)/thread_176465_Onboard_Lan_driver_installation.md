---
title: "Onboard Lan driver installation"
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rick069 on 2006-05-14
I have onboard lan, but it isn't detected in the initial installation of ubuntu. So I gathered that I would have to do a manual install of the onboard lan drivers. Taking a look at the readme text on the driver cd (for windoze), I see that the name of the lan thingy is, " IC Plus IP100 10/100 Fast Ethernet Adapter". I believe the chipset is made by Sundance Technologies or something close to it. I went to the site and could not make heads or tails of the install process. Couldn't even find the damn drivers. Anyway, does anyone here know where to find these drivers and how to install them on my ubuntu system?

---

### Post by skylark on 2006-05-15
Apparently there are drivers in the kernel that support it... see [http://forums.fedoraforum.org/showthread.php?t=67809&goto=nextnewest](http://forums.fedoraforum.org/showthread.php?t=67809&goto=nextnewest) for some info. The guy there had the same problems as you and never got them resolved though, so maybe there is something wrong with the kernel drivers. If you can't get it working, maybe file a bug report?

Failing all else, at least PCI 10/100 cards are quite cheap nowadays if you need to buy a new one...

---

### Post by zwilrich on 2006-08-11
There is a driver at
[http://www.icplus.com.tw/driver-pp-IP100A.html](http://www.icplus.com.tw/driver-pp-IP100A.html)
I was able to get this driver to work with Gentoo Linux.  I haven't been able to figure out how to get it to work with Ubuntu yet.

---

### Post by Danieliozzi on 2006-09-17
for me Solution was to compile the Encore Drivers for the "ENL832-TX-ICNT" after making 2 lines modification in the source.
It seems to be a problem with the kernel 2.6.15-26 and the module that comes with the distro.
To be able to do that u need to 

1.Modify sundance_main.c 
  1.a = line 1400 "pci_dma_sync_single" --> "pci_dma_sync_single_for_cpu"
  2.b = line 1653, comment the line 
    Original =  strcpy(info.bus_info, np->pci_dev->slot_name); 
    Correct = /* strcpy(info.bus_info, np->pci_dev->slot_name); */

3.To compile succesfully u need to intstall the packages from your Ubuntu CD from K/X/ubuntu 6.06.1 i386\pool\main" only if u dont have internet conection other way u can do it online with the package manager tool.

4.copy the sundance.ko module that u make to lib/modules/2.6.15-26-386/kernel/drivers/net "Yes overwrite it".

5.Uninstall the module first ."rmmod sundance"

6.Install the module ."insmod sundance" or maybe "insmod  lib/modules/2.6.15-26-386/kernel/drivers/net/sundance.ko"

7.and finnaly bring up the card with "ifconfig eth0 192.168.0.1" or whatever your ethx or ip addres is, or maybe u can use the xwindows system confriguration tool that u have or u like .

I have to say that the main clue for the solution comes from "http://bazar2.conectiva.com.br/pipermail/linux-br/2006-June/040211.html"
but is in brazilian portuguese.

---

