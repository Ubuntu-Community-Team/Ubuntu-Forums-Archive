---
title: "Wine wow and gutsy poor performance"
date: 2007-11-25
forum: Wine
---

### Post by chadless on 2007-11-25
OK, I have installed wine and wow, and everything is running w/o any crashes or errors. I am just gettin very poor performance even with the lowest graphical settings. 

I have read every install guide and troubleshooting guide I could find and have tried everything they say, but I am still just not getting even close to the performance from when   I was on xp (shudders).

I am running a radeon x1650, maybe my card is just not going to work? any ideas?

I am also running an amd dual core 3200 processor and have 1 gig of ddr2 ram

I think this should be enough to handle what I am trying to do

---

### Post by Tyke91 on 2007-11-25
just a thought... have you installed the latest ATI drivers?

---

### Post by chadless on 2007-11-25
I believe I have. My understanding though is that there are two dif ways that I can get my video drivers.

I went to this site and followed their directions
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
so I believe I got the most up to date drivers

---

### Post by chadless on 2007-11-25
You know I do have one important bug. my minimap doesn't render a map, regardless of whether I am outside or in.

---

### Post by chadless on 2007-11-26
Ok, I have done some more reading, and I think maybe its my wine version. I have the most up to date version, but I have seen some people complain of things not working after they update. 

Could going back a version help and if so, does anyone know of a version of wine that works well with wow?

---

### Post by hikaricore on 2007-11-26
0.94.7 had worked nearly flawless until late.

Blizzard started ******* around with **** again and as of recent my girl's game has been locking up randomly every 30mins-5hrs with no particular pattern.
But I still believe 0.94.7 to be the best version, just be aware that many people are having issues based on WoW patches and not WINE.

---

### Post by chadless on 2007-11-26
Good to know, ty very much. I will try it out and post my results

---

### Post by chadless on 2007-11-26
Ok, I tried using the older version but I am still getting the same results. Though I do get errors when I launch playonlinux, saying that I don't have 3d acceleration.

Again I have a x1650 radeon, could this be my problem, and if so, how do I enable 3d acceleration?

---

### Post by hikaricore on 2007-11-26
I have no idea what playonlinux is, but check the output of:

> glxinfo | grep rendering

---

### Post by chadless on 2007-11-26
My results

Xlib:  extension "XFree86-DRI" missing on display ":2.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

---

### Post by Ferrat on 2007-11-26
Im running WoW Flawless with 0.9.49 

tip on FPS is to lower all the settings and make the ATi drivers force AAx2, this makes the gamestill look very good, for me even a bit easier on the eyes and this keeps me on a steady 30+ FPS (with some drops to 25 in really croweded areas)

Running with ATi driver 8.40.4 btw which sadly still is the recommended version from ATi

---

