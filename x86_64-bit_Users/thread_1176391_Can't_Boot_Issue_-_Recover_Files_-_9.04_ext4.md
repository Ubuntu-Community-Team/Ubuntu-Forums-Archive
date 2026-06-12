---
title: "Can't Boot Issue - Recover Files - 9.04 ext4"
date: 2009-06-02
forum: x86 64-bit Users
---

### Post by BrMBr on 2009-06-02
Hi!

I'm worried and hope someone can help me.

I use Ubuntu for some months on my notebook and never had any problems. Last Saturday I formated _ext4_ and upgraded to _9.04 x64_.

The only thing I did after installing was upgrading the system. Everything was working fine until yesterday. When I turned the computer on it just wasn't booting. GRUB loads normally and and when the system is up to loading I get a blank screen with a blinking dash on the top left. Nothing else happens.

I tried Recovery Mode and nothing happens. Also tried to mount the disk using LiveCD without luck (_**code below**_). 

I know I can solve reformating, but I have some documents and pictures inside the partition and I don't have a backup. I know, I'm a lame, but I need to recover them. Could someone, PLEASE, help me? I'm not a pro user, so any help would be very useful.

Thanks a lot!

```
root@ubuntu:/home/ubuntu# sudo /sbin/fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7d8d298

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30035   241256106   83  Linux
/dev/sda2           30036       30401     2939895    5  Extended
/dev/sda5           30036       30401     2939863+  82  Linux swap / Solaris
``````
root@ubuntu:/home/ubuntu# sudo mount /dev/sda1 /media/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
``````
root@ubuntu:/home/ubuntu#  dmesg

(...)

[13544.044136] EXT4-fs: ext4_check_descriptors: Block bitmap for group 768 not in group (block 3169060638)!
[13544.044143] EXT4-fs: group descriptors corrupted!
[15496.242468] EXT4-fs: ext4_check_descriptors: Block bitmap for group 768 not in group (block 3169060638)!
[15496.242475] EXT4-fs: group descriptors corrupted!
[15504.150784] EXT4-fs: ext4_check_descriptors: Block bitmap for group 768 not in group (block 3169060638)!
[15504.150791] EXT4-fs: group descriptors corrupted!
[15883.135418] EXT4-fs: ext4_check_descriptors: Block bitmap for group 768 not in group (block 3169060638)!
[15883.135424] EXT4-fs: group descriptors corrupted!
[16992.030400] EXT4-fs: ext4_check_descriptors: Block bitmap for group 768 not in group (block 3169060638)!
[16992.030407] EXT4-fs: group descriptors corrupted!
```

---

### Post by philinux on 2009-06-02
Sounds like you need to run fsck either from recovery or a live cd. I'm not sure how this works with ext4 though.

---

### Post by BrMBr on 2009-06-02
> **philinux said:**
> Sounds like you need to run fsck either from recovery or a live cd. I'm not sure how this works with ext4 though.

W00T!

_**You saved my life, philinux! Thanks a LOT!**_ =D>

Everything is working now and, btw, I'm posting this from my recovered partition! :D

Some lessons learnt:

[LIST=1]
[*]Always keep an external backup;
[*]Always keep a /home partition away from /;
[*]Never use ext4 (at least by now).
[/LIST]
Here is the solution:

1) ```
root@ubuntu:/home/ubuntu# fsck.ext4 -f /dev/sda1

(...found many errors. <y> to all...)

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 135285/15081472 files (0.4% non-contiguous), 3525756/60314026 blocks
```Problem found and fixed!

2) ```
root@ubuntu:/home/ubuntu# fsck.ext4 -f /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 135285/15081472 files (0.4% non-contiguous), 3525756/60314026 blocks
```Double checked. Yes, it's really fixed!!!

3) ```
root@ubuntu:/home/ubuntu# sudo fsck.ext4 -p /dev/sda1
/dev/sda1: clean, 135285/15081472 files, 3525756/60314026 blocks]
```IDK what this one did, but someone told me to do that... lol

---

### Post by philinux on 2009-06-02
Marvelous. I thought that was the problem.

Problem is, how did the system get messed up? Did you do a hard reboot for instance.

Also read this. I'm sticking with ext3 for next 6 months.
[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

You could post a thread here to find out if ext4 is ok now.
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

I didn't think 9.04 was ext4 ready.

---

### Post by BrMBr on 2009-06-05
Philinux, how the system got messed? Ask ext4's developer... And no, I never did a hard reboot, never ran off power, etc. The ext4 is really a buggy thing... :(

Anyway, I'm happy again with ext3. Never crashes!!! Ubuntu is so perfect... :KS

Well, for the next year or more I don't wanna know about ext4. :eek:

Thanks again! :cool:

---

### Post by ddales on 2009-06-07
In order to use the ext4, or any other filesystem traits, you have to touch all the files first.  The easiest way to do that is with fsck.

Boot with a live CD and do the following.

NOTE:  If you don't know already, filesystems don't like to be fsck'ed while mounted.

//Convert from ext3 to ext4:
# tune2fs -O extents,uninit_bg,dir_index /dev/xxx
# fsck -pf /dev/xxx

If you upgrade your boot partition:
# update-grub

Don't forget to change your /etc/fstab entries from ext3 to ext4.

Remount your filesystems or reboot for the changes to take effect.

To check to see if everything is in order:
# df -T
//Make sure the filesystems you wanted to use with ext4 are actually mounted that way.

I converted all my filesystems to ext4 last week and everything seems to be working perfectly.

---

### Post by BrMBr on 2009-06-09
> **ddales said:**
> In order to use the ext4, or any other filesystem traits, you have to touch all the files first.  The easiest way to do that is with fsck.

Boot with a live CD and do the following.

NOTE:  If you don't know already, filesystems don't like to be fsck'ed while mounted.

//Convert from ext3 to ext4:
# tune2fs -O extents,uninit_bg,dir_index /dev/xxx
# fsck -pf /dev/xxx

If you upgrade your boot partition:
# update-grub

Don't forget to change your /etc/fstab entries from ext3 to ext4.

Remount your filesystems or reboot for the changes to take effect.

To check to see if everything is in order:
# df -T
//Make sure the filesystems you wanted to use with ext4 are actually mounted that way.

I converted all my filesystems to ext4 last week and everything seems to be working perfectly.

Thanks for your feedback, ddales!

I won't change to ext4 for the next 6 months, as I have some "vital" data here but, please, keep us informed if you have any issue there.

):P

---

