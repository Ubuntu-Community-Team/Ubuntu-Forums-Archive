---
title: "how to specify driver startup dependency"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by ThunderRd on 2008-08-04
Is it possible to specify that a driver be dependent on another driver starting?  In other words, can I make it a requirement that driver B cannot start until driver A has successfully started?

My Hardy install is fine except for one thing-for some reason the mount points of the drives change on reboot.  This causes all kinds of problems with Samba, and the mounting of the SATA drives (Ubuntu and XP are on independent IDE drives).

I believe after investigation that *sometimes*, due to something in my hardware, Ubuntu sees the SATA controller first, instead of the IDE, and this causes the problem.

Can I make the startup of the SATA controller contingent on the successful start of the IDE controller?  If so, how is it done?

There is a thread regarding this at this url.  It's on another site because I couldn't get any responses when I originally posted my problem here ;):
[http://www.linuxquestions.org/questions/linux-software-2/samba-is-changing-mount-points-658343/page2.html?posted=1#post3235791](http://www.linuxquestions.org/questions/linux-software-2/samba-is-changing-mount-points-658343/page2.html?posted=1#post3235791)

---

### Post by xen-uno on 2008-08-04
Check the contents of your /media directory. I had some folders named sda1, sdb5, etc that were duplicates (as far as the system was concerned) of my NTFS mount labels. For instance, **sda1** was a duplicate of the properly named **data** partition. What it would do is mount **data**, but on the next bootup it wouldn't, and instead created **data_**, and the cycle continued. Now my media dir contains nothing except for cdromX's and my (4) NTFS partitions. I also removed all NTFS entry lines from fstab, and instead have Ubuntu auto-mount them.

---

### Post by ThunderRd on 2008-08-04
Nothing unusual in /media.  Just CD, floppy, and the two drives I am mounting.

---

### Post by Yellow Pasque on 2008-08-04
Can you post your /etc/fstab ? If your hardware presents the controllers to you in a different order and screws up the /dev/sd## links, then it's better to mount by UUID. I'll show you my fstab as an example.


```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a119114-4fd7-4ee0-922f-a7d03a5b4b3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=196c7c15-ca90-492f-a140-1957cfb65bfe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec     0       0
```

To get the UUID:
```
cd /dev/disk/by-uuid; ls -la
total 0
drwxr-xr-x 2 root root 100 2008-08-03 23:50 .
drwxr-xr-x 6 root root 120 2008-08-03 23:50 ..
lrwxrwxrwx 1 root root  10 2008-08-03 23:50 196c7c15-ca90-492f-a140-1957cfb65bfe -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-08-03 23:50 7a119114-4fd7-4ee0-922f-a7d03a5b4b3e -> ../../sda1
```

---

### Post by ThunderRd on 2008-08-04
> **Temüjin said:**
> If your hardware presents the controllers to you in a different order and screws up the /dev/sd## links, then it's better to mount by UUID.

That was the first thing I did ;)  fstab here:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# sdb1: Linux
UUID=e4e7a3e8-1a47-434d-89b9-27791d79be88 /               ext3    relatime,errors=remount-ro 0       1

# sdb5: Linux swap
UUID=6b80dd2e-1943-4a6b-a432-452160ac8c12 none            swap    sw            	0       0

# removable
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 			0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 			0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 			0       0

# sdc1: SATA 160GB
#/dev/sdc1	/media/FAT32_REPO	vfat	rw,user,auto,exec			0	0
UUID=E8C8-82D7	/media/FAT32_REPO	vfat	defaults,auto,users,umask=000		0	0

# sdd1: SATA 250GB
#/dev/sdd1	/media/FAT32_ARCH	vfat	rw,user,auto,exec			0	0
UUID=4889-5BE5	/media/FAT32_ARCH	vfat	defaults,auto,users,umask=000		0	0
```


It's all documented here in this thread on another site, but no one has gotten to the bottom of the cause yet ;)
[http://www.linuxquestions.org/questions/linux-software-2/samba-is-changing-mount-points-658343/page2.html?posted=1#post3235791](http://www.linuxquestions.org/questions/linux-software-2/samba-is-changing-mount-points-658343/page2.html?posted=1#post3235791)

It is also similar to this guy's situation I think:
[https://bugs.launchpad.net/ubuntu/+bug/224969](https://bugs.launchpad.net/ubuntu/+bug/224969)

---

