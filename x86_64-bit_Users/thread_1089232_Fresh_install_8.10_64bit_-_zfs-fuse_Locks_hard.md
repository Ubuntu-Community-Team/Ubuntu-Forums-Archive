---
title: "Fresh install 8.10 64bit - zfs-fuse Locks hard"
date: 2009-03-06
forum: x86 64-bit Users
---

### Post by nixgeek on 2009-03-06
Hey all,

I recently upgraded my machine (details below). Getting it tweaked
quite nicely. Fresh install of Kubuntu 8.10 64bit. Installed all the
necessary tidbits. Its ready for use now. 

I've installed zfs-fuse from [https://wiki.ubuntu.com/ZFS/](https://wiki.ubuntu.com/ZFS/)
without issue.

Created pool from the two 300gb drives. /zfspool
Created zfs volume /zfspool/home to be used as home
was my plans.

Started a copy of /home/* to the new zfs fs  After about a
minute - system hang. Seconds on clock stops, no mouse movement,
no HD lights.

Hard reboot... tried the copy again... same thing.

Any ideas?


Computer specs:

Intel i7 920
Evga x58 mobo
Evga gtx 260 nvidia 
12gb Crucial Ddr3 ram
2x 250gb hd seagate  {OS mirrored via mdadm}
2x 300gb hd seagate

Nixgeek.

---

