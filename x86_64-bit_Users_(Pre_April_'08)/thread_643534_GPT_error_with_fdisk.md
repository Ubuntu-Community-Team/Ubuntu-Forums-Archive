---
title: "GPT error with fdisk"
date: 2007-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-12-17
Has anyone seen this error that I have highlighted in red before? What does it mean?

```
$ sudo fdisk -l

[COLOR="Red"]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.[/COLOR]


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd65ddc8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9363    75208266   83  Linux
/dev/sda2            9364        9729     2939895    5  Extended
/dev/sda5            9364        9729     2939863+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x397a3979

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156288000    7  HPFS/NTFS
```

---

### Post by jhbumby on 2007-12-17
I do not believe this to be an error, but rather just a warning.  fdisk does not support GPT.  Not to sound like a dink, but use GNU parted instead.  (I did some research into GPT, it seems like it is more tied into solaris than linux, which maybe why it is not supported ????)

---

### Post by Yfrwlf on 2008-03-06
When you issue the p command in parted it should tell you the partition label type which is typically MSDOS unless you made a GPT partition for whatever reason, like to try to have a disk size greater than 2TB.

---

