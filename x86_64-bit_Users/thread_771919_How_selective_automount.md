---
title: "How? selective automount"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by vikrant_me on 2008-04-28
I would like to automount only a few of my partitions, not all, below are the required files:

fdisk -l:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c3d2c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          19      152586   83  Linux
/dev/sda2              20          38      152617+  83  Linux
/dev/sda3              39          57      152617+  83  Linux
/dev/sda4              58        9729    77690340    5  Extended
/dev/sda5              58        1925    15004678+  83  Linux
/dev/sda6            1926        3793    15004678+  83  Linux
/dev/sda7            3794        5661    15004678+  83  Linux
/dev/sda8            9450        9729     2249100   82  Linux swap / Solaris
/dev/sda9            5662        6966    10482381   83  Linux
/dev/sda10           6967        9448    19936633+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e1639ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        3265    26218076+   7  HPFS/NTFS
/dev/sdb2            3266        9729    51922080    5  Extended
/dev/sdb5            3266        9729    51922048+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaeb9764b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              14       30401   244091610    f  W95 Ext'd (LBA)
/dev/sdc2   *           1          13      104391   83  Linux
/dev/sdc5            2612       27778   202153896    b  W95 FAT32
/dev/sdc6           27779       30401    21069216    7  HPFS/NTFS
/dev/sdc7              14         300     2305264+  82  Linux swap / Solaris
/dev/sdc8             301        2611    18563076   83  Linux


fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=0f5959a2-7c92-498a-9349-d62f4bf770c0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=d2d5ece1-463e-4d70-8924-f4a139331cd4 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=e705e1d6-3398-465d-bf7c-b7d3e632186b none            swap    sw              0       0
# /dev/sdc7
UUID=ed60c027-c868-49d3-92d6-fc3c89493fbb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

mount -a:

vikrant@vikrant-desktop:/$ sudo mount -a
vikrant@vikrant-desktop:/$ mount
/dev/sda9 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda2 on /boot type ext3 (rw,relatime)

---

