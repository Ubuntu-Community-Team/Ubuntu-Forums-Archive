---
title: "Blank desktop, Ray Woodcock?"
date: 2009-04-21
forum: x86 64-bit Users
---

### Post by bryceowen on 2009-04-21
O.K., So I booted my x64 ubuntu install and instead of the normal gnome desktop, all I get is the ubuntu wallpaper and a link on the desktop to:

[http://raywoodcockslatest.blogspot.com/2008_09_01_archive.html](http://raywoodcockslatest.blogspot.com/2008_09_01_archive.html)

This makes absolutely no sense, as I never went to that site when ubuntu was working, so there's no way I could have bookmarked it.

When I try to kill X (ctrl+alt+backspace), the system locks up. I tried booting in recovery mode and chose the 'xfix' option, but that didn't help either. Does anyone know what is going on? The last thing I did when it was working correctly was download and install Cinelerra.

---

### Post by Sef on 2009-04-22
On the desktop, right click > Change Desktop Background > Select the desired background.   (Also you can delete backgrounds too.)

---

### Post by bryceowen on 2009-04-23
You don't understand. The panels at the top and bottom were gone and the only thing left was the above mentioned shortcut. Sure, I could change the desktop wallpaper, but that doesn't let me DO anything. Heck, if that shortcut hadn't been there, I wouldn't have even been able to launch firefox.

I tried going to another tty screen and kill -9 -1 to stop everything then apt-get install ubuntu-desktop in the hopes it would fix the problem. It did, but it didn't. I was able to get back into gnome, but the mouse and keyboard were unresponsive and I got an error about HAL. (I didn't think to write it down. I was frustrated.)

In the end, since I hadn't really DONE anything with it, I slicked the drive and reinstalled Ubuntu. So far, no problems. I think I may avoid Cinelerra for now...

---

