---
title: "Can't mount hfsplus drive."
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by omjaroo on 2006-05-17
Hi,

I have installed a hard drive that I used as a backup for my g5. It has lots of music and photos on it.

I typed the following in a terminal gnome terminal window:
jared@ubuntu:~$ sudo mount -t hfsplus /dev/hdb /mnt/backup

and I get the following:
mount: /dev/hdb already mounted or /mnt/backup busy

The mount command does not indicate that the volume is mounted and umount says that it is not mounted.

Any ideas?

Thanks for you consideration.

Jared

---

### Post by aysiu on 2006-05-17
I don't know if you can mount just /dev/hdb.
It's usually /dev/hdb1 or /dev/hdb2.

Can you post the output of this command? ```
sudo fdisk -l
```

---

### Post by aimislame15 on 2006-05-17
You need to mount in the /media folder. Like:

```
sudo mount -t hfsplus /dev/hdb /media/mac/
```

Least I've never mounted in any other folder and mine works every time. Also, is your HD named hdb? Could check in Gparted or something to find the /dev/disk0xxx number, as all HD's I mounted mount that way due to the format.

Of course take this with a grain of salt as I am on my OSX partition right now without the ability to test the /mnt theory.

---

### Post by aysiu on 2006-05-17
You can mount it wherever you want. It doesn't have to be in the /media folder.

---

### Post by omjaroo on 2006-05-18
Hi, Thanks for responding.

jared@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9924    79714498+  83  Linux
/dev/hda2            9925       10011      698827+   5  Extended
/dev/hda5            9925       10011      698796   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table
jared@ubuntu:~$

---

### Post by aysiu on 2006-05-18
[QUOTE=omjaroo]
Disk /dev/hdb doesn't contain a valid partition table[/QUOTE] This could be a problem.

Read [this thread](http://www.ubuntuforums.org/showthread.php?t=174962) for more details.

---

### Post by omjaroo on 2006-05-18
>Also, is your HD named hdb? Could check in Gparted or something to find the >/dev/disk0xxx number,

Thank you, that did the trick. Loaded Gparted and ran it. Turns out the drive had an unallocated hdb1, 2, 4 and 6. The HPS+ partitions were hdb3 & 5. I typed those into the terminal and it mounted just fine :-)

Thanks for all your help!

Jared

---

### Post by omjaroo on 2006-05-18
Thank you for your help. I have learned quite a lot from the thread you suggested and your comments :-)

Jared

---

