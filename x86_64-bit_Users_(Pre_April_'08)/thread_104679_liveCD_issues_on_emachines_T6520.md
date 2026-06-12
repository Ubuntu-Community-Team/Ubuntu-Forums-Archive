---
title: "liveCD issues on emachines T6520"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nitin Madan on 2005-12-16
Hello

I am having trouble booting up an emachinesT6520 using an Ubuntu live CD. I believe that the problem is with the IRQ settings of the USB controller and ATI card. I would appreciate any help. 

My eventual goal is to have a dual-boot system with Winxp and Ubuntu. My hardware configuration is listed below.

Thanks in advance.

-----
CPU:  	AMD Athlon™ 64 3400+ Processor (512KB L2 cache, 2.4GHz, 1600MHz FSB)
Operating System: 	Microsoft® Windows® XP Media Center Edition 2005 1
Chipset: 	ATI RS480
Memory: 	1024MB DDR (400MHz)
Expandable to 2GB
Hard Drive: 	200GB 2
Optical Drives: 	16x DVD±RW multi-format double layer
48x CD-ROM
Media Reader: 	8-in-1 Digital Media Manager
Secure Digital (SD), Smart Media, Compact Flash, Micro Drive, Memory Stick, Memory Stick PRO, Multimedia Card, USB 2.0
Video: 	ATI Radeon® Xpress 200 (PCI-Express®)
128MB DDR shared video memory
Sound: 	AC '97 audio, Dolby 5.1 (6-channel)
Modem: 	56K ITU V.92 ready Fax/Modem
Network: 	10/100Mbps Integrated Ethernet LAN
Peripherals: 	Premium plus multimedia keyboard, 2-button wheel mouse, amplified stereo speakers
Dimensions: 	14.125"H x 7.25"W x 16"D
Ports/Other: 	7 USB 2.0 (2 in front; 4 in back; 1 in Media Reader), 1 IEEE 1394 port (in back), 1 Parallel, 2 PS/2 (keyboard and mouse)
-----

---

### Post by Ry Fryar on 2005-12-16
I found a thread about this- do a search for emachines.  My setup is similar to yours, and I had the same problem.  In the thread I found, he got it to install by opening the box to disconnect the card reader from the motherboard.  I guess the idea is to reconnect it after ubuntu has been installed, or to later mess around with the IRQ settings to get it to work in ubuntu.

I disconnected the card reader and that "solved" my first install problem, but met another one- freeze at the detecting hardware to find cdrom drives screen.  You commented on my last post actually, to send info your way if I get answered.

If you get this one figured out, let me know too!  I will do the same.

ry

---

### Post by radiotalent on 2005-12-17
I've got a T6414 (Black Friday Best Buy special) and was able to get the installation to work by removing the cable connecting the card reader to the motherboard.  On my pc they used a pair of black cables near the front bottom edge of the motherboard.  I'm still trying to figure out how to get the card reader to work under Ubuntu, or at a bare minimum, not cause problems and still work under Windows in the dual boot.  Best of luck.

---

### Post by calenti on 2006-11-05
I've got a T6520 as well and having the same issue. Have you tried disabling it in BIOS prior to a LiveCD boot?

Maybe I will give that a try and report back. 

PITA, but the T6520 is a great bargain for what you pay.

---

### Post by mid_night gypsy on 2006-11-26
Hello,
 How are you all. I'm new to ubuntu,but... loving it "no KDE bugs". I have the 
T-6520 and I am running in to the same problems. I too can't install 6.10 u/k
 I also am plauge with the cannot allocate pci of region so and so. I have google 
till I was blue in the face.I read somewhere that the problems we are 
having are fixed ocne we update our bios. But,I can't find any can't use [LEFT][/LEFT]MSI's 
and emachines don't offer any. any light on this would help.thanks
                                                                            Gypsy
emachines T-6520
amd althon64 3400+
msi 7145 (rs480m)
bfg6600 gt oc pci-e

---

### Post by mid_night gypsy on 2006-11-27
Bump

---

### Post by rsambuca on 2006-11-27
I think there may be a problem with some of the ATI chipsets and the live CD.  I got around this easily by adding "ide=nodma" as a boot option prior to booting.

After you boot up, you will then probably want to turn dma back on prior to installing or it will take a couple of hours instead of 15 minutes!

Good Luck!

---

### Post by mid_night gypsy on 2006-11-28
rsambuca,
 THanks for the reply. questions...Are you running 6.10 w/out problems (dvd-cd-rw rom didn't work on my install) 2) 32 or 64 bit?
I am now runing dapper(6.06)32 bit and it for the most part runs fine,But I think it would run alot better dress in edgy.Also I hope
someone has info on the bios update question.
                                            much thanks,gypsy[LEFT][/LEFT]

---

### Post by rsambuca on 2006-11-29
mid_night gypsy,  so far I running both 32 bit and 64 bit Edgy without any problems, although I haven't been using the 64 bit very much yet.  My plan was to try and keep both systems running the same programs as much as possible, and see if there is any performance gain with the 64 bit.  I haven't used the 64 bit as much yet as I have also just installed 64 bit Sabayon linux and I want to test that out.  Right now I am booting XP, Vista (RC2), ubuntu 32bit, ubuntu 64bit, Sabayon 64bit.  Just testing the waters, I guess.

---

