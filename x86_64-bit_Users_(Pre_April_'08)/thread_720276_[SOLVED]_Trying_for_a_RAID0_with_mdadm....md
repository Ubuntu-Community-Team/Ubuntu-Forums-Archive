---
title: "[SOLVED] Trying for a RAID0 with mdadm..."
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by alexandreracine on 2008-03-10
Hi all, I am trying to build a RAID0 (strip, faster, bigger) just because I love complications ;) and guess what, I can't find a way to make it work.

Just a few things first...

1-This is a working machine on /dev/sda (/) and I want to install my RAID0 on /dev/sdb and /dev/sdc. So I wont be using the installation alternate CD.
2- I have no hardware RAID or chipset RAID on that machine (fake raid)
3- There is no complete documentation for a complete A (partition) to Z (mount, reboot to test and use) howto RAID.

4-To get where I am I use those two articles
4.1 - [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
4.1 - [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

So here I am... I boot the machine, open a console, sudo su - and start :)

-- So I partition everything ether with type 1 or type fd (RAID autodetect) but both gives me some errors later on...  I'll give those details later...--
```

fdisk /dev/sdb
fdisk /dev/sdc
fdisk -l
/dev/sdb 200GB (dev/sdb1)
/dev/sdc 200GB (dev/sdc1)
apt-get install mdadm
mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1

```
fdisk -l tell me that I now have /dev/md0 with 400GB... GOOD!

So I partition the new md0 drive, just like any drive... right?
```

fdisk /dev/md0

```

I create a partition just like with /dev/sdb and /dev/sdc but get the error "WARNING, re-reding the partition table with error 22. Invalid argument. The kernel will use the old table. The new table will be used after a reboot. Disks sync."

I look with fdisk -l and I now have /dev/md0p1
I reboot and check fdisk -l if the result is the same. The /dev/md0p1 is still there with 400GB.

So, I want to format the partition.
```

mkfs.ext3 /dev/md0p1

```
Now I get an error that says /dev/md0p1 does not exist.
Let see...
ls -lh /dev/md0* gives me only md0 ...
So I try this instead... just like the 4.1 reference documentation...
```

mkfs.ext3 /dev/md0

```
Now it format correctly, but checking with fdisk -l after that gives me /dev/sdb, /dev/sdc and /dev/md0 with no valid partitions.

Getting back to the first partitioning of /dev/sdb and /dev/sdc, if I partition with fd type (Linux RAID autodetect) I have the same result...

Either way, looking at the stats, I always get this...
```

# mdadm --misc -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jan 26 14:09:25 2008
     Raid Level : raid0
     Array Size : 390721792 (372.62 GiB 400.10 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Mar 10 01:01:36 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : dc0d28ad:1f8e5319:9369fb4c:51afb7ee
         Events : 0.11

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc

```

After that I would mount it, but I am stuck right there. Thanks for any help.

---

### Post by fjgaude on 2008-03-10
Looks to me that the /dev/md0 is fine, ready to be mounted.

Some programs don't understand raid arrays, gparted doesn't. So let's mount the array and see what happens:

```
sudo mkdir /media/raid

sudo mount /dev/md0 /media/raid
```

When you see the "no vaild partition table" from fdisk -l and the like, /dev/md0p1, it's because the program doesn't handle multidisk arrays correctly.

Let us know if things go well.

---

### Post by dagrump on 2008-03-10
I'm too old & to lazy to do things the hard way, I used 6.06 server disk to setup my array let it install, & then used the alt. disk to install & over write the existing array. Not pretty, & not fancy, but I'm lazy & it just works.

---

### Post by alexandreracine on 2008-03-10
> **fjgaude said:**
> Looks to me that the /dev/md0 is fine, ready to be mounted.

Some programs don't understand raid arrays, gparted doesn't. So let's mount the array and see what happens:

```
sudo mkdir /media/raid

sudo mount /dev/md0 /media/raid
```

When you see the "no vaild partition table" from fdisk -l and the like, /dev/md0p1, it's because the program doesn't handle multidisk arrays correctly.

Let us know if things go well.

Haaa, ok it is working. But how would you add this to your fstab or automount it?

---

### Post by celestius on 2008-03-11
open up your fstab file (mine was located in /etc) with a text editor and add the following line:

```
/dev/md0	/media/raid	ext3	defaults	0	0
```

that's what worked for me. limited accounts can't edit that file so i had to use sudo gedit /etc/fstab

---

### Post by fjgaude on 2008-03-11
> **celestius said:**
> open up your fstab file (mine was located in /etc) with a text editor and add the following line:

```
/dev/md0	/media/raid	ext3	defaults	0	0
```

that's what worked for me. limited accounts can't edit that file so i had to use sudo gedit /etc/fstab

Good, but I would make the second "0" a "2" so that the array gets checked every 30 or so boots.

---

### Post by alexandreracine on 2008-03-11
> **celestius said:**
> open up your fstab file (mine was located in /etc) with a text editor and add the following line:

```
/dev/md0	/media/raid	ext3	defaults	0	0
```

that's what worked for me. limited accounts can't edit that file so i had to use sudo gedit /etc/fstab


Correct, the fstab file is actually /etc/fstab and needs root privilege to edit.

I used this :
```
/dev/md0	/media/raid	ext3	defaults	0	2
```

And it work very well. After a reboot, the raid0 is still there! I was actually worried about fdisk not seeing the partitions, but that seems to be "normal". I could actually fill a bug report about that. What do you think? :)

Thanks all.

---

### Post by fjgaude on 2008-03-13
Beleive me, the developers of gparted know about this, haven't had the time to fix it. Complicated!

BTW, there's nothing wrong with running fsck on a software raid array, as long as it isn't mounted.

**Always have a backup made of important data.**

---

