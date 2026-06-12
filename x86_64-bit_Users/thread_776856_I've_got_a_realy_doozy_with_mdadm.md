---
title: "I've got a realy doozy with mdadm"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by ASULutzy on 2008-05-01
So I've got two identical disks that used to be in raid-0. Then I formatted for my switch to Ubuntu.

 Before today /dev/sda had my 64 bit hardy install and /dev/sdb had my 32 bit gutsy install. I decided that I'd like to setup a RAID-1 without having to backup everything and wipe everything and repartition and all that nonsense, and I found this thread [http://ubuntuforums.org/showthread.php?t=173058](http://ubuntuforums.org/showthread.php?t=173058) which has a couple errors in how exactly you'd do it, but seems completely plausible. So I'll list exactly what I did. (Note I don't have lvm)

Start by of course install mdadm with
```
sudo apt-get install mdadm
```
then I wiped my 32 bit gutsy drive since I never use it.
As I'm typing this I realize it may be a lot more useful to just fast forward to the present, as anyone who may be able to help me with this will understand that I've already got things pretty much set up.

Here's the output of my sudo fdisk -l
```
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

Disk /dev/sde: 2029 MB, 2029518848 bytes
129 heads, 32 sectors/track, 960 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         961     1981936    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(967, 128, 32) logical=(960, 31, 32)

Disk /dev/md0: 115.1 GB, 115112673280 bytes
2 heads, 4 sectors/track, 28103680 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

So yea, everything looks good, /dev/sda contains my hardy install, and what I did was essentially copy all of /dev/sda1 over to /dev/md0.

A quick check by mounting /dev/md0 to /raid_temp/ shows
```
ryan@ryan-desktop:/$ sudo mount /dev/md0 /raid_temp/
ryan@ryan-desktop:/$ cd raid_temp/
ryan@ryan-desktop:/raid_temp$ ls
bin    etc         initrd.img.old  lib64       opt        sbin  usr
boot   home        jdk1.6.0_10     lost+found  proc       srv   var
cdrom  initrd      lib             media       raid_temp  sys   vmlinuz
dev    initrd.img  lib32           mnt         root       tmp   vmlinuz.old
ryan@ryan-desktop:/raid_temp$ 
```
So that's all good to go. 

I've edited /raid_temp/etc/fstab to have
```
/dev/md0        /               ext3    relatime,errors=remount-ro 0      
```
I've also done ```
sudo update-initramfs -u
sudo cp -au /boot/init* /raid-temp/boot/
```
After doing all of that I rebooted, went into my grub menu and edited (hd0,0) to (hd1,0) basically switched from /dev/sda1 to /dev/sdb1
And changed the root= to root=/dev/md0

When I then boot like this my machine hangs for a while and eventually I get to a busy box prompt that tells me essentially that /dev/md0 doesn't exist.

I'm so confused. Does this have anything to do with Ubuntu's problems booting into a degraded array? Did I do something wrong?

Please help!
(Oh, and if a forum mod sees this and thinks that this may not be the best forum to get an answer to something this tricky, please by all means move it.)

Thanks in advance, this one is really bugging me.

edit: Note, my system isn't broken or anything, I can still boot into my hardy install just fine by booting to (hd0,0) but I really want to get a RAID-1 setup on these two drives.

---

### Post by futileissue on 2008-05-01
I know this isn't very helpful, but it's my understanding that the linux kernel still doesn't do very well in booting from the software raid. See that line at the bottom of your "fdisk -l" ?
"Disk /dev/md0 doesn't contain a valid partition table"

This is why your system doesn't think it exists.  Unfortunately I'm not sure there's a way to change this.  I would like to know if there is, as it would save a lot of hassle for me instead of having my boot partition not be in my RAID setup.

---

