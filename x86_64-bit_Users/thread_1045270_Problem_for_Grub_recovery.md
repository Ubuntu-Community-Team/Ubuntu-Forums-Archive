---
title: "Problem for Grub recovery"
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by seraphlz on 2009-01-20
Hello everyone, I reinstalled windows xp and tried to recover Grub by live dvd (ubuntu 8.04 x64). But it failed as follows:

grub> find /boot/grub/stage1
find /boot/grub/stage1
(hd0,11)
grub> root (hd0,11)
root (hd0,11)
grub> setup (hd0)
setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,11)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition 

How to solve this problem?

---

### Post by cariboo on 2009-01-20
Boot from the LiveCD and in a terminal type:

```
sudo fdisk -l
```

and paste the output in your next post. From the looks of it you have 11 partitions on your hard drive, so that could make things a little complicated. The fdisk command should help us sort things out.

JIm

---

### Post by caljohnsmith on 2009-01-20
It sounds like you might have a problem with your HDD's partition table. In addition to what Jim asked for, please also post:
```
sudo sfdisk -luS
sudo sfdisk -d

```

---

### Post by seraphlz on 2009-01-20
I booted from live cd and checked as follows:
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8e8f8e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8393931    c  W95 FAT32 (LBA)
/dev/sda2            1046       30401   235802070    f  W95 Ext'd (LBA)
/dev/sda5            1046        5393    34925278+   b  W95 FAT32
/dev/sda6            5394       12863    60002743+   b  W95 FAT32
/dev/sda7           12864       24958    97153053    7  HPFS/NTFS
/dev/sda8           24959       27508    20482843+   7  HPFS/NTFS
/dev/sda9           27509       29095    12747546    b  W95 FAT32
/dev/sda10          29096       29157      497983+  82  Linux swap / Solaris
/dev/sda11          29158       30401     9992398+  83  Linux
```

---

### Post by seraphlz on 2009-01-20
And
```
ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  16787924   16787862   c  W95 FAT32 (LBA)
/dev/sda2      16787925 488392064  471604140   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5      16787988  86638544   69850557   b  W95 FAT32
/dev/sda6      86638608 206644094  120005487   b  W95 FAT32
/dev/sda7     206644164 400950269  194306106   7  HPFS/NTFS
/dev/sda8     400950333 441916019   40965687   7  HPFS/NTFS
/dev/sda9     441916083 467411174   25495092   b  W95 FAT32
/dev/sda10    467411238 468407204     995967  82  Linux swap / Solaris
/dev/sda11    468407268 488392064   19984797  83  Linux
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 16787862, Id= c, bootable
/dev/sda2 : start= 16787925, size=471604140, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 16787988, size= 69850557, Id= b
/dev/sda6 : start= 86638608, size=120005487, Id= b
/dev/sda7 : start=206644164, size=194306106, Id= 7
/dev/sda8 : start=400950333, size= 40965687, Id= 7
/dev/sda9 : start=441916083, size= 25495092, Id= b
/dev/sda10: start=467411238, size=   995967, Id=82
/dev/sda11: start=468407268, size= 19984797, Id=83
ubuntu@ubuntu:~$ 
```

---

### Post by ranch hand on 2009-01-20
Just lurking again.  Grub is powerful and versitile.  That means it can be screwed up royally.  I am good at that part.

---

### Post by caljohnsmith on 2009-01-20
> **seraphlz said:**
> I booted from live cd and checked as follows:
```
ubuntu@ubuntu:~$ sudo fdisk -l
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8e8f8e8

```
Getting that "omitting empty partition (x)" error is unfortunately a sure sign that your partition table is partially corrupt, and that would explain why you are getting such strange Grub errors. In your case, since you don't have any overlapping partitions, getting an "omitting empty partition (x)" error usually means you have an EBR (Extended Boot Record) that points to another EBR that doesn't exist any more (the EBRs are associated with your logical partitions). Fortunately the solution is usually simple for that type of situation, so how about doing:
```
sudo fdisk /dev/sda
```
Press "w" and then enter, and that should hopefully fix the problem. What that does is simply rewrite your current partition table with all the original values, except fdisk does not include the non-existent EBR. So after doing the above fdisk command, how about posting:
```
sudo fdisk -lu
```
And if that does not show the "omitting empty partition (5)" error any more, then reboot, and how about trying the Grub commands again and let us know how it goes.

---

### Post by seraphlz on 2009-01-21
caljohnsmith, I did it as you said. It gave warning message as follows:
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
omitting empty partition (5)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```
However, the fdisk give no errors:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8e8f8e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16787924     8393931    c  W95 FAT32 (LBA)
/dev/sda2        16787925   488392064   235802070    f  W95 Ext'd (LBA)
/dev/sda5        16787988    86638544    34925278+   b  W95 FAT32
/dev/sda6        86638608   206644094    60002743+   b  W95 FAT32
/dev/sda7       206644164   400950269    97153053    7  HPFS/NTFS
/dev/sda8       400950333   441916019    20482843+   7  HPFS/NTFS
/dev/sda9       441916083   467411174    12747546    b  W95 FAT32
/dev/sda10      467411238   468407204      497983+  82  Linux swap / Solaris
/dev/sda11      468407268   488392064     9992398+  83  Linux
```
So, I reboot from live cd and try to recover grub again. I got grub back! Thank you very much caljohnsmith for your sincerely help, and I appreciate Jim's help also! :)

---

### Post by caljohnsmith on 2009-01-21
Glad to hear that worked OK, seraphlz. Cheers and have fun with Ubuntu. :)

---

