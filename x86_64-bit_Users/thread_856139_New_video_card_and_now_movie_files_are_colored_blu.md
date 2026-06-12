---
title: "New video card and now movie files are colored blue?"
date: 2008-07-11
forum: x86 64-bit Users
---

### Post by paholg on 2008-07-11
I just got an nvidia geforce 9600 gt, and, after putting it in, everything worked fine.

After upgrading to the 173.14.09 drivers, though, all of my video files play with a bluish tint.  Everything else works fine, including flash movies such as youtube.

Note:  I'm pretty sure that before updating the drivers, but after installing the card, everything worked fine.

I have tested multiple media formats (avi, mpg, and wmv) in multiple players (vlc, totem, and mplayer) and they all have the same problem.  A screenshot is included to demonstrate.


Anyone have any ideas how this might happen, or how to fix it?

Thanks so much!

I'm running 64 bit Hardy, if that's relevant.

---

### Post by kerry_s on 2008-07-11
change the video output in the settings, i think X11 or xv, can't remember.

---

### Post by philinux on 2008-07-11
Close vlc.
Delete the .vlc folder from your home directory and let vlc create a new default one.

---

### Post by paholg on 2008-07-11
Changing the output to X11 worked like a charm.  Thanks!

---

