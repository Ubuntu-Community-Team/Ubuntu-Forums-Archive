---
title: "Nvidia 180 drivers Dual 8500GT's issue..."
date: 2009-05-28
forum: x86 64-bit Users
---

### Post by HappyGilmoreX on 2009-05-28
I have been dealing with this nasty issue for the better part of 6 hours now. My issue is every time i install the Nvidia driver, I reboot and keep on getting the CLI login screen. It spiting an error saying that it is unable to identify something in the bios (I am going of memory right now please forgive me). For the life of me I cannot figure this out and i have been looking all over the web for any kind of advice and I am sure if you name I have tried it. Any help would very nice, TIA.

System Setup:
AMD 6000+ 3.0Ghz Dual core
6GB RAM (4GB Corsair) (2GB Kingston)
7 HDD Drive totaling ~1.25TB (Ubuntu being on a Single 320GB HDD)
Dual 512MB 8500GT Nvidia Graphics Cards
4 head setup 3 monitors on side and 1 on the other (2 are cloned for movies)

---

### Post by ShotgunNinja on 2009-05-28
I've been having exactly the same problem. The reason I am posting is because I also have almost exactly the same setup, and I still haven't been able to figure anything out.

My Specs:
Proc: AMD Athlon 64 X2 5400+ 2.7GHz Dual-Core
Mobo: MSI K8N-SLI Pro w/ nForce4 chipset (and onboard SLI, is this the problem?)
GPUs: 2x EVGA nVidia GeForce 8500GTs 256MB, SLI'd through motherboard SLI controller
RAM: 2x  1GB Corsair XMS2 DDR2-800 (PC2-6400), total 2GB
HDD: 1x (i think) WD Caviar 500GB SATA 7200RPM
Monitor: ViewSonic Q19WB 19", max. res. 1440x900, connected via a DVI-to-VGA dongle and a VGA cable into the monitor.

What I did:
 - Installed Ubuntu 9.0.4 x86-64 through Wubi from Windows XP SP3
 - Tried installing nVidia Drivers version 180.51
 - Followed directions, rebooted machine
 - Watched x-server fail to start, then yell that it couldn't find the monitor
 - Tried restoring the settings file I backed up, only to find that it was not created properly.
 - Gave up and went back to suffering on XP.

Is there any way that I can get this to work? Should I somehow try the 32-bit drivers? Should I switch to using the 32-bit Jaunty? Will that even work? Why does nVidia/MSI/x86-64 combo hate Ubuntu so much?

Please help. Thanks.

---

### Post by thewarlock on 2009-05-30
Dual 8800GT  here, tried 64 and 32 bit 9.04 and same deal.

Has to be something about SLI as no problems with the drivers on my laptop or spare machine. (7600 and 6800, but only 1 vid card)

still plonking at it though.

---

### Post by Yellow Pasque on 2009-05-30
The exact error message would be helpful. Attaching the Xorg log might be extremely helpful.

---

### Post by tactx on 2009-05-31
Me too: :(

Nvidia nForce 780i main, C2DX-quad cpu,2x GeForce GTS8800,3x20 displays.

Load driver, reboot, hang on text screen that blacks out. When rebooting is says its shutting down the "Gnome display manager."

tried booting to recovery and "envyng --uninstall-all" to no avail so its re-install x3

It's so frustrating because I had this working beutifully on this rig with 8.04..so until I get help along with these other gents 9.04 is a nogo on my main puter.

---

### Post by tonkabot on 2009-06-08
I have this problem also, with Dual 8800GT's and a AMD X2 64 .  This thread I found here seems to describe a fix - [http://www.overclock.net/linux-unix/507320-ubuntu-9-04-nvidia-drivers.html](http://www.overclock.net/linux-unix/507320-ubuntu-9-04-nvidia-drivers.html)   I haven't tried it yet, but I will soon

---

### Post by dagrump on 2009-06-08
Can't help with the 4 head rig, but sli I can give some clues. 1. sli in the search bar. 2. look for a thread entitled "GUI doesn't load after installing nvidia drivers. 3. check the #8 post.
Now it's all up to you.

---

