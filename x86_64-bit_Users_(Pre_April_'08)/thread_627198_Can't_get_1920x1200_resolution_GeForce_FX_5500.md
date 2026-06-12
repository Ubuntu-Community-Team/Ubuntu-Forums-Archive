---
title: "Can't get 1920x1200 resolution GeForce FX 5500"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by markmaus on 2007-11-29
I can't seem to get 1920x1200 resolution on Gutsy AMD64.  I'm using a GeForce FX 5500 AGP video card with the Nvidia restricted drivers and it only seems to run at 1600x1200@50.  When I run nvidia-settings there is no option to select 1920x1200, although when I edit /etc/X11/xorg.conf there is an entry for 1920x1200.  In fact I have deleted all of the other resolutions in xorg.conf and left only 1920x1200 and I also generated the modelines with gtf 1920 1200 59 and pasted the output from that into the Display section of xorg.conf.  All to no avail.  It's like my OS is just ignoring the xorg.conf file.  Any help would be appreciated.  :confused:

---

### Post by markmaus on 2007-12-01
I solved my problem.  I replaced the Nvidia 5500 video card with an Nvidia 6200 video card and voila!  It booted right up to 1920x1200.  I guess that the 5500 wasn't capable of outputting that high of resolution.

---

