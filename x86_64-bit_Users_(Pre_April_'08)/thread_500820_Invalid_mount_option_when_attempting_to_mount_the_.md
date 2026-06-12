---
title: "Invalid mount option when attempting to mount the volume 'CNC3'."
date: 2007-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Joe88 on 2007-07-14
I'm using Feisty 7.04 32 bit with an AMD 64 processor. When i put my Command and conquer 3 disc in the drive and then close it the disc fails to mount giving me this error message : "Invalid mount option when attempting to mount the volume 'CNC3' ".

All the other cds and DVDs i have tried to mount in my drive have worked.

This is the contents of my fstab file :
[B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=88028bfd-b1b6-4164-b088-efe760823812 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3ab3239d-aabe-412f-a69d-e40613176b9e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/B]

Does anyone know whats wrong?

---

### Post by diddler on 2007-07-14
Apparently not.  I have the same problem.  The WINE apps page for CNC3 says:  "If you are unable to mount the DVD, make sure that /etc/fstab's entry for your cdrom has type auto".

I tried that, but I still get the error message.  I'm not sure what to do next.  If you figure it out, please let me know.

[http://appdb.winehq.org/appview.php?iVersionId=7440](http://appdb.winehq.org/appview.php?iVersionId=7440)

---

### Post by Joe88 on 2007-07-16
I've tried changing a few settings, including setting the drives to auto mount yet the Drive still doesn't play the CNC3 dvd.

If anyone reading this has Ubuntu and can mount the command and conquer 3 DVD please give your fstab details so I can compare them with my fstab and try to figure out whats wrong.

---

### Post by catinabox on 2007-07-17
When I set my drive to auto, I can't seem to mount any cds or dvds at all, I get the error message:

[mntent]: line 9 in /etc/fstab is bad
mount: can't find /media/cdrom0 in /etc/fstab or /etc/mtab

This is my fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1e01eb61-d052-4cc1-843f-69aba560c54b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6164e0a8-8bc8-4224-a6dc-6bdb49b83f6f none            swap    sw              0       0
/dev/hda        /media/cdrom0 auto udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by gbesso on 2007-07-17
Here's what I use, I can mount the CNC3 dvd with no issues.

```
/dev/hda	/media/cdrom0	auto	users,noauto	0	0
/dev/hdb	/media/cdrom1	auto	users,noauto	0	0
```

catinabox: auto needs to come in place of udf,iso9660 :)

---

### Post by catinabox on 2007-07-17
> **gbesso said:**
> Here's what I use, I can mount the CNC3 dvd with no issues.

```
/dev/hda	/media/cdrom0	auto	users,noauto	0	0
/dev/hdb	/media/cdrom1	auto	users,noauto	0	0
```

catinabox: auto needs to come in place of udf,iso9660 :)

Aha! Thank you, it mounts now.

---

### Post by Joe88 on 2007-07-17
thanks gbesso, your settings work perfectly for me, they let my drives read DVDs + CDs +data CDs + Data DVDs + Film DVDs + cnc3 DVD and my DVD writer can still write dvds and CDs :)

---

### Post by wayno on 2007-08-23
worked for me too, THANK YOU :)

---

### Post by wcbardwell on 2007-08-24
Suggestion worked perfect with my CNC3 Kane Edition! Thanks!!!!

---

### Post by beazee on 2007-09-02
Yupi!!!

Thanks a lot. It's really working :)

---

### Post by pan69 on 2007-09-06
> **gbesso said:**
> Here's what I use, I can mount the CNC3 dvd with no issues.

```
/dev/hda	/media/cdrom0	auto	users,noauto	0	0
/dev/hdb	/media/cdrom1	auto	users,noauto	0	0
```

catinabox: auto needs to come in place of udf,iso9660 :)

Whats the difference between *user* and *users* because my fstab says *user*?

---

### Post by Ahslan on 2007-12-24
How do i get permission to change the fstab file??? It never lets me change it and I am logged in as the only user for the computer...

---

### Post by Ahslan on 2007-12-24
YAY! I finally got it by digging through the forums
it was :

gksudo gedit /etc/fstab

---

