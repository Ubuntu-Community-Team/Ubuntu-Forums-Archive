---
title: "unable to write to /dev/sdb1"
date: 2015-10-16
forum: Wine
---

### Post by jon-zendatta on 2015-10-16
I want to defragment a Seagate external drive using Defraggler or similar software. Either Wine can't see it or I need to change permissions.
Here is some additional information
```
sudo fdisk -l
[sudo] password for j0n: 


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000aac7d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1936979967   968488960   83  Linux
/dev/sda2      1936982014  1953523711     8270849    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1936982016  1953523711     8270848   82  Linux swap / Solaris


Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disk identifier: 0x8a3e4fa9


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT

```
```
sudo blkid
/dev/sda1: UUID="67d9074b-2311-40f8-bd5c-2f1237148b25" TYPE="ext4" 
/dev/sda5: UUID="34afc06d-bd88-495d-bb6f-ad22dff133cf" TYPE="swap" 
/dev/sdb1: LABEL="Seagate Expansion Drive" UUID="8656156E56155FEB" TYPE="ntfs" 

```
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=67d9074b-2311-40f8-bd5c-2f1237148b25 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34afc06d-bd88-495d-bb6f-ad22dff133cf none            swap    sw              0       0

```

---

### Post by Bucky Ball on 2015-10-16
There are no guarantees Defraggler or any other Win fragmenting tool is going to work in Wine. Have you checked their app database to see if it runs at all? [It is rated there as 'Garbage']("https://appdb.winehq.org/objectManager.php?sClass=application&iId=10317").

If you have Windows installed, boot Windows and defrag there. If not, perhaps you could install Windows as a virtual machine and do it there. Good luck.

---

### Post by jon-zendatta on 2015-10-16
Apparently after Windows 98, it was changed to superuser. I tried using Wine Windows 98 version on various  defrag software, but all stated it requried a more recent Windows. So I think this thread is finished

---

