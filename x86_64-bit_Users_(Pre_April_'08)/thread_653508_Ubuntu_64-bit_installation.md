---
title: "Ubuntu 64-bit installation"
date: 2007-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anthrax9 on 2007-12-30
i have got a ubuntu 7.10 cd 64-bit from canonical. i have a AMD Athlon X2 processor and ASUS AM2NPV-MX motherboard the OS fails to install.....
the linux kernel loads during installation and the PC boots........
Plzzzz help!!
THnx

---

### Post by Sef on 2007-12-30
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Checks for download errors.)

2) Did you burn the cd at 4x or less?  (Faster can corrupt the burn.)

3) Did you check the cd to make sure it is good?  (Instead of starting, go down the menu to check disk or something similar.)

---

### Post by Anthrax9 on 2007-12-30
I got it shipped from canonical and i did check the cd it is ok!!

---

### Post by Yellow Pasque on 2007-12-30
So where are you getting stuck? Any error messages to help us?

---

### Post by Anthrax9 on 2007-12-30
after the kernel loads during installation some kind of bug appears but the screen doesnt stay long enough to find out what it is and the PC boots

---

### Post by John.Michael.Kane on 2007-12-31
Well if the PC is completing the boot pass the "error", and is leaving you at a blank/black screen you could try pressing ctrl f1 which should bring up a command prompt. after which you could attempt to log-in.

Also what is the full machine spec's eg: video card,mem amount etc?

---

### Post by Griff on 2007-12-31
Go to the ubuntu wiki and see what others have said about similar hardware.  You're problem is most likely not unique.  There are more than a few laptop models that need extra boot parameters to load correctly.

---

### Post by Aethor on 2007-12-31
First thing, at the first installation menu, press the key that allows you to change options (if I remember, F6) and remove "splash" from there. Also when the install finishes and reboots, do the same in the boot menu.

To fix it permanently, remove it from options in /boot/grub/menu.lst

---

### Post by Magzimum on 2007-12-31
When I installed my ubuntu 7.10 on my amd athlon 64 x2 dual core + asus m2n-e sli motherboard, the screen went black (like on powersave mode). It must have something to do with my asus en8500gt silent videocard... 

I could see the initial menu of the installation CD. The screen went black when I did the cd-check to see if the cd is ok, and also when I did the actual installation. 

Ubuntu installed "normally" (only no sound, some alsa problem that I haven't figured out yet)... but I haven't seen anything of the installation, since the screen was black. 

Still when I boot, I have a black screen until the point where I have to login. 

No solutions from me, I'm a newbie... but I thought I'd share the experience.

---

### Post by ~LoKe on 2007-12-31
You'd have to change the way usplash displays, likely the resolution.  I just disabled it completely (I prefer to see the messages).

---

### Post by Anthrax9 on 2008-03-13
Downloaded another copy and installed seems to be there was some kinda problem with the CD Thanx a lot!!!

---

