---
title: "X1270 drivers"
date: 2008-12-09
forum: x86 64-bit Users
---

### Post by epic93 on 2008-12-09
Hi I have searched everywhere and cannot find drivers for ATI radeon xpress 1270. I know that this has been an issue but I saw a thread where someone had managed to get drivers yet there was no link posted to the drivers. If anyone knows the link I would appreciate it If they would post it here.

---

### Post by briandu on 2008-12-09
Why do you not use the unified ATI drivers at

[http://ati.amd.com/support/driver.HTML](http://ati.amd.com/support/driver.HTML)

Google is your friend

---

### Post by dE_logics on 2009-01-06
Unified drivers where?

Same card...the infamous x1270.

You know...what I got from google?...the printer.:mad:

the FGLRX drivers not working properly.

---

### Post by dE_logics on 2009-01-08
Great no help...sticking to windows. :(


Thanks to the good for nothing Dell.

---

### Post by Kilz on 2009-01-08
> **dE_logics said:**
> Unified drivers where?


The link he gave is to the ati drivers page. You might want to look again. ATI has better linux support than some give them credit for since AMD bought them.

---

### Post by Yellow Pasque on 2009-01-09
You don't need to use fglrx/Catalyst if you don't want to (it's not as stable as the open-source radeonhd driver, but its 3D performance is better).
I would recommend purging the fglrx/Catalyst driver and building the radeonhd driver (see: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)) With an X1270, you should be able to use direct rendering/DRI.

---

### Post by dE_logics on 2009-04-02
Hay I found something - 

[http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html](http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html)

IT does mention support for the infamous graphs.

---

### Post by Yellow Pasque on 2009-04-02
That link is to an ancient version of the open-source radeonhd driver. It would be much better to build it from source or use the PPA link in this document: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by dE_logics on 2009-04-03
:lolflag: Humm ok thanks!

---

### Post by dE_logics on 2009-04-04
Hay man...those drivers that you referred to, I tried to download the binaries, but I don't know what to download!...I mean there are tons of deb packages...with no mentioning of ATI.


And what's a PPA link?

---

### Post by Yellow Pasque on 2009-04-04
> **dE_logics said:**
> Hay man...those drivers that you referred to, I tried to download the binaries, but I don't know what to download!...I mean there are tons of deb packages...with no mentioning of ATI.


And what's a PPA link?
At this point, I don't even know what you're trying to do. More info, like your video card, what video driver you're currently using, what's wrong with it (if anything), etc. is necessary.

---

