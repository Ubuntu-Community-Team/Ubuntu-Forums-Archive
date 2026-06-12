---
title: "HELP Setting up RAID-1 on an already running system"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by ASULutzy on 2008-05-02
Has anyone been able to do this? Been trying for the past week to setup a degraded array to boot from and then let mdadm automatically rebuild it... 

I am able to setup partitions with fdisk, able to create /dev/md0 with mdadm, setup the file systems, mount /dev/md0, copy everything over from /dev/sda1 (my current install partition) to /dev/md0 using sudo cp -ax / /raid_temp/, edit fstab, mtab, grub, run update-initrafms... Once I get everything done if I attempt to actually boot from /dev/md0 the ubuntu progress bar bounces back and forth for a while and eventually gives up saying it can't find /dev/md0 and falls back to a busy box prompt.

Has anyone been able to setup a RAID-1 on an already existing system? Note, I don't have LVM.

I'd be very appreciative if anyone who has been able to do this could guide me through it. Thanks in advance!

---

### Post by ASULutzy on 2008-05-02
bump because I have bad forum etiquette:lolflag:.

---

### Post by fjgaude on 2008-05-02
Okay, when you boot from your other disk, can you mount /dev/md0?

There has been some few who have done what you wish but not me. It can be done if all the steps are carried out correctly.

Can you mount /dev/md0?

---

### Post by ASULutzy on 2008-05-02
I'm starting over with attempting to do it. My problem was that I could not boot from the other disk after copying everything over... Hold on a sec and I'll detail each step I go through, one because it'll be easier to see where I went wrong, and two, if it works this'll turn into a HOWTO guide! :)

---

### Post by ASULutzy on 2008-05-02
Ok, I'll start by explaining my system in its current state.
```
ryan@ryan-desktop:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G   32G   69G  32% /
varrun                2.0G  120K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   88K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G   43M  1.9G   3% /lib/modules/2.6.24-16-generic/volatile
/dev/sdc1             466G  360G  107G  78% /media/Big drive
```
Here's fdisk -l
```
ryan@ryan-desktop:/$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x227629b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc2b0d66

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b5c7aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b0a4b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4864    39070048+   7  HPFS/NTFS
```

sda is my current Hardy 64 install, sdb is an identical hard drive that is currently not formatted. I begin by copying over the partition table from sda to sdb as root
```
root@ryan-desktop:/# sfdisk -d /dev/sda | sfdisk /dev/sdb
Checking that no-one is using this disk right now ...
OK

Disk /dev/sdb: 14593 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0       -       0          0    0  Empty
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63 224829674  224829612  83  Linux
/dev/sdb2     224829675 234436544    9606870   5  Extended
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5     224829738 234436544    9606807  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```
I can verify this worked by doing sudo fdisk -l which shows me that sda and sdb have the same exact partition tables. Now I want to change sdb's table from Linux partitions to linux raid autodetect partitions, so I use fdisk. After repartitioning those drives my fdisk -l looks like
```
ryan@ryan-desktop:/$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x227629b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc2b0d66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112414806   fd  Linux raid autodetect
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  fd  Linux raid autodetect
........
```
Now I have to zeroout my superblock on sdb since I failed the first time at doing this, but most people won't have to do this part.
```
ryan@ryan-desktop:/$ sudo mdadm --zero-superblock /dev/sdb1
ryan@ryan-desktop:/$ sudo mdadm --zero-superblock /dev/sdb5
```
Now I need to actually make the RAID.```
ryan@ryan-desktop:/$ sudo mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/sdb1
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=112414720K  mtime=Wed Dec 31 19:00:00 1969
Continue creating array? yes
mdadm: array /dev/md0 started.
ryan@ryan-desktop:/$ sudo mdadm --create /dev/md1 --level=1 --raid-disks=2 missing /dev/sdb5
mdadm: array /dev/md1 started.
```
In order to verify that worked I do```
ryan@ryan-desktop:/$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb5[1]
      4803328 blocks [2/1] [_U]
      
md0 : active raid1 sdb1[1]
      112414720 blocks [2/1] [_U]
      
unused devices: <none>

```Next I need to go ahead and setup the file systems on that RAID.```
ryan@ryan-desktop:/$ sudo mkfs.ext3 /dev/md0
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
7028736 inodes, 28103680 blocks
1405184 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
858 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
ryan@ryan-desktop:/$ sudo mkswap /dev/md1
Setting up swapspace version 1, size = 4918603 kB
no label, UUID=2193be90-fa31-4c30-b895-78b7ee3fd213
```
Ok, so now I just need to mount /dev/md0 somewhere and copy over my existing filesystem.```
ryan@ryan-desktop:/$ sudo mkdir /raid_temp
ryan@ryan-desktop:/$ sudo mount /dev/md0 /raid_temp/
```
Next I need to edit my fstab accordingly with sudo nano /etc/fstab```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
#UUID=f480cccf-8a38-426b-be9f-6af3a5912443 /               ext3    relatime,errors=$
# /dev/sda5
#UUID=833d3ea1-898c-4cf7-8016-7071383a484c none            swap    sw              $
/dev/md0        /               ext3              relatime,errors=remount-ro    0  $
/dev/md1        none            swap      sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


``` Noticed how I change /dev/sda1 to /dev/md0 and /dev/sda5 to /dev/md1. And now I need to change mtab with sudo nano /etc/mtab. You'll obviously want to make backups of both mtab and fstab before doing this stuff. But basically I want to change /dev/sda1 in mtab with /dev/md0```
/dev/md0 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdc1 /media/Big\040drive fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4$size=4096 0 0
```Ok, so now I need to switch up my grub so it'll boot off the degraded array. So I add the following to my grub with sudo nano /etc/boot/grub/menu.lst```
title           Ubuntu hardy (development branch), RAID     
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet
``` Almost done now, I need to make those updates do something so```
ryan@ryan-desktop:/$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
```Now all I have to do is copy stuff over.```
ryan@ryan-desktop:/$ sudo cp -ax / /raid_temp/
``` Which takes a while... So I'll get back to this post once it's done.

edit: as this is copying, does anyone see any huge problems with what I've done so far? It all seems to make sense to me?

edit2: ok it's done copying. Now there's only 1 more step before I can test if this works, I need to setup a boot loader on /dev/sdb so ```
ryan@ryan-desktop:/$ sudo grub
[sudo] password for ryan: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ryan@ryan-desktop:/$ 
```

From here, all you should have to do is the following:
```
mount --bind /proc /raid_temp/proc
mount --bind /sys /raid_temp/sys
mount --bind /dev /raid_temp/dev
chroot /raid_temp
grub-install /dev/md0
exit
```

---

### Post by ASULutzy on 2008-05-02
Yikes, so I haven't rebooted yet... But a quick look at /etc/mdadm/mdadm.conf shows the following, which doesn't look right to me at all...```
ryan@ryan-desktop:/$ cat /etc/mdadm/mdadm.conf
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

# This file was auto-generated on Wed, 30 Apr 2008 15:59:15 -0500
# by mkconf $Id$
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=431c9e21:349cbc9f:d919d176:d92b132e
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=9f07aab3:1dec7914:d919d176:d92b132e
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=da98d5d0:6d71beee:d919d176:d92b132e
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=431c9e21:349cbc9f:d919d176:d92b132e
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=3e9201b8:fbdc6e80:d919d176:d92b132e
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=89497e42:0c8f852a:d919d176:d92b132e

```

Looks like way too many entries to me!
Anyone got any ideas?

---

### Post by fjgaude on 2008-05-02
Can you mount /dev/md0 and /md1?

What does **sudo mdadm -D /dev/md0** look like?

---

### Post by ASULutzy on 2008-05-02
So I got home and tried to reboot, it would not boot from the grub entry for hd1,0 but I was able to boot from the old grub entry... But what's weird is that df -h says```
ryan@ryan-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              106G   32G   69G  32% /
varrun                2.0G  124K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   84K  2.0G   1% /dev
devshm                2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G   43M  1.9G   3% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      106G   32G   69G  32% /home/ryan/.gvfs
```
And the output of what you asked is ```
ryan@ryan-desktop:~$ sudo mdadm -D /dev/md0
[sudo] password for ryan: 
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Apr 30 20:06:14 2008
     Raid Level : raid1
     Array Size : 117220736 (111.79 GiB 120.03 GB)
  Used Dev Size : 117220736 (111.79 GiB 120.03 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Apr 30 20:08:06 2008
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 431c9e21:349cbc9f:d919d176:d92b132e (local to host ryan-desktop)
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       16        1      active sync   /dev/sdb
```

edit: and yes I can mount /dev/md0, I already copied over all of / (which is /dev/sda1) to /raid_temp/ (which is /dev/md0)

edit2: whoa... check out my fdisk -l```
ryan@ryan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x227629b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc2b0d66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112414806   fd  Linux raid autodetect
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b5c7aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/md0: 120.0 GB, 120034033664 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc2b0d66

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1   *           1       13995   112414806   fd  Linux raid autodetect
/dev/md0p2           13996       14593     4803435    5  Extended
/dev/md0p5           13996       14593     4803403+  fd  Linux raid autodetect

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b0a4b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4864    39070048+   7  HPFS/NTFS
```
edit3: And apparently my swap didn't get raided? I'm so confused```
ryan@ryan-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb[1]
      117220736 blocks [2/1] [_U]
      
unused devices: <none>

``` What happened to /dev/md1???

---

### Post by fjgaude on 2008-05-02
I would delete my mdadm.conf file and then:

```
sudo mdadm --assemble --scan
```

and see what I get.

Maybe the two drives sda and sdb haven't been sync'd up yet.

I tell you, why so few have done what you try is one of philosophy: it is easy to install an OS but it is difficult to re-create data. I never try to boot from a raid, hardware or software, but always have a big raid for data and always backup that data to another drive or two on other machines. Think about it.

I know you can boot from a software raid1 if you have boot loaders and stage1 grub on both drives... but now think when one drive fails you have to go through what you are trying to do now. Wow!

Just my thoughts, coming from others with 20 years of experienve running servers, and my own of about three years of mdadm raid experience.

---

### Post by ASULutzy on 2008-05-02
Well, I know that sda isn't in the raid as I haven't added it yet.

And I'm well aware of the advantages and disadvantages to a RAID and how a RAID does not equate to backing up. I do backup important data, but I would also like to protect against hardware failure as I do have storage to spare (just got a 1TB eSata drive)

I'll try deleting the config and resetting it.

edit: Oh, I misunderstood what you wrote there. You're saying just boot from a single drive and RAID your data.
Yea that's smart... I just feel like I'm so close right now that I stubbornly want to finish lol

---

### Post by ASULutzy on 2008-05-02
I backed up my /etc/mdadm/mdadm.conf (thankfully) and when I delete it this is what happens. ```
ryan@ryan-desktop:~$ sudo mdadm --assemble --scan
mdadm: No arrays found in config file
```

---

### Post by fjgaude on 2008-05-02
Okay, let you get it up and running and then make that HOW-TO. I'm sure many others could, will use the knowledge.

Oh, I don't think anyone ever got a raid1 swap working, to my knowledge. <smile>

---

### Post by ASULutzy on 2008-05-02
One last question, when my 1TB hard drive gets here, will it be any easier to just backup everything to there, create a RAID-1 with the two hard drives I want to now, and then copy back? Or am I pretty much looking at a clean install in order to get this working?

---

### Post by fjgaude on 2008-05-02
> **ASULutzy said:**
> One last question, when my 1TB hard drive gets here, will it be any easier to just backup everything to there, create a RAID-1 with the two hard drives I want to now, and then copy back? Or am I pretty much looking at a clean install in order to get this working?

Well, yes and no... you'll have to learn something like dd to do the copying... else if what you backup is just data, that's easy with cp or Nautilus, etc.

---

### Post by ASULutzy on 2008-05-03
I should be syncing the two disks momentarily... I got a friend of mine a real linux guru to ssh to my box and fiddle... Added a grub entry to /dev/md0 and some other stuff... But yea, it IS possible, just very very very tricky. And booting from a degraded array can be a monstrous headache.... But if you're paranoid about drive failure, you can in fact install raid-1 on a system that already has an OS running without formatting everything first... Though I wouldn't recommend it unless you're 100% sure that's what you want.

---

### Post by ASULutzy on 2008-05-03
He tells me he did the following from where I left off with my howto guide```
mount --bind /proc /raid_temp/proc
mount --bind /sys /raid_temp/sys
mount --bind /dev /raid_temp/dev
chroot /raid_temp
grub-install /dev/md0
exit
```

Want to know what makes me happy?```
ryan@ryan-desktop:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[2] sdc1[1]
      112414720 blocks [2/1] [_U]
      [=>...................]  recovery =  8.5% (9620736/112414720) finish=38.4min speed=44581K/sec
      
unused devices: <none>
```

---

### Post by fjgaude on 2008-05-03
Yes, I would say you are on your way. Wonderful!

Trust you will finish up a HOW-TO now that you have it all down.

---

### Post by ASULutzy on 2008-05-03
Yep, of course.

Later today I'll come back and change the "I have no clue what I'm doing" tone of the post and make it more how-to-ie!

---

### Post by keld on 2008-05-11
There is a howto on preventing against a single disk failure at [http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk](http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk)

This inludes booting from different drives, having swap mirrored, so you will not crash with a sudden disk error, and getting best preformance out of your disks, while also getting the redundancy with raid.

---

### Post by fjgaude on 2008-05-11
> **keld said:**
> There is a howto on preventing against a single disk failure at [http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk](http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk)

This inludes booting from different drives, having swap mirrored, so you will not crash with a sudden disk error, and getting best preformance out of your disks, while also getting the redundancy with raid.

Thanks for the interesting, useful link... many can learn from going through such expereinces...

---

