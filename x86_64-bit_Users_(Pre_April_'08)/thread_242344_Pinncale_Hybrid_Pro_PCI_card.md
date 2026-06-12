---
title: "Pinncale Hybrid Pro PCI card"
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-08-23
Hi can anyone please help me to get a tv picture in ubuntu from my pinnacle hybrid pro card.

i don't know if it'll even work with linux or how to even try it. the guides don't mention my card so i could do with some help. if it'd just get something in zapper or tvtime i'd be happy. can someone please help thanks.

---

### Post by RAOF on 2006-08-23
Have you checked out [linuxtv.org](linuxtv.org)?  That's where all the TV card drivers are developed, and they've got a Wiki with the status of all the supported cards.  If your card is on there, great.  If it isn't, then...

---

### Post by jonah1980 on 2006-08-24
i've looked but i'm still not sure. the site isn't easy to look through and i don't really know where to look for it!

you can't just type pinnacle in a search and supported cards come up.

this page:
[http://linuxtv.org/wiki/index.php/PCI_devices_DVB-T](http://linuxtv.org/wiki/index.php/PCI_devices_DVB-T)

has a reference to this:
Hybrid DVB-T / Analogue card.
but doesn't tell you anything about it or what to do to see if it works...

please if anyone can help me out, or chech the above page for me and tell me what to do or what it means?

Hybrid DVB-T / Analogue - i mean that's not my card is it? or is it? or is it at least close enough to work??

---

### Post by jonah1980 on 2007-01-06
hi just wondered if anyone had got this card to work yet?

---

### Post by cylon359 on 2007-01-07
Can you post the output from lspci and dmesg ?

---

### Post by jonah1980 on 2007-01-07
ok as requested, lspci:

[quote]jonah@jonah-desktop:~$ lspci
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
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
04:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
04:08.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
04:08.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
04:08.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
04:08.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
04:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
jonah@jonah-desktop:~$

---

### Post by jonah1980 on 2007-01-07
and dmesg attached

---

### Post by jonah1980 on 2007-01-07
though dmesg didn't really fit and attachment size limit is too small... but i think it's got the bit about tvcard in there

---

### Post by cylon359 on 2007-01-07
Yes, it looks like your card is supported as /dev/video0... if you're trying to test with an analogue signal, you could just "sudo apt-get install xawtv", then run xawtv, right click on the image, change TV norm to NTSC (assuming you're in North America), and trying the various "Video source" settings until you get a picture...

If you're trying a digital signal, I've never done that before, so I can't help more, sorry :(

---

### Post by jonah1980 on 2007-01-08
ok i'll try that when i'm home - i'm PAL cos in Europe, it's just an analog signal i want. thanks for helping i'll let you know how i get on...

---

