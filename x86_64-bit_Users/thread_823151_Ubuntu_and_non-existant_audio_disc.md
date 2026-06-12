---
title: "Ubuntu and non-existant audio disc"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by txnec on 2008-06-08
Ubuntu is behaving oddly.  It pops up and error randomly saying that it was unable to mount an audio disc and gives a file path.  It seems as though when Ubuntu starts doing this, the system is about to crash soon...  My system starts to slow down, icons become missing until i reboot, and just as i was writing this post, my cd drive just popped out for no reason?!?  lol

Anyways, the problems start to become more serious.  The system locks up completely and I have to do a hard-reboot/powerdown.  Often after this, I have to run a manual fsck and typically find a crap load of harddrive errors.  

I'm running an Hardy 8.04 - Acer 5100, 4gb DDR2, AMD turion X2 1.6GHz, ATI gfx card....

I have read about unstability issues that other members of this forum are having.  But these symptoms, aside from the complete lock up, are something I haven't read about before..  I've reinstalled about 1000x... its frustrating cause i'm still a linux newb...

---

### Post by txnec on 2008-06-08
It keeps saying 
Unable to mount Audio Disc
Drive /dev/hdb does not contain audio files

How would i go about looking for what is causing this?

The message pops up randomly

---

### Post by txnec on 2008-06-11
bump

---

### Post by yragrelluf on 2008-06-12
try to install some codecs. do you have gstreamer installed? ive had similar problems, (minus the instability) and i just installes codecs and plugins even ones i dont really need, and thst solved my problem.

---

