---
title: "Help required for Install 64 bit in addition to existing 32 bit"
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by Euphorion on 2008-07-24
Hallo

I plan to install Ubuntu 64 in addition to my Ubuntu 32 Bit in order to perform a soft migration as advised in this Forum. As I also have Vista installed and Boot using EasyBCD the question that I am facing is how will repartitioning affect Grub and my current beautifully setup Ubuntu 32 Bit.

Currently I have the following Setup on a Fujitsu XI-2550 Laptop.

The first Harddisk contains the Vista recovery partition and Vista.
The second Harddisk contains 3 Partitions:
The first partition contains a common Data Area
The second partition contains Ubuntu 32 Bit
The third partition contains Ubuntu swap
Grub is in Harddisk 2 Partition 2 (hd1,1) (required by EasyBCD

I now want to insert a new partition between the common Data Area and Ubuntu 32 in which to install Ubuntu 64 Bit.

I can imagine that this will move Ubuntu 32 Bit to Partition 3 along with Grub (hd1,2), my current Menu.lst references hd1,1 .

When installing Ubuntu 64 I will instruct the installer to use Partition 2 and share the swap with Ubuntu 32 Bit and will Install grub in the new Partition 2 (hd1,1).

My Questions are the following:

1. is this feasible ?
2. How do I tell Ubuntu during install to share the Swap, use existing swap partition
3. Will I have to edit Grub in order to boot the 32 bit version and if yes what must I edit and what must I modify. I assume menu.lst and change hd1,1 to hd1,2
4. Will the 2 Grubs collide

Naturally I will have to reconfigure EasyBCD.

When modifying the Partition data I will use Gparted from a boot CD. I would like to avoid the other alternative that springs to mind and that would be to move the 32 Bit Partition forward so that it remains partition 2 (hd1,1) but then how will the 32 bit version know that its swap partition is partion 4 and once again will Grub be affected as all relevent boot data has physically moved. To safeguard against calimity I have saved everything to an external Hard Disk using Acronis True Image.

Thanks in advance

---

### Post by oraldlight on 2008-07-24
I spent the better part of 3 weeks trying to dual boot 32+64bit Ubuntu (8.04) on my laptop and gave up becasue of UUID#'s for drive with common data files. There were also difficulties getting grub to share like name files.

  It may work, I got close, but it was just over my head as to how to make it reliable.

  The sequence of partitions should not matter so long as it is consistent. Leaving them alone is understood (makes Windows happy), but not a priority.
  
  Backing up is a good thing.

---

### Post by Cappy on 2008-07-24
1) Yes
2) Use manual partitioning and pick /swap as a mount point and pick the partition for it.
3) Yes. You'll need to edit whichever grub is being used. If you install grub while installing the 64-bit then you'll need to edit menu.lst to boot the 32-bit ubuntu. 

To have 32-bit use swap you'll need to edit /etc/fstab. UUIDs change when you repartition. 
```
ls -l /dev/disk/by-uuid/
```
will list each partition's UUIDs. It's possible to mount by partition name (hda1, etc) rather than UUID if it becomes a problem.
4) No, only one will be used.

Honestly, it's my opinion that you should just install 64-bit. If you use a 64-bit live CD you'll see it's almost the same as 32-bit.

The 32-bit and 64-bit will not be able to share a swap partition if you plan on hibernating btw. Suspending (Suspend to RAM) will work fine though.

---

### Post by Sef on 2008-07-24
> Honestly, it's my opinion that you should just install 64-bit. If you use a 64-bit live CD you'll see it's almost the same as 32-bit.

Agreed.  Almost all 32-bit apps have a 64-bit counterpart.  If you do need to use a 32-bit app, there are ways to install it under a 64-bit system.

---

### Post by Euphorion on 2008-07-25
Thank you all for your replies and valuable help.

One of the reasons I like Ubuntu is simply the community through which one can learn an awful lot about computing.

The UUID Numbers was something completely new to me, never knew that such a table existed.

All in all I will have to seriously consider migrating to 64 Bit, and "bite the Bullet" with regard to reinstalling my Programmes and resolving the ATI Video Driver issues (flgrx).

---

