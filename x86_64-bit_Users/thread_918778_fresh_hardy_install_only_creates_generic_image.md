---
title: "fresh hardy install only creates generic image"
date: 2008-09-13
forum: x86 64-bit Users
---

### Post by tomgarvin on 2008-09-13
wanted a clean slate, so i repartitioned and formatted my drives, and installed from the 8.04 (hardy) amd64 CD fresh.  however, upon reboot, the generic image (and recovery) was my only option.  sure enough, it booted the generic image, and i can find no 64bit image in /boot.

i do have WinXP installed on this sytem, and grub seemed to handle this fine.  i need the 64 bit install to address my 4Gb of memory.  it was running the 64bit image on my previous install (7.10).

i even thought, oh well i'll just install the 64bit image... but i see neither the proper headers or images in synaptic.

what gives?  what am i missing?

---

### Post by tomgarvin on 2008-09-13
forget about it.  i only have 2Gb of memory, so no compelling reason to go to 64-bit version.

---

### Post by ptn107 on 2008-09-13
If you installed Ubuntu 64-bit then your running the 64-bit kernel.  The 'generic' image tag has nothing to do with your processor architecture, but rather the type of processor you have; e.g. desktop, server, real-time, etc...

You can verify your running 64 by typing *uname -m*.
For example, my output is:
```
phil@phil-desktop:~$ uname -m
x86_64
```

> 
forget about it. i only have 2Gb of memory, so no compelling reason to go to 64-bit version.

*Addressing larger amounts of memory is only one of the many benefits of 64-bit computing.

*[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by wowbuts5 on 2008-09-14
[world of warcraft gold](http://veryge.com/) Don't miss those.Here are some tips that we hope will give you a better experience in Alterac Valley. Buy world of warcraft gold, This is a very involved Battleground and it can take time to learn how everything worksDon't miss those.Here are some tips that we hope will give you a better experience in Alterac Valley. Buy [world of warcraft gold](http://veryge.com/), This is a very involved Battleground and it can take time to learn how everything works [ffxi gil](http://veryge.com/)

---

