---
title: "What desktop wireless card should I buy?"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by gfunk87 on 2007-09-03
I have the beta version of Gutsy Gibbon, Ubuntu 7.10 and have been trying to get a linksys wmp54g working on my desktop however this has failed and my last post asking for suggestions on how to make it work got no replies so I decided that in the interest of time I should just buy a new wireless card.  My PC is an AMD 64 and i installed the 64 bit version of the operating system, and i am just wondering what desktop wireless card should I buy that will work right out of the box?

i posted it here because i wasn't sure if it being a 64 bit would change what kind of cards would be recomended

thank you,
-Greg

---

### Post by John.Michael.Kane on 2007-09-03
> **gfunk87 said:**
> I have the beta version of Gutsy Gibbon, Ubuntu 7.10 and have been trying to get a linksys wmp54g working on my desktop however this has failed and my last post asking for suggestions on how to make it work got no replies so I decided that in the interest of time I should just buy a new wireless card.  My PC is an AMD 64 and i installed the 64 bit version of the operating system, and i am just wondering what desktop wireless card should I buy that will work right out of the box?

i posted it here because i wasn't sure if it being a 64 bit would change what kind of cards would be recomended

thank you,
-Greg

First let see if there is a way to get your current card working.

Can you post the out put of the following command.
```
lspci
```

---

### Post by gfunk87 on 2007-09-03
output is as follows:

> greg@greg-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
[COLOR="Red"]04:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02[/COLOR])


I'm guessing that what I put in red is what your looking for?

---

### Post by John.Michael.Kane on 2007-09-03
> **gfunk87 said:**
> output is as follows:



I'm guessing that what I put in red is what your looking for?

You card is broadcom base, and should be supported through the use of  use the fw-cutter tool, As a check of the bcm43xx devices list shows your card listed.

Here is version one of the guide for installing. 
[Using Broadcom Wireless in Ubuntu Feisty 7.04]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty")

---

