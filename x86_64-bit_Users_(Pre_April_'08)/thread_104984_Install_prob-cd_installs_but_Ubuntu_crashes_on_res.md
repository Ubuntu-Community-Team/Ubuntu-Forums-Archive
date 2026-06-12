---
title: "Install prob-cd installs but Ubuntu crashes on restart"
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by trjtrj on 2005-12-17
Hi, new user, AMD 64 system.

The live cd works great, but when I use the other disk, installer 64 it won't go.  I have tried ver 5.10 and ver 5.04 and both have the same problem.

I can do the install cd ok, I have 3 hd and want to put Ubuntu on hd 3 which is a USB externat with 2 primary partitions.  I can do the install cd to make the first partition free space and the auto partition makes the first and swap partitions and formats.

Then the install cd puts all the Ubuntu stuff on automatically and says reboot.

On reboot I get the crash 
-
loading moduels
booting kernal, loading
/dev/sdb1 does not exist dropping to shell

then nothing
-
same deal with Ubuntu 5.04
-
decompressing Linux..done
booting kernel
audit..initialized
starting Ubuntu..
pivot_root no such file or directory
/sbn/init: 428; cannnot open dev/console: no file
kernel panic-not syncing: attempted to kill init
--

what's the problem? Is the auto partition not working, it put the linex file system on one. but is the swap file not having the proper linex file system format or what?

please help by replying to my post

---

