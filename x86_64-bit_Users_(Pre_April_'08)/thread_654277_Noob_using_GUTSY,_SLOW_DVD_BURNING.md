---
title: "Noob using GUTSY, SLOW DVD BURNING"
date: 2007-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dive4Life on 2007-12-30
I have read through the threads and figured that I could some how make my burning faster through using HDPARM.  Most unfortunately, I can't seem to find out where my drives are located.  (i.e.  /dev/f?????)  I have tried to use /etc/fstab to no avail.  I'm sure this is pretty easy for the experienced users out there.  I would appreciate your help.

---

### Post by Offoffoff on 2007-12-31
Did You try to make faster Your drive with DMA settings or just try to set high speed? For fist one - look trough System/Settings/Hardware Information. For second one - just install gnomebaker.

---

### Post by John.Michael.Kane on 2007-12-31
Please post the output of the below command. Make sure to replace scd0 with the proper drive 

```
 sudo hdparm -i /dev/scd0
```

---

### Post by Bartender on 2008-01-02
```
sudo cat /etc/fstab
```
should show you your devices so you have the right name to use in hdparm.  When I bring up things like this, I'll copy/paste the output into a new OpenOffice document and save the document.  Can be handy for future reference.
the "cat" part just shows you the file without letting you edit it.  Safer that way.

---

### Post by ~LoKe on 2008-01-02
> **Bartender said:**
> ```
sudo cat /etc/fstab
```
should show you your devices so you have the right name to use in hdparm.  When I bring up things like this, I'll copy/paste the output into a new OpenOffice document and save the document.  Can be handy for future reference.
the "cat" part just shows you the file without letting you edit it.  Safer that way.

Sudo isn't necessary in this case.   Sudo is only necessary when you're writing to a file.

---

### Post by Dive4Life on 2008-01-03
This is the code from my fstab.  Gonna check to see if there is anything I can do.  Ty for help so far.  I am open to any and all suggestions.


> sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=94efe7bb-db9b-4da0-8c72-2720c3385427 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=2e7c69d7-4509-4567-ba0a-705637129d7c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


---

### Post by Bartender on 2008-01-05
So your two optical drives are identified as /dev/hdc and /dev/hdd

---

