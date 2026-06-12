---
title: "Installation advice wanted"
date: 2008-12-03
forum: x86 64-bit Users
---

### Post by Tuliku on 2008-12-03
Hi,

I would like some suggestions for my PC.

**Specs:**
Pentium Core 2 Duo E8400 3.00 GHZ
4 GB memory
2x 750 GB hard disk
GeForce 9600 GT 512MB video card

Currently it has only Win Vista 32 bit on it.

Tonight i wanna do a re-installation, and make it a dual boot with Ubuntu.

Some my questions are:
- Ubuntu 32 or 64 bit ? I did some reading here and it seems the only issue with 64 bit is the flash plugin...?
- Partitioning.. i'm not a heavy user who does a lot of rendering etc, so would 4 gb for swap be ok ? Some other suggestions are welcome also
- Is NTFS no problem anymore for Ubuntu, or is it recommended to make an extra partion in FAT32 for sharing files between Vista and Ubuntu ?
- Is there any noticeable difference between a logic and a primary partition ?
- For ubuntu, if i would make the / and /home on different partitions, can logic partitions be used ?

Most information i found here regarding partitioning is old info,  for old pc's. Not much actual info.
So all experiences with new pc's are very welcome :-)

Thanks

---

### Post by __Ryan__ on 2008-12-03
- 64-bit for sure as it will make the most out of your hardware
- 4 GB of swap is plenty, it will give you enough to suspend RAM to disk
- logical partitions are fine to use for all your uses, you only need them if you have > 4 partitions on your drive however.
- I wouldn't recommend NTFS for the Ubuntu partition, it lacks permissions and might cause a bunch of issues, I'm not even sure if it is supported. The best way is to use ext3 or similar for root and mounting an NTFS or VFAT partition where you can store your files you want to view in windows.

---

### Post by dabl on 2008-12-03
Use the Vista partitioner tool to shrink the Vista main (larger) partition (Vista is using two partitions already). Don't make any change to the small Vista partition. Since Vista uses two, you only have two more primary partitions possible.  There are some different schemes that you can use, depending on future plans.

1. One scheme:

Leave your main Vista partition large enough that you can keep shared data there.  Then, your two new partitions can be (a) small primary partition for swap, and (b) rest of the disk in a primary partition for Linux -- 10G is plenty of space.  Use ntfs-3g in Linux to access the shared data in the Vista partition.

2. Another scheme:

Squeeze Vista down as small as reasonably possible, then your two new partitions can be (a) big primary partition for shared data, format ext3, and (b) Primary/Extended partition of maybe 10G or 12G, sub-partitioned into two logical partitions (a) small one for swap and (b) the rest of it for Linux.  Then in Vista you can install ext2IFS (free) from here:

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

and use that to access the data on the shared data partition.

Hope this gives you some ideas!  :)

---

### Post by felker2 on 2008-12-03
To avoid repartitioning, you could consider Wubi, which is a part of Ubuntu that installs Ubuntu onto your Windwos-drive. When booting your computer, you can select which OS (Windows or Ubuntu Linux) to start.

See [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation) which says:

> How do I install Ubuntu?

Run wubi, insert a password for the new account, and click "install". The installation process from this point is fully automatic. The installation files (700MB) will be downloaded and checked, after which you will be asked to reboot. Do so and select Ubuntu at the boot screen. The installation will continue for another 10-15 minutes and the machine will reboot again. This is it. Now you can select Ubuntu at the boot screen and start using it. 

You can to [http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi) to download Wubi (1MB) and run it ...

Sounds great, doesn't it?

---

### Post by graysky on 2008-12-03
You can also read [this post](http://forums.debian.net/viewtopic.php?t=32648&highlight=partition).  I have the same hardware more or less as you and also wanted a dual boot setup.  Good info in there.

The long and short of it:

Disk1
Partition1 (FAT32) c:
Partition2 (NTFS) d:
Partition3 (ext3) /boot

Disk2
Partition1 (ext3) /
Partition2 (swap)
Partition3 (NTFS) e:

Download and use [gparted](http://gparted.sourceforge.net/) liveCD to resize your partitions.  It is WAAAAAY better than anything else out there.

Putting the /boot on the 1st disk is best in case your disk #2 goes down, you can still boot into windows.  Make sure you use ntfs-3g for reading/writing NTFS and you should be fine.

4 gigs of mem on my machine and I haven't gone into swap yet.  LINUX is way better than windows w/ memory management.

The max # of partitions on a drive is 4.  If you need more, you'll have to use extended/logical partitions.  There should be no difference in speed between primary and extended all things being equal.  Know that partitions on the end of the disk are slower than partitions at the beginning of the disk.

---

### Post by Yellow Pasque on 2008-12-03
> - Ubuntu 32 or 64 bit ? I did some reading here and it seems the only issue with 64 bit is the flash plugin...?
64-bit. There's now a 64-bit version of Flash and it works well for most users (though it's still an Alpha), much better than the old way of using 32-bit Flash and nspluginwrapper.

> - Is NTFS no problem anymore for Ubuntu, or is it recommended to make an extra partion in FAT32 for sharing files between Vista and Ubuntu?
ntfs-3g works well. Sometimes, getting the permissions set up correctly  (so that the partition automatically mounts/unmounts) requires a bit of effort, but NTFS is definitely the way to go. FAT32 is slower and you can't store files larger than 4GB on it.

---

### Post by LeapingLeapord on 2008-12-03
IMHO You should always stick to the 1.2 times rule for swap (in that case you would 9.6GB or 9830.4 MB of swap. as for NTFS please refer to the link below

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009).

---

### Post by graysky on 2008-12-03
> **LeapingLeapord said:**
> IMHO You should always stick to the 1.2 times rule for swap (in that case you would 9.6GB or 9830.4 MB of swap. as for NTFS please refer to the link below

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009).

Not true for LINUX at all... I have 4 gigs on my machine and have never touched the swap.  At most I've had about 1.5 gigs of RAM in use.  If you wanna hibernate, you'll need the same amount of swap as you have RAM.  You're just wasting HD space otherwise.

---

### Post by __Ryan__ on 2008-12-03
The best way to do it is skip the Swap partition all together.  You can use a swap file later if you decide you need it. 

The benefit to doing it this way is you can change the size of the swap file depending on your needs, you don't have to worry about partitions, and there are no performance drawbacks.

---

### Post by Tuliku on 2008-12-04
Everybody thanks for your advice !
Based on this and some advice from colleague's i decided to do the following:

Did the reinstalling of Vista, all went well
Did the partitioning the following way:

750 gb disk
- 100 gb: C:\vista (NTFS)(primary)
- 4 gb: / (ext3)(primary)
- 2 gb: swap (primary)
- extended partition
- 4 gb: /home (ext3)(logical)
- 4 gb: /var (ext3)(logical)
- 4 gb: /usr (ext3)(logical)
- 100 gb: D:\ (NTFS)(logical)
- Leftover GB: E:\ (NTFS)(logical)

Rebooted, grub comes up, vista works fine.
Rebooted, grub comes up, ubuntu loads, and hangs with the following screen.

-------------------------------------------
Boot from (hd0,1) ext3   (very long number)
Starting up ...
Loading, please wait...
usplash: Setting mode 1152x864 failed
usplash: Setting mode 1024x768
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/79cdc601-497e-4d85-98c2-9bb99fb21072) = dev(8,3)
kinit: trying to resume from /dev/disk/by-uuid/79cdc601-497e-4d85-98c2-9bb99fb21072
kinit: No resume image, doing normal boot...
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have  /sbin/init
No init found. Try passing init= bootarg

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
-------------------------------------------

Reinstalled it, and same screen again...
Where did i go wrong....?

---

### Post by Tuliku on 2008-12-04
This kinda pisses me of, decided to do now a 3rd install, but differently:

The plan is as following:

750 gb disk
- 100 gb: c:\ vista (ntfs)(primary)
- 15 gb: ubuntu (ext3)(primary)
- 4 gb: swap (primary)
- extended partition
- 100 gb: d:\ (ntfs)(logical)
- leftover gb: e:\ (ntfs)(logical)

Back in half hour with the results.

---

### Post by Tuliku on 2008-12-04
Ok, this worked, now running happily Ubuntu.

Still curious thought why the previous setup didn't work..

---

### Post by felker2 on 2008-12-04
> **Tuliku said:**
> Ok, this worked, now running happily Ubuntu.

Still curious thought why the previous setup didn't work..

What was the order of installation? First Vista, then Ubuntu (which is good), or first Ubuntu, then Vista (which is bad).

---

### Post by Tuliku on 2008-12-04
First i formatted the harddrive completely, then in the vista installer created the 100 gb partition for vista, and installed vista. Then with paragon partition manager created the other partitions, and installed ubuntu, and reagrding which mount on which partition i did the "manual" option in the ubuntu installer.

When it didn't work, i booted again into vista, used partition manager to delete the linux partitions, and made them new, and installed again..

---

### Post by dabl on 2008-12-04
I don't see an ext3 partition bigger than 4GB in the original partitioning.  That is not large enough for a Ubuntu OS installation -- that's probably why it couldn't boot.

---

