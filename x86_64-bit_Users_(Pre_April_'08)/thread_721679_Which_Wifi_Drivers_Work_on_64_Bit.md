---
title: "Which Wifi Drivers Work on 64 Bit?"
date: 2008-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by czechman86 on 2008-03-11
I am running a macbook before the santa rosa chipset and last night did an install of 64 bit ubuntu. i love the system and it seems to work better with my dual core than 32 bit did. however, i tried to install the ndiswrapper drivers and foolishly, i didnt think that they were only for a 32 bit system. does anyone have recommendations as to which drivers i can/should use. Thank you! Also, as I understand it, to install skype on 64 bit requires some tinkering around. I know its a different question, but if anyone could point me in the direction of a guide to do that, that would be awesome. Thanks again!

---

### Post by czechman86 on 2008-03-11
I found a skype guide, so that question is no longer needed to be answered. thanks again though.

---

### Post by TouchuvGrey on 2008-03-11
Pretty much the same issue here. Running 7.04 Feisty and looking to go
wireless. I have a linksys router and several other windows machines
very happily wireless. HP Pavillion dv8000 laptop, AMD Turion64.

What do i need to do to get wireless working on this machine.

---

### Post by Jouke74 on 2008-03-12
For ndiswrapper wireless 64 bit, you need to use the 64 bit windows XP drivers from your wireless card. 
Since neither of you give any indication on which wireless chipset is in your computer, pointing to a driver will be difficult.

---

### Post by TouchuvGrey on 2008-03-12
> **Jouke74 said:**
> For ndiswrapper wireless 64 bit, you need to use the 64 bit windows XP drivers from your wireless card. 
Since neither of you give any indication on which wireless chipset is in your computer, pointing to a driver will be difficult.


           How do i find out what wireless chipset is in my computer ? And is there
any other information you will need ?

---

### Post by Jouke74 on 2008-03-12
Open a terminal and type the command: **lspci**
That should give a list of your PCI devices. One of them will be your wireless card.

The HP Pavillion dv8000 has a Broadcom wireless system. There are quite some issues with these drivers as I read the "Network" section of this forum. Search for "Broadcom wireless" and you will find both help as well as problems. Anyway, the drivers for XP can be downloaded at HP, but I don't know if those are 64 bit (winXP64). If you installed wireless with Ndiswrapper under 32 bit already, you might have the 64 bit drivers on the same disk you used to get install the 32 bit drivers.
Link HP: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=nl&product=500449&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=nl&product=500449&dlc=en&lang=en)

Otherwise check Broadcom themselves:
Broadcom : [http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php](http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php)

Read before installation the compatibility and installation section of the Ndiswrapper website:
Ndiswrapper: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

---

### Post by TouchuvGrey on 2008-03-12
Hello Jouke:

             Thank you, that seems to be just what i'm looking for. It may be
the weekend before i have a chance to get to it. I will post on the results when i do.

---

### Post by TouchuvGrey on 2008-03-23
I have been trying off and on for the past 10 days to get my
HP laptop working wireless. 64 bit 7.04 Feisty here, i have not upgraded to 
7.10 because of the known issues it has with HP laptops.

    Broadcom BCM4318 chipset in this machine and as i have found
through trying and research that this particulat chipset does not get
along well with 7.04 on an HP when it comes to setting up wireless.

      Does anyone know if the compatibility issue with HP laptops
has been solved in 8.04 ? And has anyone had any experience with
64 bit 8.04 on an HP laptop with the 4318 chipset and setting up
wireless ?

---

