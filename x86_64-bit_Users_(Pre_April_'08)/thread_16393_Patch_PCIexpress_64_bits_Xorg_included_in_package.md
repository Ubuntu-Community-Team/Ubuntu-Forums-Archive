---
title: "Patch PCIexpress 64 bits Xorg included in package ?"
date: 2005-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by my64 on 2005-02-21
Hello,
I have a Asus A8N SLI delux + Geforce 6600XT and PCI express.
Until few days ago, I was using successfully a Warty with the workaround for nvidia corruption indicated [(here)](http://www.ubuntuforums.org/showthread.php?t=15311) .

Gnome and basic applications were running fine, but I had problems with an OpenGL application.

So  I decided to install the real patch around Xorg as indicated in [(here)](http://www.shell.linux.se/xpatrikx/articles/xf86pcibus-bug.html) 

And here came the problems....   it's a long story...

To make it short, I had to ugrade to Hoary, but even with reinstalling the nvidia-* packages (common, kernel, glx) I still have a problem with /etc/fonts.conf file badly corrupted by the manual compilation and installation of X11. Even reinstalling the fontconfig package did not succeed...

So here is the question:  Is the fix for the PCIexp corruption problem [(here)](http://www.nvnews.net/vbulletin/showthread.php?t=42597&page=1&pp=15) included in an hoary package ?

Also, about the nvidia-glx_1.0.6629-1ubuntu7_i386 package. Does it includes the patch for GLX games ?

Last one: If I generate my own kernel AMD-K8 specific,  do I have to use the NVIDIA installer from NVIDIA or is there a nividia-glx source package that Icould use ?

I realize that's may be too many questions in one....

Anyway, It is my first mail on this list (not my last) and  I want to take this opportunity  to thank all Ubuntu contributors for their work. So great.
Ubuntu is now my favorite distro (coming from Mandrake), and it has even replace my windows XP.

---

### Post by my64 on 2005-02-22
Apparently from this thread [http://www.ubuntuforums.org/showthread.php?t=12464&page=3&pp=10](http://www.ubuntuforums.org/showthread.php?t=12464&page=3&pp=10) 
the packaging of PCIexp fix is not yet available.

---

### Post by Vytis on 2005-02-24
[QUOTE=my64]Apparently from this thread [http://www.ubuntuforums.org/showthread.php?t=12464&page=3&pp=10](http://www.ubuntuforums.org/showthread.php?t=12464&page=3&pp=10) 
the packaging of PCIexp fix is not yet available.[/QUOTE]

But gentoo fixed this bug almost a month ago. Why ubuntu is so slow? Are there too little users with 6600gt pci-e?

---

### Post by pwe on 2005-03-01
[QUOTE=Vytis]But gentoo fixed this bug almost a month ago. Why ubuntu is so slow? [/QUOTE]
good question...

---

### Post by Nadir on 2005-03-01
[QUOTE=pwe]good question...[/QUOTE]

Is it this ?

xorg (6.8.2-1) hoary; urgency=low

  * New upstream version (update from 6.8.1.904).
    + Contains AMD64 PCIE BAR fix (closes: Ubuntu#6085).

---

### Post by daniels on 2005-03-01
Yes, that's the one.  And it was unfixed for a while because I was very busy.

---

### Post by my64 on 2005-03-01
[QUOTE=daniels]Yes, that's the one.  And it was unfixed for a while because I was very busy.[/QUOTE]

yessssssssss..... I did an apt-get upgrade    and now my X works fine on my PCI-express 6600 GT video board. I don't need anymore these extensions in xorg.conf

  #Option   "SWCursor"
  #Option   "NoRenderExtension"

and I get a clean screen when I exit X. 

Thanks Daniel!

(By the way, I would be interersted to know  how you proceed to build the xorg packages,especially  if you did use the 'checkinstall' program, how you solved the modules directory location and the font problem)?

But, the bad news is that the glxgears now gives me:
2067 frames in 5.0 seconds = 413.400 FPS
3120 frames in 5.0 seconds = 624.000 FPS
3120 frames in 5.0 seconds = 624.000 FPS
3120 frames in 5.0 seconds = 624.000 FPS

before the update I got around 6000 FPS.
Any idea ?

---

### Post by my64 on 2005-03-01
[QUOTE=But, the bad news is that the glxgears now gives me:
2067 frames in 5.0 seconds = 413.400 FPS
3120 frames in 5.0 seconds = 624.000 FPS
3120 frames in 5.0 seconds = 624.000 FPS
3120 frames in 5.0 seconds = 624.000 FPS

before the update I got around 6000 FPS.
Any idea ?[/QUOTE]

Okay, after desinstalling and reinstalling again nvidia-glx package, the glxgears  worked fine again.

---

