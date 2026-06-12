---
title: "Unable to make changes to data on Hard Disk!!!"
date: 2007-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by nik_nmn on 2007-11-05
I am unable to save or make any changes to data saved to my hard disk. I cannot even make changes to the properties of songs on rhythm box.  I cannot save anything to hard disk at all. 
Error message reads " You do not have permissions to write to this folder " "Read only File system".
System Details
Dual Boot - Ubuntu Feisty Fawn 7.04 and Win XP SP2.
AMD Athlon 2800+ (64 Bit).
512 MB RAM.
Swap 512MB
80GB SATA 7200Rpm HD. (6 partitions, 10GB for Ubuntu, 8GB for WinXp, 20GB * 3 data storage partitions.)
Please help with this issue. Thanks in advance.

****Note: I am using Ubuntu since 2 months almost, experienced this the first time"******

---

### Post by dcstar on 2007-11-06
> **nik_nmn said:**
> I am unable to save or make any changes to data saved to my hard disk. I cannot even make changes to the properties of songs on rhythm box.  I cannot save anything to hard disk at all. 
Error message reads " You do not have permissions to write to this folder " "Read only File system".
System Details
Dual Boot - Ubuntu Feisty Fawn 7.04 and Win XP SP2.
AMD Athlon 2800+ (64 Bit).
512 MB RAM.
Swap 512MB
80GB SATA 7200Rpm HD. (6 partitions, 10GB for Ubuntu, 8GB for WinXp, 20GB * 3 data storage partitions.)
Please help with this issue. Thanks in advance.

****Note: I am using Ubuntu since 2 months almost, experienced this the first time"******

Most likely some file system corruption has caused an error and the mount has reverted to Read Only mode for it's own protection.

An fsck on the partition and a reboot will (usually) fix this.

---

