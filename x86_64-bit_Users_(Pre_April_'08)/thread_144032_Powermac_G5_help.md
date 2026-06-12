---
title: "Powermac G5 help"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mtlhead on 2006-03-13
Ok, I want to install ubuntu onto my dual 2.3ghz PowerPC on my external hard drive (which is partitioned into 2 parts, 100gb and 100gb), but i keep getting the grey error screen and my install locks up, is there any solution to this? i have open firmware activated so i can boot from the cd, is there anyway to install from os x? thanks

---

### Post by linear on 2006-03-14
Installing to an external drive is non-trivial. :(  See these threads:
 
[http://www.ubuntuforums.org/showthread.php?t=84131](http://www.ubuntuforums.org/showthread.php?t=84131)
[http://www.ubuntuforums.org/showthread.php?t=40536](http://www.ubuntuforums.org/showthread.php?t=40536)
[http://www.ubuntuforums.org/showthread.php?t=91755](http://www.ubuntuforums.org/showthread.php?t=91755)
[http://www.ubuntuforums.org/showthread.php?t=89990](http://www.ubuntuforums.org/showthread.php?t=89990)

---

### Post by mtlhead on 2006-03-14
Ok, well i partitioned my hard drive, and have linux on the other partition, but now i get some error with the video drivers and my partition not being there.  It says it is "dropping to a shell", and locks up. Any ideas?

insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/bitblit.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/font.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/tileblit.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/console/fbcon.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/cfbcopyarea.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/cfbfillrect.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/cfgimgblt.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/softcursor.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/vgastate.ko' : no such file or directory
insmod: can't read '/lib/modules/2.6.12-10-powerpc/kernel/drivers/video/vga16fb.ko' : no such file or directory

---

