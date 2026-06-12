---
title: "Another G3 iMac install problem"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by gazman on 2005-12-11
First off, I have read quite a number of posts on this issue and I have already edited my xorg.config file to delete the "dri", changed the horizontal refresh rate to 60-60 and vertical refresh rate to 43-117.

It is a 600MHz, slot-loading G3 with 512MB RAM and 16MB Ati Rage 128 Pro card, 40 Gig hard drive split into an OSX and (hopefully!) Ubuntu partition.

I initially tried updating from Hoary, when that went pear-shaped I tried erasing the Ubuntu partition and reinstalling Breezy, same problem.  When starting up the new splash screen starts up saying 'loading modules', but then reverts back to a text startup with a whole heap of warnings saying:

```
insmod: can't read '/lib/modules/2.6.12-9-powerpc/kernel/drivers/video/*
```

with * replaced by a number of directories and files.  Eventually it takes me to a warning about the X window system not being configured properly.  Hoary was working fine and the same CD has installed fine onto the G3 PowerBook (slower processor and video card).  I would like to upgrade, apart from always wanting the latest and greatest, mainly for the new features in OO.org.

---

### Post by gazman on 2005-12-11
Not to worry, I've given up on Ubuntu and gone back to OSX.

---

