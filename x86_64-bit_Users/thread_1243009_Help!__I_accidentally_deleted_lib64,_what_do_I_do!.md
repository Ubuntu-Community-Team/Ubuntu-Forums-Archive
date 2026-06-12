---
title: "Help!  I accidentally deleted /lib64, what do I do!"
date: 2009-08-17
forum: x86 64-bit Users
---

### Post by MechaMechanism on 2009-08-17
SOLVED

Edit:  Here's what I did to save my hide.  I booted into an live CD of Ubuntu and mounted my root disk.  I then made a symbolic link to the live CD's /lib and the link went on the disk.  This works because when I reboot the link is now pointing to the /lib on the disk.

```
$sudo ln -s /lib /media/disk/lib64
```Talk about excitement!  Original post below.



I accidentally deleted /lib64.  Everything else is fine as far as I can tell.  Is lib64 not a symbolic link directory?  I used an live CD to create a symbolic link but my computer still stops in the middle of the boot up progress bar.  Is there something else I need to do?

---

