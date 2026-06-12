---
title: "Problem with webcam in AMD 64"
date: 2008-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Arrgoss on 2008-03-23
Hello,

I'm using Ubuntu 7.10 AMD64 in my Dell Latitude D430 laptop, and I'm having problems installing a Logitech Quickcam Communicate STX webcam. I tried to install Easycam ([https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)), but when I reload my repositories I get the following error message:> [url]http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz: 404 Not Found, which I believe appears because I'm using AMD64, and not the 32 version.

Any tip to go around this, or another way to install my webcam? I must say that, in a previous installation of Ubuntu, the same cam worked out of the box :confused:.

I appreciate your help and, please, take into account that I'm a newbie in the Linux world.

---

### Post by warp99 on 2008-03-26
That directory is only for 32-bit, not for 64-bit:

[http://blognux.free.fr/debian/dists/unstable/main/](http://blognux.free.fr/debian/dists/unstable/main/)

If you want to make the webcam work you need to download the source for your driver and compile, then install the drivers. This thread and the associated links will show you how:

[http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393)

I believe that you webcam uses the gspca driver, but please double check using the instructions. :)

---

### Post by Arrgoss on 2008-03-29
Thanks, that worked!

---

