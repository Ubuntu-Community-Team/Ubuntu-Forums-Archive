---
title: "partioning on install"
date: 2007-01-14
forum: openSUSE and SUSE Linux Enterprise
---

### Post by simonsimon on 2007-01-14
Hi 

I currently dual boot XP and Ubuntu.

I'm trying to install SUSE and it seems like it wants to delete my Ubuntu partition.  Anyone know how to get it to set up a new partition without wiping my Ubuntu?

Thanks.

---

### Post by bernied on 2007-01-14
You need to know about your current partitioning. So try:
```
sudo fdisk -l
```
Post your output here if you want help with interpreting it.

To make some space on your hard drive for your suse install, you need a partition editor, but you **do not** want to run this while you are using your installed ubuntu (or anything on the disk you want to change). So use a live CD for this job.

An easy partition editor to use (which is probably on your ubuntu install cd) is gparted. Others are qtparted (on knoppix and some other live-cds), or just parted (text only, but you'll find it everywhere).

You need to know some things:
- don't move windows - asking for trouble, though resizing its partition should be ok, within reasonable limits (make sure it's got some spare space)
- windows may be using more than one partition - probably better not to move the start points of any of these (though it's probably fixable if you do)
- you can only have 4 primary partitions, and windows needs to boot from a primary partition (it may have another, which may not be primary)
- if you want more than 4 partitions, then one of the (maximum 4) primary partitions must be an extended partition, in which you can create as many logical partitions as you like
- primary partitions are numbered 1-4, logical partitions are numbered 5 onwards

if you are confused by this, then be very very careful.

---

### Post by simonsimon on 2007-01-14
Thanks for the help.

Here's the output.

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10231    82180476    7  HPFS/NTFS
/dev/sda2           10233       12030    14442435    c  W95 FAT32 (LBA)
/dev/sda3           12031       12161     1052257+  d7  Unknown

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11784    94654948+  83  Linux
/dev/sdb2           11785       12161     3028252+   5  Extended
/dev/sdb5           11785       12161     3028221   82  Linux swap / Solaris
```

---

### Post by bernied on 2007-01-14
Right, so tell me (and don't do any of my suggestions) if I get any of this wrong:
- you have two disks (they are called sda and sdb), both around 100GB
- the first disk (sda) has windows installed on it, there are three partitions, the second and third are very small and probably have something to do with system recovery/restore/backup
- the second disk (sdb) has linux (ubuntu?) installed on it, there is one very large partition (sdb1), with the operating system on it, and a smaller logical partition (sdb5), inside an extended partition (sdb2), which has a swap filesystem - this is virtual memory for linux. It looks like 3GB of swap space - huge!

So, if it were mine, I'd probably leave the first disk alone - there be dragons. Unless of course you really need the space, then you could try to make some space between sda1 and sda2 - shrink sda1.

I guess the easiest thing to do would be to shrink sdb1, then create a new primary partition in the space you've made. This might be called either sdb2 or sdb3 (probably sdb3), but that shouldn't matter. You could install suse in this. Suse can use the same swap space as ubuntu, as they cannot run at the same time and swap space, like memory, does not persist between boots.

But...
- you might want to consider the future. Are you the sort of person who'd want to install another distro in two weeks time? You might need another partition for that.
- also do you want to share files between the two (three) OSes? Do you want to share the whole filesystem, including all those delicate system files, or would you prefer to have some reserved space, that is just for music/video/photo files. You might want another partition for that.

---

### Post by simonsimon on 2007-01-14
Thanks for the suggestions.  Let's see how this goes and I'll let you know.

:)

---

### Post by simonsimon on 2007-01-15
It worked...after dealing with nvidia trouble on the gparted cd.

Thanks so much for your help.

:)

---

### Post by bernied on 2007-01-17
excellent!

---

