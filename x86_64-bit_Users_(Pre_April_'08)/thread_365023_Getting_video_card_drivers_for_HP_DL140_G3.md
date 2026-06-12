---
title: "Getting video card drivers for HP DL140 G3"
date: 2007-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by miketheman on 2007-02-19
Heya.
I don't know if this is the right forum - it could possibly be more suited for the Hardware forum, so moderator, please move it there if appropriate.

I recently got a couple of HP Proliant [DL140 G3]("http://h20000.www2.hp.com/bizsupport/TechSupport/SupportTaskIndex.jsp?lang=en&cc=us&taskId=120&prodClassId=-1&prodTypeId=15351&prodSeriesId=1842838") servers. (CPU: 1x Intel Xeon 5130 2.0Ghz Dual Core - [ref]("http://www.intel.com/products/processor/xeon/specs.htm"))

The CPU and server tout themselves as 64-bit capable, so naturally I'm giving the AMD64 version of Edgy a shot - I want to run multiple virtual machines on these babies.

The LiveCD boots well, but only will support 640x480 resolution. Installing to the hard drive does not make a difference.

The Device Manager shows the graphic card as an unidentified Matrox card, and digging around the 'net shows that it's probably the "Matrox Millenium G200" (dated back to 1998 or so? :confused:).

[LIST=1]
[*]How can I determine exactly which model the card is?
[*]Assuming it IS the G200, how can I get it to run higher display modes?
[*]If it's not the G200, what is it and where do I find graphic modes for it?
[/LIST]

I _know_ that servers can run headless, via SSH and don't require graphics capabilities, but I still want the option to have a GUI.

Another place I found drivers is: [http://www.matrox.com/graphics/en/corpo/support/drivers/latest/home.cfm]("http://www.matrox.com/graphics/en/corpo/support/drivers/latest/home.cfm")
They have something that says it's a Linux 64-bit driver, but both that and the regular driver will not install, reporting that the version of X that I am using is not supported.

I also found [this]("http://dri.freedesktop.org/wiki/Matrox"), but I don't know how relevant or helpful it is.

Any and all assistance at this point would be greatly appreciated.

---

### Post by RAOF on 2007-02-19
It seems that the driver you want is in the **xserver-xorg-video-mga** package.  Make sure that's installed (it should be by default) and run "sudo dpkg-reconfigure xserver-xorg".

When it asks for the driver, select "mga".  I think that should work.

---

### Post by miketheman on 2007-02-19
I ran that, and sure enough, it was detecting vesa mode, not mga.
But it still didn't help.
I tried using kernel framebuffer mode, and that fried it completely.

So I'm still stuck.

---

### Post by RAOF on 2007-02-19
You manually selected the "mga" driver, rather than the Vesa one?  Hm.  That driver **says** it should work for Millenium cards. :(

---

### Post by weekdaysailor on 2007-03-20
I have the same problems - running Edgy. There's a detailed thread with more possible workarounds [https://launchpad.net/debian/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/debian/+source/xserver-xorg-video-mga/+bug/58721) but none worked for this newbie, and I'm about to slag the whole thing and go to RHE (which HP supports directly)

Anyone else get further?

---

