---
title: "Please help me with my grub!!!"
date: 2007-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigdidz on 2007-12-17
Ok, first I'm not like you I only have one computer at home.  And unfortunately now, it is only running under Ubuntu7.10 and I have a kernel panic.  Like nobody helped me on my last [thread]("http://ubuntuforums.org/showthread.php?p=3954409"), I'm calling back for help!!!

I NEED MY COMPUTER!!!

I would like to know who to repair my grub menu.lst .  I think it is maybe the problem.  Nevertheless, if you know how to help me with my kernel panic, feel free.

And, do not forget that the only way I found to get on my computer is from my Ubuntu live-cd.  I have nothing else.

Thanks in advance

Long live Windows!

---

### Post by rasta_freak on 2007-12-17
Looks like your /boot/grub/menu.lst is f*cked up, specificly "root" option - which tells initrd (ram image that is started when kernel is loaded, but before main system stuff starts to boot) where is your main (root) filesystem.
Can you bring up grub menu when you start your comp (or is it displayed by default) ? I think it's with shift key, or try ctrl.
When in menu, press "e" key  - to edit boot options, and position yourself on longest line that has "root=" / quiet / splash ... words in it. On it press again "e" to edit it. Now replace "root=" option:
if your linux is on first hard disk, and it's on first partition,
option will be /dev/hda1 or /dev/sda1,
if it's on second disk, try /dev/hdb1 or /dev/sdb1,
if it's on other partition (if you have windows too), it will be /dev/hda5 or /dev/sda5 or /dev/hdb5 or /dev/sdb5  or ... - you notice how disks go, i guess.
So in grub, add/replace line with "root=/dev/hda1", press enter than "b" to boot it. if you booted ok, you must edit /boot/grub/menu.lst and make same changes there to make it permanent. Try "sudo update-grub; sudo update-initramfs -u" - maybe if it's smart enough, it will do it for you :)

---

### Post by bigdidz on 2007-12-17
first, thanks a lot for your help.

when I try to edit my grub (when I press 'ESC' , 'e' and 'e' ) I'm getting in front of a monstrosity:
```

grub edit> kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ddf2edd-c4b4-4e6f-ba2a-cffc450adefd ro quiet splash
```

then I tried to replace all the 'UUID=7ddf2edd-c4b4-4e6f-ba2a-cffc450adefd' by '/dev/hda1' (because I thing is that.  I have the simplest system; ubuntu 7.10 for 64-bit and nothing else ) and it still cannot load.  The same 'kernel panic'.

Do you know if there is a way to do the command lines but via the cd?

Thanks again

Didier Amyot

---

### Post by logos34 on 2007-12-17
from the live cd, mount your root partition:

-Places>computer>root partition (double-click to mount.  It will mount at '/media/disk/.  Click on it to open. Either go to /boot/grub folder or do this in a terminal:
[B]
sudo gedit /media/disk/boot/grub/menu.lst[/B]

Post it.

And post 

**sudo fdisk -l **

too.

One more thing:

**ls /media/disk/boot**

will show if vmlinuz- and initrd.img- are there.

---

### Post by bigdidz on 2007-12-17
I sould give you 20$ for your help :)

here is my grub file ( without the comments)

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ddf2edd-c4b4-4e6f-ba2a-cffc450adefd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ddf2edd-c4b4-4e6f-ba2a-cffc450adefd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```


here is the answer for "sudo fdisk -l"

```

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfbadfba

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11975    96189156   83  Linux
/dev/hda2           11976       12161     1494045    5  Extended
/dev/hda5           11976       12161     1494013+  82  Linux swap / Solaris
```

and here is the answer for "ls /media/disk/boot"

```

abi-2.6.22-14-generic             initrd.img-2.6.22-14-generic.dpkg-bak
config-2.6.22-14-generic          memtest86+.bin
grub                              System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic      vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
```

millions thanks for your help, I'm learning at the same time!

Didier Amyot

---

### Post by logos34 on 2007-12-17
Your files look in order.  Can't spot any errors. You say you've tried 'root=/dev/hda1' on kernel line and it doesn't help, so that's not it.  Unless vmlinuz- or initrd.img files have gotten corrupted somehow...maybe that's causing the kernel panic. dunno.

According to fdisk, hda1 is root and so hd0,0 should work.  What does 

/media/disk/boot/grub/device.map 

show? (should be just your one hard drive listed)

---

### Post by logos34 on 2007-12-17
run a filesystem check:
[B]
sudo e2fsck -y -f -v /dev/hda1[/B]

---

### Post by rasta_freak on 2007-12-17
Try booting with grub entries:

kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro init=/bin/bash noinitrd

to see if you need any special driver for your HDD.
BTW, did you edit/change your initrd (did you ever do update-initramfs) ?
Did you change your BIOS settings?

Oh, and while in liveCD, try:

sudo umount /media/disk
sudo fsck -f /dev/hda1

just to make sure filesystem is ok.

EDIT:
in grub, also delete line with initrd (press DEL (or d ?) on it) to make sure "noinitrd" has an effect.

---

### Post by bigdidz on 2007-12-17
I did everything you asked me, and I still have the (more or less) error.

/media/disk/boot/grub/device.map
I only have one hard drive: (hd0,0)

the filesystem test was okay

I changed the kernel like you said and it shows the same error.

Can I reinstall Ubuntu by creating a new partition, copy my files into the new partitions and merge the two partitions?  But if do it, I will like to go back to Ubuntu 32bit.  If you think that is doable why not?

---

### Post by logos34 on 2007-12-17
> **bigdidz said:**
> Can I reinstall Ubuntu by creating a new partition, copy my files into the new partitions and merge the two partitions?  But if do it, I will like to go back to Ubuntu 32bit.  If you think that is doable why not?

it's doable.  32-bit no prob.  But if you create a space after the existing root and reinstall there, then copy over your files, you'll have to use the gparted live cd -- version 0.3.4-- because then you want to delete the original root and reclaim the space by dragging the slider to the left (can't resize on the left using the gparted version included with ubuntu).

what the heck could be the problem, though.  I'm outta ideas.  maybe rasta_freak has some other suggestions you could try before you reinstall.

---

### Post by uidb4056 on 2007-12-17
Looking at the result of 'ls /media/disk/boot' it seems that somenthing has changed your 'initrd.img-2.6.22-14-generic' because there is also a previous version 'initrd.img-2.6.22-14-generic.bak', you know some action that can change this file?, may be renaming 'initrd.img-2.6.22-14-generic' to other name and reverting 'initrd.img-2.6.22-14-generic.bak' to 'initrd.img-2.6.22-14-generic' let you to boot again.

Another thing you can check is from Live CD run on the terminal the command 'blkid' this will show you your partitions with the current UUID of each one, then you can compare with what is listed in menu.lst if they are different you can try to replace the UUID value showed in menu.lst with the current value from blkid.

---

### Post by rasta_freak on 2007-12-18
If that before doesn't work (copying initrd.bak over initrd in /boot),
well, if I were you, I'd boot from liveCd, mount original partition, and then:
- if you have USB flash stick with enough capacity for your stuff (you can compress files so on 1GB stick should fit a lot of your stuff) - then
 make a new directory on original partition, copy there all that you need to preserve, make tar+gzip archive out of that, (tar -cvf data.tar .; gzip -9 data.tar) 
(you can skip gzip if you don't need to compress it)
and then copy(move) that arhive to USB flash, and restore it after fresh/clean reinstall, OR
- if you don't have any USB stick, reformat swap partition to ext3 (sudo mke2fs -j /dev/hda5; sudo mount /dev/hda5 /mnt) and put there (in /mnt) your files (compress them if you need to), unmount partition (sudo umount /mnt), launch installer, tell installer not to touch that partition ("swap" one), not to use swap, install everything as usual, and after you boot it, restore your files (mount /dev/hda5 /mnt, copy from /mnt where you want, umount /mnt), then add this to /etc/fstab:
/dev/hda5 none swap sw 0 0
then:
mkswap /dev/hda5
and then
swapon -a
and make a check with:
free
(it should show swap usage)
(BTW, use sudo for each of these command)

---

