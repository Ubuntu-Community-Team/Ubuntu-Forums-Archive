---
title: "CD-RW/DVD+-RW Drive Mounting Problem"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by innocenceisdeath on 2007-10-03
My DVD Drive won't mount anymore unless I input the command:
```
sudo mount /dev/dvd /media/cdrom0
```

Then when I try to unmount it this appears:
```
It seems media/cdrom0 is mounted multiple times
```

But I can unmount it by using the -f parameter:
```
sudo unmount -f /dev/cdrom
```

Here are the contents of my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=09741809-5f8b-4b1e-b853-1845a044c7a2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e7fdd507-89c7-40b5-ba92-0feb6d96273b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0
```

Plus I never had any problems before I did this:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Thanks in advance for any help given

---

### Post by dogson on 2007-10-03
> **innocenceisdeath said:**
> My DVD Drive won't mount anymore unless I input the command:
```
sudo mount /dev/dvd /media/cdrom0
```

Then when I try to unmount it this appears:
```
It seems media/cdrom0 is mounted multiple times
```

But I can unmount it by using the -f parameter:
```
sudo unmount -f /dev/cdrom
```

Here are the contents of my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=09741809-5f8b-4b1e-b853-1845a044c7a2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e7fdd507-89c7-40b5-ba92-0feb6d96273b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0
```

Plus I never had any problems before I did this:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Thanks in advance for any help given

i don't know how gnome-volume manager handles binds in fstab but it might not like that you have /media/cdrom0 /chroot/media/cdrom0 none bind 0 0  in your fstab, just a guess

---

### Post by innocenceisdeath on 2007-10-04
Thanks that was the problem ^_^

---

