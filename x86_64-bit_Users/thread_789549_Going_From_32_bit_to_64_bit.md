---
title: "Going From 32 bit to 64 bit"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by fenderocker on 2008-05-10
I'm replacing pretty much everything in my computer except for the hard drive. I'm currently using a 32 bit processor and my new processor will be a 64 bit. Do I have to do anything to my currently installed Hardy Heron install? Do I have to install Ubuntu 64x instead?

---

### Post by Kilz on 2008-05-10
> **fenderocker said:**
> I'm replacing pretty much everything in my computer except for the hard drive. I'm currently using a 32 bit processor and my new processor will be a 64 bit. Do I have to do anything to my currently installed Hardy Heron install? Do I have to install Ubuntu 64x instead?

You dont have to , but you may want to reinstall the 64bit version to take advantage of all that new hardware you just paid for. Otherwise you might as well just leave the old 32bit processor in. You have to do a clean install, there is no way to say upgrade from 32bit to 64. You can also do a duel boot 32bit and 64bit and slowly move over if you have the hard drive room.

---

### Post by Sef on 2008-05-10
I just converted to 64-bit and find not a lot of difference with 32-bit.  If you do gaming or video editing, then you will notice a big difference.  I noticed a difference when downloading about 2800 files (1800 pics) from my usb to my hard drive.  That usually takes about 30 - 40 minutes, but only took about 4 with the 64-bit. But in everyday use, I rarely notice it.  Biggest headache is not all programs have a 64-bit version, so you have to install it under a 32-bit system.  Not hard, but there are some tweaking to do, to get them running.  Am I glad I changed?  Yes, I am.  Eventually 64-bit will be the norm, and I do like to be ahead of the curve.

---

### Post by tamoneya on 2008-05-10
I also use 64 bit and it seems to be a little faster.  One thing you should note about 64 bit is that there is no native flash plugin.  flashplugin-nonfree is 32 bit only.  While you can get flash working on 64 bit it is a bit more difficult and I find that it is a bit more unstable than 32 bit.

---

### Post by fenderocker on 2008-05-10
> **Kilz said:**
> You dont have to , but you may want to reinstall the 64bit version to take advantage of all that new hardware you just paid for. Otherwise you might as well just leave the old 32bit processor in. You have to do a clean install, there is no way to say upgrade from 32bit to 64. You can also do a duel boot 32bit and 64bit and slowly move over if you have the hard drive room.

sounds like I'm lucky I have a separate home partition :D

Thanks for the help :D

---

### Post by remu on 2008-05-10
> **tamoneya said:**
> I also use 64 bit and it seems to be a little faster.  One thing you should note about 64 bit is that there is no native flash plugin.  flashplugin-nonfree is 32 bit only.  While you can get flash working on 64 bit it is a bit more difficult and I find that it is a bit more unstable than 32 bit.

While flash won't work natively, all you have to do is enable medibuntu (I think you may have to do that on the 32bit, don't know for sure), and go:

sudo apt-get install flashplugin-nonfree

and that will install flash for you with ndiswrapper, it really isn't difficult at all.

---

### Post by Sef on 2008-05-10
Also I have been told that Swfdec works well.  You can even watch YouTube on it, and it is in the repositories under Universe, I believe.

---

### Post by Kilz on 2008-05-10
> **remu said:**
> While flash won't work natively, all you have to do is enable medibuntu (I think you may have to do that on the 32bit, don't know for sure), and go:

sudo apt-get install flashplugin-nonfree

and that will install flash for you with ndiswrapper, it really isn't difficult at all.

You dont even have to enable medibuntu, flashplugin-nonfree is in the ubuntu repositories.

---

### Post by Yellow Pasque on 2008-05-11
Please read the stickies in this forum:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
Flash: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by remu on 2008-05-11
> **Kilz said:**
> You dont even have to enable medibuntu, flashplugin-nonfree is in the ubuntu repositories.

Well there you go!

---

