---
title: "Gutsy 7.10 + Win XP Dual Boot Fail"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ramadhian on 2007-10-20
This is my experience with Gutsy not as smooth like Feisty

My Laptop is AMD Turion 64, grub at Feisty amd64 can make dual boot after installation successfully ..

in Gutsy ,, NTFS can be detected ,, but seems like at Grub install process , it failed to to read NTFS boot loader.

this is my current partition 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb20db20

   Device Boot      Start         End      Blocks      Id  System
/dev/hda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/hda2            4463      9729    42307177+   5  Extended
/dev/hda5            4463      5767    10482381   83  Linux
/dev/hda6            5768      5898      1052226   82  Linux swap / Solaris
/dev/hda7            5899      8509    20972826   83  Linux
/dev/hda8            8510      9729    9799618+   83  Linux

my /boot/grub/menu.lst look like this :

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9429c5b4-cf10-4e72-8f05-d88a20226314 vga=791 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9429c5b4-cf10-4e72-8f05-d88a20226314 vga=791 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           slax (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz root=current vga = 0x317 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda8.
title           slax (on /dev/hda8)
root            (hd0,7)
kernel          /boot/vmlinuz root=current vga = 0x317 
savedefault
boot


seems like Grub fail to read partition type at /dev/hda1 (which is actually there is NTFS partition there ..

---

### Post by logos34 on 2007-10-20
change this entry
> # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title slax (on /dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz root=current vga = 0x317
savedefault
boot

to this:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP 
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

