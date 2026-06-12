---
title: "i7 System"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by jeitzen on 2009-04-25
Hello, was wondering if any one has got 9 to install on an i7 system?

---

### Post by beef623 on 2009-04-26
I just installed it on my core i7 965 system tonight. I'm having some trouble with system freezes with Kubuntu 9.04 and OpenSuse 11.1. Hopefully it's nothing major.

[http://ubuntuforums.org/showthread.php?t=1137968](http://ubuntuforums.org/showthread.php?t=1137968)

---

### Post by harveygfl on 2009-04-26
I am experiencing I7 Problems as well..  
I already resolved the 64Bit Adobe Flash Problem by executing a Script that I Found on the Net,  so that Problem is Solved.  FYI.. the Reason why i needed flash was to run Adobe Connect now (Which still did not work because it need an additional plugin from adobe...:lolflag:  Update:  I got Connect Now to Work after Installing Adobe Air in addition to Adobe Flash.. The Adobe Air Instructions are located  here... [http://goblog.vergilhost.info/](http://goblog.vergilhost.info/)

 Here are the Detail of my Configuration...    Operating System:
Ubuntu 9.04 Jaunty Jackalope 64BIT (Already Experimented with Open Solaris and OpenSuse, niether have enough support for the Hardware and Software that I need to use) 

There are some Issues that i need to resolve with Ubuntu: 
1)Sound Card on System Board  I am unable to hear any sound, i tried the instructions on the **  Jaunty 9.04 Sound Solutions**_ [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)_   Without any success.  UPDATE:  I also tried this,  [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) But I am still having Problems...

2)Better Support for MY ATI Video card to work with my Samsung 1080p 50 Inch DLP/LED TV ... I tried to use the ATi Driver, but all i got was Screen Flicker, so I removed it.    UPDATE:   My gut tells me that it may have something to do with the fact the monitors have different aspect ratios,  and different screen resoultions.

If I am unable to resolve my Issues with Ubuntu,  There is a New Fedora release that will soon be released and I May have to give that A try.

-----------------------------------------------------------------------------------------------------
Hardware:
-Intel BOXDX58SO LGA 1366 Intel X58 ATX Intel Motherboard 
-&#65279;Intel Core i7 920 Nehalem 2.66GHz LGA 1366 130W Quad-Core Processor -(used Arctic Silver 5 Thermal Compound during CPU Installation)
-CORSAIR DOMINATOR 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Triple Channel Kit Desktop Memory Model
-POWERCOLOR AX4870 1GBD5-PPH Radeon HD 4870 1GB 256-bit GDDR5 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Video Card 
-Pioneer 20X DVD±R DVD Burner Black SATA Model DVR-216DBK
-Western Digital Caviar Black WD1001FALS 1TB 7200 RPM SATA 3.0Gb/s 3.5" Hard Drive
-SIGMA ATLANTIS ATLANTIS-S Silver Aluminum ATX Mid Tower Computer Case
-Seventeam ST-850PAF 850W ATX 12V V2.2 SLI Ready CrossFire Ready 80 PLUS BRONZE Certified Active PFC Power Supply
-Logitech USB Keyboard and Logitech USB Mouse
-Hitachi Superscan Elite 802Plus  Monitor (22 Inch CRT  Massive size/weight, Would like to Replace with Dell G2410 24" LED Backlit LCD)
-Hauppauge WinTV-Nova-S-Plus Video Device 790 PCI Interface (Recognized By Totem as a Valid Device, I Need to Congigure Frequency Tabe and Re-Aim Dish) 
-Creative Webcam NX USB Webcam (My Logitech Pro Needs additional Support)


Any Ideas would be Helpful

Thanks in advance....
Harvey

---

### Post by malaprohibita on 2009-04-30
Mine's working pretty well (Dell Studio XPS 435).  A few hiccups here and there, like the screen saver freezing my display (ironic, is it not?).  Overall, however, it's the smoothest Ubuntu/Linux experience for me yet.

---

### Post by densou on 2009-04-30
> **harveygfl said:**
> Any Ideas would be Helpful

Best solution, imo: upgrade Jaunty kernel (at your own risk): 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
(advice: wait the .30-rc4 backport, it should be uploaded in a while)

( Read how to on: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) )

W A R N I N G: after doing that, some hardware might not work as before (linux-restricted-modules not included, some modules might be not compatible)


I tried Fedora 11 Preview, I have no doubt again, it's the best distro for Intel crap (aka: Video Cards) owners, imo :rolleyes:

---

### Post by olaboy- on 2009-04-30
Just installed on i7. Works fine and got flash working. Xonar DX isn't liking the prepackaged drivers though.

---

### Post by itendo on 2009-04-30
smooth install, did not have the tracker corruption problem with my i7 like i did on my dell 700m laptop. havent noticed any problems, but havent pushed it yet.

---

### Post by beef623 on 2009-04-30
It looks like my problems were due to my video card. I just replaced it and everything works fine now.

---

