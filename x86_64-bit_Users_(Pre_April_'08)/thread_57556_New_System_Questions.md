---
title: "New System Questions"
date: 2005-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by PsyberOneZero on 2005-08-16
I've got a new system coming tomorrow and I was wondering if anyone has had luck with simialr hardware and what doesn't work. (Will be using breezy)

ECN KN1 Extreme
    SATA 2
    PCI-E 1x
    PCI-E 16x
  nForce4 Ultra
  Sis 180

Athlon 64 3000+
Nvidia 6200 PCI-E 16x
2 x SATA 2 HD's
2 x SATA DVD/RW

I really want to keep using ubuntu but I love me some new hotness.

---

### Post by rmrf on 2005-08-17
[QUOTE=PsyberOneZero]I've got a new system coming tomorrow and I was wondering if anyone has had luck with simialr hardware and what doesn't work. (Will be using breezy)

ECN KN1 Extreme
    SATA 2
    PCI-E 1x
    PCI-E 16x
  nForce4 Ultra
  Sis 180

Athlon 64 3000+
Nvidia 6200 PCI-E 16x
2 x SATA 2 HD's
2 x SATA DVD/RW

I really want to keep using ubuntu but I love me some new hotness.[/QUOTE]
 The only problem I can see from that system is the fact that it is nF4. The nF4 nic will not work, but most likely it is a dual nic board paired with a marvell which is supported. I have the following system:

DFI nF4 Ultra-D
BFG 6600GT PCI-e
A64 3000+
1GB PC3200
Seagate 120GB SATA HDD
Seagate 60GB ATA133 HDD
Lite-on DVD/CD-RW combo (IDE)
Lite-on DVD-RW (IDE)

It has been working fine for me, except for that pesky nF4 nic. I have gone between the 32 and 64 bit versions of the OS, and I prefer the 32 bit version. Everything works fine in 32 bit mode, and you don't have to have two sets of libraries (one for 32 and one for 64) so that your applications are supported.

Nice looking system, and good luck with the install :cool:

---

### Post by DancingSun on 2005-08-17
Hmm...my NF4-Ultra's NIC worked right after installation.

---

### Post by PsyberOneZero on 2005-08-18
I have no probs with the NForce4 NIC, but  the system cant get past gdm, it loads, the startup sound goes off then it just locks up.

---

### Post by DancingSun on 2005-08-18
Is this with Breezy?  Since you're on a new system, you might as well try Hoary.  This way, you might be able to tell whether it's a hardware problem or some settings on Ubuntu itself.

The biggest difference between my system and yours is that I don't use a SATA drive.  Are you using a RAID configuration?

---

### Post by tseliot on 2005-08-18
[QUOTE=PsyberOneZero]I've got a new system coming tomorrow and I was wondering if anyone has had luck with simialr hardware and what doesn't work. (Will be using breezy)

ECN KN1 Extreme
    SATA 2
    PCI-E 1x
    PCI-E 16x
  nForce4 Ultra
  Sis 180

Athlon 64 3000+
Nvidia 6200 PCI-E 16x
2 x SATA 2 HD's
2 x SATA DVD/RW

I really want to keep using ubuntu but I love me some new hotness.[/QUOTE]

Nvidia 6200 PCI-E 16x works properly only by doing these things (I have the same graphic card)
1) Get to the bios and set the graphic adapter you want to use: make sure the enabled graphic adapter is PCI-E (if there is PCI or AGP your system will be likely to freeze randomly

2) The free "nv" driver will have (at least if you use KDE and/or Mozilla) some graphic corruptions. The only nvidia proprietary drivers that works (without giving you a black screen) are versions no lower than 7664 (7667 and 7676 are better). I advise you to use 7667:

Here is my easy HOWTO to install the drivers:

This is for Ubuntu Hoary
[http://www.ubuntuforums.org/showthread.php?t=57368&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=57368&page=1&pp=10) 

This is for Ubuntu Breezy

[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924) 

3) This might not affect you but if you notice your CPU usage it's about 40% or more (without doing anything) (open System Monitor to check it), try this HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=53094](http://www.ubuntuforums.org/showthread.php?t=53094) 

I hope it helps.

---

### Post by DancingSun on 2005-08-18
Is this the GeForce 6200 with Turbo Cache?  I would think the non-Turbo Cache ones are not that much different from 6600GT, which is what I have.

---

### Post by tseliot on 2005-08-18
[QUOTE=DancingSun]Is this the GeForce 6200 with Turbo Cache?  I would think the non-Turbo Cache ones are not that much different from 6600GT, which is what I have.[/QUOTE]

Mine is with Turbocache.

---

### Post by DancingSun on 2005-08-18
[QUOTE=tseliot]Mine is with Turbocache.[/QUOTE]
Ah, that explains.  If I remember correctly, even on Windows it took a while before the drivers would support Turbo Cache.

---

### Post by krusbjorn on 2005-08-18
I've got an nforce4 chipset and the nvidia 6200 16x PCI-E turbo-cache graphics card. I havent run into any problems whatsoever, neither with the NIC nor the graphics.

---

### Post by DancingSun on 2005-08-18
[QUOTE=krusbjorn]I've got an nforce4 chipset and the nvidia 6200 16x PCI-E turbo-cache graphics card. I havent run into any problems whatsoever, neither with the NIC nor the graphics.[/QUOTE]
Great...gah! You just just complicated things a bit....hmm....maybe it has to do with the an nVidia graphics card not being paired up with an nVidia mobo....

---

### Post by PsyberOneZero on 2005-08-26
I've actually been having alot of troubles with X freezing randomly, I've used the vesa, nv, and nvidia drivers.  It was getting so bad I had to install the dreaded windows in another partiton.  Don't get me wrong I love Ubuntu, but I need it to not freeze

I have the BIOS set to PCI-E, and it's not a heat thing I've got a MASSIVE heatsink/pipe on the CPU and it's only running at 32 C with 100% CPU usage. I will try again and see if maybe a kernel update or two will make it better

---

### Post by Leonidas16a on 2005-09-02
I currently have hoary hedgehog installed and i am running an Evga 6600gt on an epox nf4 sli motherboard. i cannot get the NIC on the motherboard to work, there is no second nic on the motherboard and i am having quite the trouble getting the nforce linux drivers off nvidia's website to run. it keeps saying it needs the source tree or something for the kernel, Oh and please forgive me in advance for my ignorance, i am completely new to linux. just trying to kick my current window's addiction. Thanks alot everyone.

Leonidas

---

