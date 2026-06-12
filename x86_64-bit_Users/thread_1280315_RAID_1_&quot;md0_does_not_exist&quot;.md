---
title: "RAID 1 &quot;md0 does not exist&quot;"
date: 2009-10-01
forum: x86 64-bit Users
---

### Post by Zizuph on 2009-10-01
User: I've only been learning Linux for about six years, so please bear with me if I make mistakes.  I did much Googling prior to posting this, but if the answer is already here somewhere, my apologies.  Lastly, I hope I chose the correct category to post this type of problem.

Hardware
Gigabyte MA785G-UD3H, AMD 64 X2 Dual 2 GHz, 4GB DDR2 800, GeForce 8400 GS 512.

Software
root@server:~# uname -a
Linux server 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

Goal
To turn two new identical drives (sdc1 & sdd1) into a software RAID 1 mirrored array for data storage.

Problem
Each time the machine is reloaded from scratch, I am able to create the array, format it to ext3, and mount it.  Following the first reboot, md0 no longer exists and one of its constituent components is in use and cannot be manipulated without going to a live CD to wipe them out and start over.

Note: Already disabled onboard fake raid and ran apt-get remove dmraid.  All OS updates have been rerun following the last reload of the system.  Each time I reload the system, I am careful to format sda1 for a fresh OS, avoid overwriting and mount sdb1, and recreate the partitions on sdc1 & sdd1.  RAM and all drives have been thoroughly tested for defects using UBCD utilities.  The motherboard has been flashed to the latest BIOS.  All drives are securely connected with new SATA cables.

Following is another attempt...

*****
root@server:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00050968

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  83  Linux
/dev/sda2           18237       19457     9807682+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006bdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000774fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006c55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

*****
root@server:~# mdadm --verbose --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=488384000K  mtime=Thu Oct  1 01:06:08 2009
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Thu Oct  1 16:56:34 2009
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=488384000K  mtime=Thu Oct  1 01:06:08 2009
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Thu Oct  1 16:56:34 2009
mdadm: size set to 488383936K
Continue creating array? yes
mdadm: array /dev/md0 started.

*****
root@server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdd1[1] sdc1[0]
      488383936 blocks [2/2] [UU]

unused devices: <none>

*****
root@server:~# mkfs -t ext3 /dev/md0
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122095984 blocks
6104799 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

*****
root@server:~# mkdir /raid

*****
root@server:~# mount /dev/md0 /raid

*****
root@server:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            144181428   3544752 133312648   3% /
tmpfs                  1995992         0   1995992   0% /lib/init/rw
varrun                 1995992       224   1995768   1% /var/run
varlock                1995992         0   1995992   0% /var/lock
udev                   1995992       168   1995824   1% /dev
tmpfs                  1995992       520   1995472   1% /dev/shm
lrm                    1995992      2560   1993432   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb1            976760000 394536696 582223304  41% /windows
/dev/md0             480718992    202796 456097000   1% /raid

*****
root@server:~# ls /raid
lost+found

*****
O.k.  So, its working.  Now, to reboot...

*****
root@server:~# mount /dev/md0 /raid
mount: special device /dev/md0 does not exist
root@server:~#

*****
Why?
Thanks for taking the time to read this.

---

### Post by raygj on 2009-10-01
use the alternative installation CD.during installation when you get to partitioner section as well as creating,formating & setting your md0 as "/" create a small separate non-raid partition,format & set it to be the "/boot" folder and mark its boot flag.after completion of installion ,when you reboot the grub program will then find and load the linux kernel in "/boot" with it's "raid drivers" which will find and use "md0"(/) for the rest of bootup into your desktop.

---

### Post by sloggerkhan on 2009-10-01
Do you have an entry in your fstab?
Have you saved the RAID configuration in the appropriate file?
```
# /dev/md0
UUID=5e08f7bb-5d9d-4f9d-91ef-1f8ec6535e43 /media/blah  ext3    relatime
```

I believe once you create the array, you have to permanently save config and then add it to fstab.

Without a saved raid config and appropriate entry, system will not know to look for sw raid on reboot.

---

### Post by Zizuph on 2009-10-01
I installed using the server CD a couple of times yesterday.  That allowed me to use the raid GUI and configure everything.  Still, after running updates and rebooting, md0 was gone.  I haven't tried the alternate install CD yet, but I imagine that uses the same tool.  I've been setting up "/" and boot on a separate hard drive altogether.

---

### Post by Zizuph on 2009-10-01
Could you help me find the steps to take to save that information in the correct file?  As for fstab, I figured I would do that once mount /dev/md0 /raid starts working.  Or, am I thinking wrong?

---

### Post by sloggerkhan on 2009-10-01
md0 will only exist if you have a saved /etc/mdadm/mdadm.conf file.....
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=50ec52d5:459d4856:3d5b301a:d527d2ca

# This file was auto-generated on Sun, 01 Mar 2009 07:23:50 +0000
# by mkconf $Id$

```

mdadm should have an option for writing this when you create the array.

---

### Post by Zizuph on 2009-10-02
I think we're making progress!  After reading that last post, I found some info on how to generate the file and did this...

mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

After that, I rebooted, and check this out...

root@server:~# mount /dev/md0 /raid
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by sloggerkhan on 2009-10-02
sounds like you're getting somewhere, might need some sort of special command or mount options to mount it. Likewise, even once you make the md device, you will have to format it, so it's possible you've just created the device and it does not yet have a filesystem.

---

### Post by Zizuph on 2009-10-02
OMG yes!  I forgot to format after that last step.

root@server:~# mkfs -t ext3 /dev/md0
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096624 blocks
6104831 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 29 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@server:~# mount /dev/md0 /raid
root@server:~# ls /raid
lost+found

*****
Now, lets see what happens after reboot...

---

### Post by Zizuph on 2009-10-02
Thanks so very very much.  This forum rocks.  I love Ubuntu.  Problem solved.

---

### Post by Zizuph on 2009-10-02
I just noticed the following warnings/errors in my fdisk -l output.  Can anyone tell me why I'm getting these?  md0 appears to be functioning correctly.

root@server:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00050968

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  83  Linux
/dev/sda2           18237       19457     9807682+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006bdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/md0: 500.1 GB, 500107771904 bytes
2 heads, 4 sectors/track, 122096624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

---

### Post by Zizuph on 2009-10-02
Found the answer.  Posting it here for anyone else who runs across this...

Somehow in preparing my drives, I had created partition tables with no partitions in them.  Not sure how that could have happened.  But, the end result is that after creating partitions on both drives and md0 and rebooting, the problem went away.

1st Question: However, fdisk -l now lists md0 as md0p1.  Yet, fstab still mounts it successfully as md0.  Not sure what that means.

2nd Question: Also, not sure if I was supposed to add tables to the physical drives as well as the managed disk.  Perhaps someone can answer that.

---

### Post by sloggerkhan on 2009-10-02
don't know about 1st question, but w/respect to 2nd question, an md device can be made from combinations of partitions or from physical disks, so it's kind of your call. At least if I'm understanding what you mean properly.

PS: If you didn't set a custom chunk size when you built your array, you might want to redo it. Last I built an array, the default chunk size was ridiculously small.

---

