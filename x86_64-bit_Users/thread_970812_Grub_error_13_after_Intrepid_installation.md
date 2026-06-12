---
title: "Grub error 13 after Intrepid installation"
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by kaprikawn on 2008-11-04
Hi,

I've had a dual boot Hardy Heron and Vista installation which worked fine.  I tried upgrading my Hardy to Intrepid and it didn't work.  So I hosed my Hardy installation and did a fresh install of Intrepid (all 64-bit versions for the Ubuntu installations).  And now grub won't load Vista since the upgrade/fresh installation of Intrepid.  I get the following error:

> Error 13: "Invalid or unsupported executable format"

I've tried a few suggestions from google searches and none have worked so far.  So could someone point me in the right direction please?

The important part of my /boot/grub/menu.lst file is:

> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		861d359b-ae01-42f8-aaee-01f15cd5d014
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=861d359b-ae01-42f8-aaee-01f15cd5d014 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		861d359b-ae01-42f8-aaee-01f15cd5d014
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=861d359b-ae01-42f8-aaee-01f15cd5d014 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		861d359b-ae01-42f8-aaee-01f15cd5d014
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

My fdisk -l output is:

> 
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dfb5adc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2   *         244        3890    29294527+  83  Linux

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9add9ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4501    36149248    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07394df0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdd: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       61760     3952623+   b  W95 FAT32


My Vista installation is on sdb 37 gig drive.  However, before, when my installations were working correctly, I tried to unplug the sdc 200gb HDD.  This made Vista unbootable which leads me to think that some Vista boot files may have been installed on that drive.  Could this mean that I need to point grub to that drive instead for Vista to boot?  If so, what would I need to put in the menu.lst file?  Or if I'm completely wrong, how do I fix whatever the problem is?

Any help gratefully accepted.

Thanks in advance.

---

### Post by TryHarder on 2008-11-04
In  my humble opinion you trying to boot here:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0) <<here
savedefault
makeactive
chainloader +1 

your sda1 partition which is Linux/Swap partition (I can be wrong, so before making any suqqested changes - backup files). Try to change this entry to (hd1, 0) or whenever you have your Vista installed, but from following output I guess its not hd0, 0.

---

### Post by caljohnsmith on 2008-11-04
If you are booting the sda drive on start up, then using one of the following entries for Windows should work:
```
title	   Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows Vista (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
Give that a shot, and if none of the above entries work, please let me know exactly what happens when you try each of them from the Grub menu. Otherwise let me know how it goes.

---

### Post by TryHarder on 2008-11-05
Can you please tell me the reason that he should map every option with hd0? Can't understand this.

---

### Post by unutbu on 2008-11-05
Windows expects itself to be installed on the first hard disk. That is, the hard drive that the BIOS lists first. 

In kaprikawn's case, the BIOS boots the Ubuntu hard drive first. So Ubuntu is on (hd0). But since Windows want to be on (hd0), you tell GRUB to swap the meaning of (hd0) and (hdX) right before chainloading Windows.

Since we are not sure what number X the BIOS is assigning to the Windows drive, caljohnsmith listed all possibilities.

See [http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

---

### Post by caljohnsmith on 2008-11-05
> **TryHarder said:**
> Can you please tell me the reason that he should map every option with hd0? Can't understand this.
If he is booting from the Linux sda drive on start up, that then is (hd0) to Grub, and his Windows is not on the same drive Linux; Windows must be on either sdb1, sdc1, or sdd1 (he didn't say which). Therefore, Windows would be on either (hd1), (hd2), or (hd3), but not (hd0). And to boot Windows from any drive that is not the first boot drive, you have to use Grub's "mapping" technique to fool Windows into thinking it is on the first boot drive (hd0), or Windows normally will not boot. That's why all the entries I gave are mapped to (hd0). Of course that all assumes he is booting from the sda drive on start up; if not, then Windows might be the first boot drive (hd0). 

I hope I explained that clearly enough, but feel free to ask any more questions. :) If you are interested, a few good resources to read more about Grub are:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

