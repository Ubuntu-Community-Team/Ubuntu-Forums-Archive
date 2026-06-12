---
title: "ATI drivers MSI s270 (fgrlx)"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Numeri on 2006-04-13
Summary: I recently installed ubuntu on my freshly bought notebook, and being the linux newb that I am :rolleyes: , I'm having problems with my fgrlx drivers for my ATI graphical card.

Notebook: MSI s270
LCD screen 12" WXGA (1280x800)
Turion AMD 64 something something ~1.8 GhZ
ATI Radeon Xpress 200M

After my installation of the standard ubuntu kernel and rebooting it I recieved an error stating that my X server isn't good configured. dpkg-reconfigure xserver-xorg didn't help me, and after a short search on google I used the command promt to change my device drivers from 'ati' to 'vesa', in xorg.conf.

That did the trick and my laptop's GNOME did start... only to be in 1024x786, a terrible resolution for my widescreen laptop LCD. 

So I found this [How-To]("http://www.ubuntuforums.org/showthread.php?t=24557&pp=10") on how to install the ubuntu ATI drivers.

I followed these instruction to the letter but was unable to start the X server. After changing some more settings in the xorg.conf file I uncommented  Load 'int10'.

Succes! The reso was 1280x800 but it appears there is no openGL.

 fglrxinfo states:
libGL error: drmMap of framebuffer failed
display: :0.0 screen: 0
openGL vendor string: Mesa project
....

I tried various things I found on the internet, skipping the methods that required a recompilation of kernels. I even called in a friend of my that has a lot of experience with gentoo, nothing helped.

Sooooo, I hope someone that reads these forums can help to find a solution for me to use my ATI card to the fullest. I hope someone can help me!

Note: please bare in mind that I'm a total, and complete newbie if it comes to linux. 

[xorg.conf]("http://home.hccnet.nl/m.van.run/xorg.conf")
[Xorg.0.log]("http://home.hccnet.nl/m.van.run/Xorg.0.log")

---

### Post by nolongerlivecd on 2006-04-15
What changes did you make?

---

### Post by Numeri on 2006-04-15
These are the changes I made to the xorg.conf:

Section "Modules":[I]
-copy pasted the extmod subsection
-uncommented the loading of the int10 module[/I]

Section "Device" :
[I]-Driver: 'ati' to 'vesa' to 'fglrx'
-copy pasted all the extra options present from an other xorg.conf.
[/I]
Section "Monitor":
[I]-I manual entered the Refreshrates
[/I]
Section "Screen":
   Subsection: "Display":
[I]- Removed all the Modelines that were of depth < 24
- Manual entered the Option "MonitorLayout" "LVDS, STV"
- Manual entered the Modeline "1280x800" ...etc[/I]

I changed a lot, but only because I changed al those setting it can run in 1280x800.

Sure hope some one knows what to do :)

---

