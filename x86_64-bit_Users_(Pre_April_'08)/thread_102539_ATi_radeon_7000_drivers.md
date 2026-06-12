---
title: "ATi radeon 7000 drivers"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by levkaizer on 2005-12-12
Hey, this is my first post and I'm new to Linux.  I just installed Ubuntu last night and when the Xserver boots up the screen goes black!  I've asked some people for help and they tell me to edit my xorg.conf file.  What do I need to change and how do I do it?  Any help would be great!!  I am running a Radeon 7000 graphics card on a AMD 2800+ processor.

---

### Post by Imexius on 2005-12-12
To edit your xorg.conf file do the following

sudo pico /etc/X11/xorg.conf

Then under BUSID type: Option        "noaccel"

hit ctrl o then press enter then press ctrl x

Once finished type startx and things should work

---

### Post by levkaizer on 2005-12-20
I tried that, I could only find the BusId in a section called "Device".  This detailed my graphics card.  I added in a section that read
Option "noaccel"

underneath the BusId part, but it did nothing.  Could it be anything else?

---

### Post by linbetwin on 2005-12-20
I don't know how to help you, but I also have the ATI 7000 VE graphics card and an AMD Athlon XP 2200+ (1,8 GHz) and I don't have those problems that you have. The graphics card may not be the cause.

---

### Post by levkaizer on 2005-12-20
Ok, do you think that reinstalling might be a good idea?

---

