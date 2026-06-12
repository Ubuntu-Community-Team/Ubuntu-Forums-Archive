---
title: "fsck no longer possible in 9.10"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by 00edd on 2009-11-02
hi
I've upgraded from 9.04 to 9.10 yesterday, vie the update manager, and suddenly I can't run fsck anymore, it tells me 

/dev/sda6 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

that never happened before, and I didn't change any disk settings. even in recovery mode, it disappeared from the options list. 

can somebody please explain why that is, and how I can run file system checks in 9.10?
many thanks!

---

### Post by computor on 2009-11-02
It's probably a new safety feature.  It's not really safe to run fsck on a mounted volume.  Not sure why you can't do it from recovery mode, however.

I usually use the Windows method:

sudo tune2fs -C 1000 /dev/sda1 (or whatever partition you want to check)

This resets the mount count and should force an fsck on the next reboot.

---

### Post by lensman3 on 2009-11-02
fsck has always said that!  

fsck said that back in the '80s on a Sun 3.

fsck changes inodes and superblocks without going through the file system kernel subsystems.  Unmount the file system or make it read-only.  Probably have to use the force flag for umount.

Hope this helps.

---

### Post by stmiller on 2009-11-02
Boot in single user mode to run fsck. Yes it's always been this way. :)

---

### Post by 00edd on 2009-11-04
> **computor said:**
> 
I usually use the Windows method:

sudo tune2fs -C 1000 /dev/sda1 (or whatever partition you want to check)

thanks! it did indeed force a fsck on recovery mode restart

> **lensman3 said:**
> fsck has always said that!  

the point is, it disappeared from the options list in recovery mode, and it was there before. recovery mode became quite strange anyway, when I choose 'continue normal boot', or whatever it's called, it used to go straight to gnome, but now I end up in text mode. have to ctrl-alt-del to restart again and choose normal login to get to gnome now. what's up with that? seems like a few steps backwards..

---

