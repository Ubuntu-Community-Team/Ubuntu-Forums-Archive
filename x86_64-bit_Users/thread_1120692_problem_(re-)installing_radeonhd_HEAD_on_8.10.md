---
title: "problem (re-)installing radeonhd HEAD on 8.10"
date: 2009-04-09
forum: x86 64-bit Users
---

### Post by dh003i on 2009-04-09
I did an update of my kernel and kernel headers, and now on my workstation, windows are exceedingly slow in moving (I can see them being re-painted...slowly). I figure that the update over-write something I did when installing radeonhd head. 

So, I'm trying to re-install radeonhd, using the [Ubuntu: RadeonHD]("https://help.ubuntu.com/community/RadeonHD") documentation. Under the *Getting DRM Kernel Modules* section, I successfully executed
```
# git clone git://anongit.freedesktop.org/mesa/drm
```
However, when getting to the checkout step, I get the following:
```
# git checkout -b r6xx-r7xx-support origin/r6xx-r7xx-support
fatal: Not a git repository
```
What's going on here? Also, what are the DRM kernel modules needed for? The checkout step isn't mentioned on the Phoronix uide to [Installing the RadeonHD Driver on Ubuntu]("http://www.phoronix.com/scan.php?page=article&item=843&num=1"). Nor is the checkout step mentioned in the [DRI Wiki]("http://dri.freedesktop.org/wiki/Building#head-b3fb665c9f24b4a32424b78428c082e830832250").

---

