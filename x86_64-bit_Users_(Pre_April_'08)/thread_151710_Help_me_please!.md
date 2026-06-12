---
title: "Help me please!"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by phelixnyc on 2006-03-28
I am new to Linux. I heard some good things about it, so Ive decided to try it. I am having problems installing Ubuntu dapper & 5.10. Ive tried both and so far nothing. Ive downloaded dapper live 64, burned image using Nero and tried to boot my pc, and it stalls on Ubuntu splash no key I press works and Ive tried to wait it out but nothing. When I boot or try to install 5.10 it gets past language choice keyborad then the loader stalls and ask me to check integrity of disc, i do its fine. I also used md5sum everthing checks out okay.Can someone please help 
I so looking to use Ubuntu but so far Im disappointed. Specs below     

AMD 3700+ cpu
ASRock 939 Dual-Sata2 mobo
ATI Radeon x700pro 256 agp
Seagate Ultra ATA/100 120gb hdd
PQI 266DDR dual channel memory 1gb
Windows XP Home Edition SP2

---

### Post by John Jason Jordan on 2006-03-28
[QUOTE=phelixnyc]
AMD 3700+ cpu
ASRock 939 Dual-Sata2 mobo
ATI Radeon x700pro 256 agp
Seagate Ultra ATA/100 120gb hdd
PQI 266DDR dual channel memory 1gb
Windows XP Home Edition SP2[/QUOTE]
First, nothing in those specs sounds as though it would be a problem, with the possible exception of the video. ATI and Linux are not good buds. Nevertheless, it should have booted to at least a standard display.

Troubleshooting is a process of eliminating possibilities. If you have another computer around, try the live CD you made with the other computer. If it works, you know there is nothing wrong with the live CD, therefore the problem must be something in your PC. Also try a different live CD. Try Knoppix, for example. And there are other distros which have live CDs available. Try them all. Also, you can order a free live and install CD set from Ubuntu. It will take a while to arrive, but at least it's free, and you'll know for sure that there is nothing wrong with the CD.

Also double-check to see if you burned the 32-bit or the 64-bit version. The 32-bit will run on either 32-bit or 64-bit CPUs, but the 64-bit version will work only on a 64-bit system.

If the problem turns out to be something in your computer, there are some setup options that you can use to eliminate various things -- sort of like "safe mode" in Windows, where you tell the boot process not to use certain features. I'm fairly new to Linux myself and don't know all of them, but they are documented somewhere on Uuntu's site.

---

### Post by Sidk on 2006-03-28
I'm no expert by any means but it sounds like x is crashing. Try pressing ctrl+alt+backspace and see if it will put you back in a  command window. Then from command give it a

sudo nano /etc/X11/xorg.conf      note that X11 is in caps

once into the file search for the line that has 'ati' and change it to read 'vesa'. save the file and then from command give it a

startx

If this works then everytime you fire up the live disk you will have to change it. You may be able to use a windows .iso editor and make the change permanent but I've never tried.

Worth a shot.

---

### Post by phelixnyc on 2006-03-28
Ive tried Knoppix and it seems that theres a prob with a root file and it wont boot past that. Iam going to try to use Dapper on another pc to see if it works asap.

---

### Post by Sidk on 2006-03-28
Have you tried to pass the command 

boot vga=771

at startup?

---

