---
title: "reading HFS+ usb disk"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by twopeak on 2006-03-25
Hello

I spend some time searching, but it seems like i'm the only one with this problem:
I'm using a pc (compaq) computer with ubuntu.
We have an external disk (Targa) that was used to make backups of two macosx computers. I would like to use this same disk to backup my ubuntu stuff too.
In macosx the disk doesn't have any permissions.

When i plug it into ubuntu, it gets recognized immediately, but I can only read.
when i try to delete a file using "sudo rm nameoffile" it will tell me the disk is read only.
The properties of the disk say the disk owner is "99", and the permissions of the disk are rwx for everyone.
In the system>administration>Disks the disk does appears, but it says it doesn't contain any partition. (and i can't add a new one or anything)

Anybody has a solution for this?

---

### Post by 3rdalbum on 2006-03-26
I was under the impression that HFS+ disks could only be read from Ubuntu, not written... if I'm wrong or if there's some convoluted way to write them too, somebody please chime in.

---

### Post by jdp on 2006-03-26
The drive is probably mounted readonly.  Go into a terminal and type **mount** to get a list of the mounted partitions, then do a **umount /path/to/your/drive** and **mount -w /dev/path/from/first/mount/listing /path/to/your/drive**.  I'm sure there's a better way to get it done with the auto mounting feature of Gnome, but I'm away from a Ubuntu install ATM.  Look for some clues in the Gnome docs for **gnome-volume-manager**. :)

---

### Post by ssam on 2006-03-26
i spoke to twopeak in irc. it seems the problem is to do with the partition being corrupted. dmesg says
```
[4305117.429000] HFS+-fs warning: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
```

mac os x disk utility would not recognise it.

i recommended that he tries to repartition with gparted.

---

### Post by twopeak on 2006-04-03
Hello,
I was out of town for a while, but i'm back...
I re-formated the disk without a problem, GParted asked me to make a new partition table, and then i reformated everything to hfs. Still, the mac won't recognize the disk (ubuntu doesn't have a problem) Then i reformated it in FAT32 and the mac doesn't recognize it either, and then in ext.

I've put some new files on the harddrive, and on ubuntu this disk really doesn't seem to have a problem. On 2 different macs it just doesn't get recognized.

---

