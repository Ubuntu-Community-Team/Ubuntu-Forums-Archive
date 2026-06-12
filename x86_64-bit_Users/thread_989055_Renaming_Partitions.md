---
title: "Renaming Partitions"
date: 2008-11-21
forum: x86 64-bit Users
---

### Post by randiroo76073 on 2008-11-21
I'm running Ubuntu 8.10 x64, and I multi-boot(no Win), like to try different distro's.  The question is can I rename a partition in gparted without messing up the MBR ?  I have LVM2 installed & setup if that's pertinent, I already edit menu-lst & fstab but in the file browser they show up as x-gb partition(not automounted at boot).  Any feedback appreciated, thanks.

---

### Post by Arup on 2008-11-21
As long as the partition is not root or swap, you can do anything with the rest of the space.

---

### Post by randiroo76073 on 2008-12-01
Uhhhmmm, not entirely so my friend, my main distro is Intrepid(will be Jaunty next) and I essentially have 3-5 roots(multi-boot), changed the names of all but Ubu & they wouldn't boot(solved), so in order for renaming to work you would have to edit MBR.  Next question: What is best way/program to do this with and still stay bootable ?

---

### Post by drs305 on 2008-12-01
I have not had problems with labeling via gparted, but here are the command line entries for labeling ext and ntfs partitions:

Ext2/3:
```

sudo tune2fs -L *labelname* /dev/sdXX

```
Example:  sudo tune2fs -L *mydata* /dev/sda3

NTFS:
Install ntfsprogs:
```
sudo apt-get install ntfsprogs
```
Label the device:
```

sudo ntfslabel /dev/sdXX *mydata*

```

---

### Post by bodhi.zazen on 2008-12-01
See also :

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

yea it says "USB" but there is nothing unique to USB devices / partitions.

---

### Post by randiroo76073 on 2008-12-01
Thanks for replies, will try again :)

---

