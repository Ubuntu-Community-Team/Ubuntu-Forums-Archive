---
title: "Floppy Drive isn't working"
date: 2006-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by fatsheep on 2006-07-18
I previously had a x86 version of Ubuntu on my system in which the floppy worked flawlessly but after have switching to the AMD 64 one (as I have a AMD 64 3000+ venice) now the floppy drive isn't working. :confused:  Here's the error message I get when I try to access it:

> mount: i could not determine the filesystem type, and none was specified

---

### Post by Kilz on 2006-07-18
> **fatsheep said:**
> I previously had a x86 version of Ubuntu on my system in which the floppy worked flawlessly but after have switching to the AMD 64 one (as I have a AMD 64 3000+ venice) now the floppy drive isn't working. :confused:  Here's the error message I get when I try to access it:
Are you trying to mount the floppy in the terminal?

---

### Post by fatsheep on 2006-07-18
> **Kilz said:**
> Are you trying to mount the floppy in the terminal?

No I'm just trying to access files I have on some floppy disks.

---

### Post by fatsheep on 2006-07-18
Any advice on getting it working?

---

### Post by fatsheep on 2006-07-18
Here's my etc/fstab file if that helps any:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


---

