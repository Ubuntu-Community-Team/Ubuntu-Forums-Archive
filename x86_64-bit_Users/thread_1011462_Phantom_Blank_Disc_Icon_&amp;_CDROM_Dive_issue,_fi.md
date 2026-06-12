---
title: "Phantom Blank Disc Icon &amp; CDROM Dive issue, fix!"
date: 2008-12-14
forum: x86 64-bit Users
---

### Post by Gabt on 2008-12-14
In reference to this: [Link](http://ubuntuforums.org/archive/index.php/t-876155.html)

I had a exactly the same issue. Blank CD icon on desktop, and no functionality from the CD drive. But it didn't bother me, until recently when I wanted to make a CD. 

Fix:

sudo gedit /etc/fstab 
and i commented out the line to the currently mounted "cdrom"
e.g. /dev/sdb                                   /media/cdrom1    udf,iso9660  defaults

then i added :
/dev/hda                                   /media/cdrom1    udf,iso9660  user,auto
 
'hda' Being my cd drive, rebooted, Icon gone, CD rom fully working.

doesnt stop the hda:drive not ready for command error, but it appear that the drive is ready for the command when you need it to be :D

hopefully someone finds this usefull.

---

