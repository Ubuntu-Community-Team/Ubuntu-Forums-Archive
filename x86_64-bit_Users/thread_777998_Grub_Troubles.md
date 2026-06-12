---
title: "Grub Troubles"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by nirvana21 on 2008-05-01
With the upgrade to Hardy I decided I would give 64bit a try. So I downloaded the disk, partitioned, and installed it on its own hard drive. Before when I ran Gusty 32bit, I dual booted using Grub between that and a 32bit XP soft RAID. Now when I go to boot Ubuntu  I receive error 21, something to effect of: Disk cannot be found. Grub only lists Ubuntu and Memtest without an option for XP. I do not now how to fix this. I thought maybe I could edit the path or map that it uses to locate the OS, but I am not sure how to do this. Any suggestions?

A little extra info: I know that the Ubuntu disk is sdc, also my BIOS boots to my Ubuntu disk (I have not tried to boot to my XP RAID). I did not have any others disks attached to the computer during the install.

Thanks in advance!

---

### Post by Yellow Pasque on 2008-05-01
Maybe this will help..
[http://ubuntuforums.org/showthread.php?t=767321&highlight=grub+xp+RAID](http://ubuntuforums.org/showthread.php?t=767321&highlight=grub+xp+RAID)

---

### Post by jharkn on 2008-05-02
Very useful page to do with GRUB errors and the like: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I had a similar issue and fixed it using a [Super Grub Disk]("http://www.supergrubdisk.org/").  You can find an in-depth tutorial on using it [here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk").

My problem was that when I installed Ubuntu the GRUB loader was written to the MBR with incorrect boot pointers, i.e. it was looking in the wrong place for the program to boot, even though everything was intact.  I could not boot windows or Ubuntu.

My system consists of two SATA HDDs in a fakeRaid Raid-0 array with windows and a third SATA HDD with ubuntu on it.

**FIRST MAKE SURE ALL HARD DISKS ARE ENABLED IN YOUR BIOS!!**

Basically, burn that disk and boot it as you would an Ubuntu live CD, then:

**To boot windows:**

The !WIN! option should automagically boot windows.  If it boots some windows utility partition like it did for me then reboot, highlight !WIN! and press 'e' to edit.

You should get something looking like one of these:

```
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

*OR*

title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

In my case the 'Windows XP' entry did not exist (I created it later).  To boot windows XP I highlighted:
```
root		(hd0,0)
```
pressed 'e' to edit the line,
then corrected "(hd0,0)" to "(hd0,1)".
Press enter.
Press 'b' to boot.

In your case the numbers may well be different, you should be able to guess the correct numbers, but in any case trial and error won't hurt you here.

[I]In GRUB "(hd0,0)" means:
hd0 = first hard disk
,0 = first partition of this disk

Example: replacing "root		(hd0,0)" with "root 		(hd3,2)" would boot the third partition of the fourth hard disk.[/I]

That should boot windows and reassure you that nothing is dead ;)

**To boot Linux:**

IIRC choose !LINUX! and Linux should boot, pressing 'e' with !LINUX! highlighted does a similar thing as described for the windows section, you may have to do this to edit the hard disk/partition to boot from.

**EDIT**

I just re-read your post, if you can see the GRUB boot menu then you should be able to edit it using the instructions above, but without using the super grub disk.  (highlight an entry and press 'e' to edit, then enter, then 'b' to boot)

For reference purposes the end of my my menu.lst looks like this:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a7303557-718c-4142-a9e6-0c8c92ef439b ro 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a7303557-718c-4142-a9e6-0c8c92ef439b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic (with splash)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=a7303557-718c-4142-a9e6-0c8c92ef439b ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

If you do managed to get into linux you should edit
```
/boot/grub/menu.lst
```
to reflect the changes you made to get linux/windows to boot.
Your primary objective should be to boot linux and edit /boot/grub/menu.lst to correct the root pointers/add another entry for windows.

FYI menu.lst is protected to use
```
gksudo gedit /boot/grub/menu.lst
```
in the terminal to edit it.


Sorry for the long rambling post but I hope it's of some vague use, feel free to ask for clarification :)

---

