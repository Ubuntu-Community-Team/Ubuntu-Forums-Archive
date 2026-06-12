---
title: "Can only get 1 screen resolution ???"
date: 2006-05-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by peterwor on 2006-05-23
I'm running 5.06 on a MacBook Pro using the Parallels VM software.  I'm also very new to Linux and Ubuntu/Gnome in particular.
I seem to only be able to get 1 screen resolution 1024x768. 
I've always been able to edit the bootloader and get access to other resolutions using another flavor of Linux and KDE (using Yast) but I don't know the Ubunto/Gnome equivelant.
Can someone please help me here with how i go about accessing different screen resolutions?

TIA,
Peter

---

### Post by EuroCity on 2006-05-23
You could try

**sudo dpkg-reconfigure xserver-xorg**

from within Ubuntu, in the Terminal: this makes it possible to add more resolutions (for example, if they don't appear in the GNOME Screen Resolution preference panel).

Or, alternatively, edit the /etc/X11/xorg.conf file with

**sudo gedit /etc/X11/xorg.conf**

always in Ubuntu.

Then, I don't know which resolutions the Parallels program supports: if it is like Virtual PC, for example, resolutions larger than 1024x768 are possible only by selecting the VESA video driver (and this could be done with the above dpkg-reconfigure command); as you are on the x86 platform, VESA should appear among the possible video driver choices, anyway...

---

