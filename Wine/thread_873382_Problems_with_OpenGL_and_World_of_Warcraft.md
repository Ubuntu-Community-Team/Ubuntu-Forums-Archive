---
title: "Problems with OpenGL and World of Warcraft"
date: 2008-07-28
forum: Wine
---

### Post by Deskull on 2008-07-28
[System Specifications]

-Computer-
Processor		: Mobile AMD Sempron(tm) Processor 3600+
Memory		: 449MB (222MB used)
Operating System		: Ubuntu 8.04.1
User Name		: deskull (Cory Sammons)
Date/Time		: Mon 28 Jul 2008 10:26:06 PM CDT
-Display-
Resolution		: 1024x768 pixels
OpenGL Renderer		: ATI Radeon Xpress Series
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA ATI SB
-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Power Button (FF)
 Power Button (CM)
 Sleep Button (CM)
 Lid Switch
 Video Bus
 Microsoft Microsoft Optical Mouse with Tilt Wheel
 PC Speaker
 SynPS/2 Synaptics TouchPad
 b43-phy0
-Printers (CUPS)-
PDF
-IDE Disks-
-SCSI Disks-
ATA FUJITSU MHY2060B

**I am trying to improve my framerate in world of warcraft. I have a one small problem though. The game starts flawless under wine. I am using this as the command line /home/deskull/.wine/Program Files/World of Warcraft/Launcher.exe -OpenGL. The problem is when I start the game completely there is blacked out spots all over the place I can login and get into the game but, I cannot see my character other npcs other characters. The environment seems okay. If anyone has found a fix for this please post back here.**

---

### Post by uberlube on 2008-07-28
The problem is that you are using an ATI Radeon Express series graphics card. They flat out suck and are not very well supported in Linux. I recommend spending $140.00 for a good nvidia card and be able to enjoy the aesthetic Linux experience to the full.

---

### Post by uberlube on 2008-07-28
And make sure that GLX is installed in the repositories.

---

### Post by Deskull on 2008-07-28
That was a quick reply. Thanks, but, I would buy a graphics card for my pc but this is a laptop I am playing on a Dell 1501 to be exact. I will try the GLX thing hopefully it works.

---

### Post by uberlube on 2008-07-28
Make sure that you restart you computer after you install it to make sure it initializes.

---

### Post by thisismalhotra on 2008-07-29
You need to follow thse links

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

Specially this:-

[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

---

