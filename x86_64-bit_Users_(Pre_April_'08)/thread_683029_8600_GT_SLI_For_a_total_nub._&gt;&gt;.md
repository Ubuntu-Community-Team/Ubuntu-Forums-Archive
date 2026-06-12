---
title: "8600 GT SLI For a total nub. &gt;&gt;"
date: 2008-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kurosu on 2008-01-30
I know. Before I get flamed, I could've searched. Well, I did. Half of my search results are basically 1 or 2 replies, and the others are Mediocre to highly technical responses that I get lost through because parts are being left out.

System:
ASUS M2N-SLI Deluxe AM2 Motherboard
AMD AthlonX2 5000+
4 Gigs of Ram
2x WD 320 GB HDs sata
2x XFX Nvidia 8600 GTs in SLI mode, one monitor, DVI.


I've installed 7.10 AMD64 version through the alternative CD. I originally tried the LiveCD, but no result.

I want to learn Linux, but I can't learn off of incomplete topics.

Can someone please help me in order to reach the Xserver, As of right now, I am rather fluent in the recovery mode trying things that aren't working. 

So far, as of what I understand, neither the nvidia-glx or the nvidia-glx-new contain 8600 drivers. However, I think Envy does. How can install envy ENTIRELY from command line without the use of gui(obviously because I can't use gui at all.)

Or, how can I even GET to GUI? Any help would be wonderful.

Thanks.

---

### Post by hajk on 2008-01-31
Hmmm, hard to tell what exactly your problem is. I'm running a single GeForce 8600GT myself, and the only problem I have is with the boot splash screen -- a known problem with usplash. X came up with the default "nv" driver; later I installed the "nvidia" driver through the Restricted Driver manager, and  it works fine as well. Are you saying that you can't even start X with the default "nv" video driver?

---

### Post by peter120980 on 2008-01-31
I had the same problem, i am also running 2 8600 GT in sli mode.  I tried everything i could think of to get it to work.  In the end the problem seemed to be in the xorg.conf file.

Ubuntu picked up my PCI-E bus as 2:0:0:0 when in fact mine is actually 7:0:0:0.  As soon as i changed this I could boot into xserver with no problems at all.

Not sure if this will help you but good luck, you can normally see what bus id you pci-e is from the post screen when you start the computer.

Hope this helps.

Ill post my xorg.conf file when i get home from work if you dont manage to get it sorted before then

---

### Post by Kurosu on 2008-02-01
Yeah, my Bus ID was set to 2:0:0, but it was actually 6:0:0. Thanks for your help, everyone.

---

