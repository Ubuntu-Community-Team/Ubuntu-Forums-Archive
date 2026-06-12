---
title: "[SOLVED] issue with mdadm: remove old arrays, create fresh"
date: 2008-09-30
forum: x86 64-bit Users
---

### Post by maxxum on 2008-09-30
Hi,
My first attempt at trying to RAID two 1TB disks (mirroring RAID1) was not successful. I ended up creating a /dev/md0 array of two unformatted devices /dev/sdb and /dev/sdd. Then I tried to "fail" both of them and removed the /etc/mdadm/mdadm.conf and uninstalled mdadm, and then reinstalled it. I created an ext3 partition /dev/sdb1 and /dev/sdd1 on each of the disks. Upon reinstallation, I see that mdadm still sees md0 array and I tried to create md1 using those new partitions but it is not functional. 

First, can anyone help me get rid of md0 array? Based on reading other threads, I was able to remove the /dev/sdd from md0 but cannot remove /dev/sdb.
```

max@ubu64:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Sep 30 02:06:29 2008
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Sep 30 13:27:32 2008
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : da5b76a4:a7e677b8:a5bc6dde:58f52177 (local to host ubu64)
         Events : 0.22

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       0        0        1      removed

```
```

max@ubu64:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/max/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=max)

```
```

max@ubu64:~$ sudo mdadm  /dev/md0 --fail /dev/sdb
mdadm: set /dev/sdb faulty in /dev/md0
max@ubu64:~$ sudo mdadm  /dev/md0 --remove /dev/sdb
mdadm: hot remove failed for /dev/sdb: Device or resource busy

```
According to 'mount' command, the sdb is not mounted. Why is it busy?

Let me also post the fdisk output:
```
max@ubu64:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc1d4e14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       20668   151364430   83  Linux
/dev/sda3           20669       21397     5855692+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009dbe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5173    41552091    7  HPFS/NTFS
/dev/sdc2            5174       18688   108559237+   5  Extended
/dev/sdc3           18689       19452     6136830   82  Linux swap / Solaris
/dev/sdc5            5174        8360    25599546   83  Linux
/dev/sdc6            8361       10402    16402333+  83  Linux
/dev/sdc7           10403       15501    40955904    7  HPFS/NTFS
/dev/sdc8           15502       18688    25599546   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009dbe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

Disk /dev/md0: 1000.2 GB, 1000204795904 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009dbe7

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      121601   976760001   83  Linux

```

Once I have a clean set of drives back again, I will ask for help with building a fresh array.


EDIT: I am not sure what I did but apparently I got it to work. Let me write down for anyone who might be stuck, like I was. 
First, I stopped the md0 array, then reset the superblock of sdb (somehow it worked this time) and after restart, I see that the md0 has both sdb1 and add1 as members of RAID1. I had labeled md0 to BKUP using
```
sudo e2label /dev/md0 BKUP
``` and out it in /etc/fstab in order to automount it. All I needed to do is change the ownership to myself and I can write files to the BKUP media. To test, I put a small file on to it.
Now to test if it is really writing to both the drives I booted into Windows XP, used ext2ifs to mount the drives and saw that small file was written to both the drives. Good. Now I put another small file from XP on to one of the two drives. Booting back into linux it shows both files in the /media/BKUP though I am not sure if it was written to both drives. I guess I could check by booting back into XP.

---

