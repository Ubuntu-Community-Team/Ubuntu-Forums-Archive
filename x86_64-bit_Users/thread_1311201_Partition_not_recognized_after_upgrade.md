---
title: "Partition not recognized after upgrade"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by dianemeeks on 2009-11-02
This problem has a history so please bear with me:
I upgraded to Karmic and was unable to boot due to an fstab error. 
I installed a clean version on a new partition and fixed the fstab file so that I could get into the upgraded partition.
Two days later, the upgraded partition froze completely.  I rebooted with same result. 
Now the clean install can no longer recognize sda1, and sda1 won't boot.
fdisk shows the partition, but gparted says it is unformatted.
Is there any way to salvage what I have on that partition?
Thanks so much.

---

### Post by bedtime_with_the_bear on 2009-11-02
> **dianemeeks said:**
> This problem has a history so please bear with me:
I upgraded to Karmic and was unable to boot due to an fstab error. 
I installed a clean version on a new partition and fixed the fstab file so that I could get into the upgraded partition.
Two days later, the upgraded partition froze completely.  I rebooted with same result. 
Now the clean install can no longer recognize sda1, and sda1 won't boot.
fdisk shows the partition, but gparted says it is unformatted.
Is there any way to salvage what I have on that partition?
Thanks so much.

Sounds like you may have a bad disk - not really anything else I can say, sorry.

However, you could try testdisk at [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) - it claims to be able to fix partition tables under some circumstances. I've never used it and don't have any experience of the author, but it is on the SysrescueCD, so can't be all bad.

If you manage to get it back, I'd strongly suggest making a goob backup and replacing the disk altogether. For what it's worth, you don't need to install a whole new copy, you should be able to do most things from the live CD.

Before you try the above, can you post the output of "sudo fdisk -l"?

If the "Id" of /dev/sda1 is NOT 83 (assuming you accepted the default partitioning or filesystem when you installed), try changing the partition type in fdisk:


[LIST]
[*]run sudo fdisk /dev/sda
[*]Type 't' to change the type
[*]Select the partition number - '1' in your case above
[*]Type the partition type - 83 for ext2/3/4
[*]Type 'w' to write and exit
[/LIST]
See if that helps.

---

### Post by dianemeeks on 2009-11-02
I was afraid of that, but I wanted a second opinion from someone who knew more than me.  Anyway, I'm going to try testdisk, but here's the fdisk output:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069387

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       76362   613377733+  83  Linux
/dev/sda2           76363      121601   363382267+   5  Extended
/dev/sda5          118846      121601    22137538+  82  Linux swap / Solaris
/dev/sda6           76363      117120   327388572   83  Linux
/dev/sda7          117121      118845    13856031   82  Linux swap / Solaris

Partition table entries are not in disk order
Thanks for your help.

---

