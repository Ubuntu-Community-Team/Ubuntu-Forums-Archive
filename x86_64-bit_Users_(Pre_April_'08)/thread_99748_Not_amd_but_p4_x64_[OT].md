---
title: "Not amd but p4 x64 [OT]?"
date: 2005-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigfatdad on 2005-12-06
Is this the right place for P4D x64? Don't want be OT.
Just install 5.10 DVD x64 inside a P4D x64 enable and the kernel is ....amd64-xeon, is that right?
At the moment got no xserver (Ati x700) and I'd like to bild my own kernel what are the right steps?

Thanks in advince for your time

Bigfatdad

---

### Post by Robocoastie on 2005-12-06
Yes to all counts. Intel EM64T is just intel's way of saying "we copied AMD". 

I use the Xeon kernel to get smp power of the HT instructions on my P4 and it works fine, no need to recompile kernel.

Having no xserver after install is normal when an ATI card is present at the moment. There's a howto thread in the video card section here with exact steps on installing the ATI driver. In the meantime you can use vi to edit your /etc/X11/xorg.conf file to change the driver to vesa so that you can get to the desktop.

---

### Post by Ronbo on 2005-12-06
Where is that post exactly?  I have a friend who is having the same problem with his ATI PCI-E video card.  I wasn't too sure on how to solve the problem, I use NVIDIA so I was kinda stumped.  I couldn't find the Video Card section.

---

### Post by RAOF on 2005-12-06
As for compiling your own kernel, you shouldn't need to - it's effort which could be more usefully spent playing games, hacking on banshee, etc.

If you really want to (or actually need to), there's this [howto on the wiki]("https://wiki.ubuntu.com/KernelHowto").  You could modify it a bit - I actually like to use "make oldconfig" before "make gconfig" - that copies the configuration from the running kernel, and only asks questions about kernel options that have been changed/added since the running kernel was released.  Oh, and you **need** to build an initrd.

Edit: And here is the [Video and Sound Forum]("http://ubuntuforums.org/forumdisplay.php?f=114").

---

