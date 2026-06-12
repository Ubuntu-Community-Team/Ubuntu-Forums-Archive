---
title: "Gutsy full system hard lock up with and without xorg this relates to K2.6.22"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jaakan on 2007-11-20
Chaintech Summit MK8M800 motherboard
AMD64 2800+
NV GF6200 AGP 256Mb
512Mb ram
160GD HD
USB 160Gb HD
the last bios update came out in 1995 or 1996
I only use x64 version of linux in my case


seemingly random full system lock up from clean installs of 7.10 desktop and server
in the middle of installs, yea even with the live CD once, mid boot, playing a pod cast etc.

this thread it for lockups not related to the X drivers for ATi or NV cards but the Kernel

from the logs it look like the I/o subsystem was put to sleep and not fully waken up. the only problem is that power saving is fully turned off

2.6.22 kernel is at the heart of the lock up i'm getting

---

### Post by jaakan on 2007-11-20
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129831](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129831)

---

### Post by arsham on 2007-11-23
I agree
There are some problems in 2.6.22 that I am using
Most of time changing from generic to 386 solves for someones , means that some kernel modules for some hardware are making these kind of problems , along xorg change of architecture that they say 
I remember in feisty I used xorg 7.2 with 2.6.23 , there were no lock-ups  , because the drivers used in 7.2 version in feisty  repositories were match the kernel modules those days.

So , I prefer testing feisty again with the latest updates to see if the problems are related with modules+xorg architecture+hardware varieties 

I tested the current gutsy with use of xorg drivers of the feisty repository and chance in stability was higher than this situation , but the 10 mins stability went to 2 days , maybe there are still problems with drivers

This is confused for me , what should I do and what should I say

Arsham

---

