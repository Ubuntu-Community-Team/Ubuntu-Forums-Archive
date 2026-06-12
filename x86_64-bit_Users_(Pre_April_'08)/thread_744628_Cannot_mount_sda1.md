---
title: "Cannot mount sda1"
date: 2008-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Plasmonic on 2008-04-03
Ive got Ubuntu installed as a dual boot with Windows XP but when i select Windows for booting i get the error that hal.dll is corrupt or missing. I understand that i need to edit the boot.ini file but have not been successful in mounting sda1, where XP is. When i try

sudo mount /media/sda1 /media/windows
I get
mount: /media/sda1 is not a block device

I used "fixboot" in the recovery console off the XP install CD but it didnt help.

I need my HL2 fix NOW!!! Please help!

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       10340    83047986    7  HPFS/NTFS
/dev/sda2   *       10988       14410    27495247+  17  Hidden HPFS/NTFS
/dev/sda3           10341       10987     5197027+  83  Linux
/dev/sda4           14411       14593     1469947+  82  Linux swap / Solaris

Partition table entries are not in disk order

I just saw the similar threads pop up but i cant read them at the moment, ill check those later.

---

### Post by pseudo-random on 2008-04-03
What bootloader are you using? GRUB or window$?
If you used fixmbr then the window$ one will have overwritten it.
You can play HL2 in Ubuntu under wine.

---

### Post by mrsteveman1 on 2008-04-03
Fdisk can fix the partition order but sometimes it causes problems with certain OS.

Have you run chkdsk on the partition? I think its in the recovery console in the XP cd

---

### Post by Plasmonic on 2008-04-04
i found the windows partition "Local Disk". Its either because of a restart after trying to mount or the fixboot command.

My boot.ini file in windows root was missing so i used BootCFG /rebuild to recreate the file. The new file correctly points to the first partition and i found hal.dll in  c:\windows\system32
But it still cant find hal.dll. When bootcfg asked for the "load name" i used "xp" and 1 for the option.

btw i have an intel core2duo not amd

---

### Post by Plasmonic on 2008-04-04
I think it was Partition Magic that removed boot.ini.But in my other ntfs partition the boot.ini still exists. Heres both boot.ini files and the end of menu.lst. 


        from windows partition
[boot loader]

timeout=20

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="xp" 1


        from backup partition
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


menu.lst

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

I will try renaming the boot.ini in the backup partition.

---

### Post by Plasmonic on 2008-04-04
i got xp  to work after renaming the boot.ini in the backup partition, now to figure out how to recreate it cause i cant access it!

:lolflag:

---

### Post by autowiz on 2008-04-07
Congratulation, You solved the problem.

Additional information. 

Look :
> Device    Boot Start End    Blocks          Id System
/dev/sda1            2 10340 83047986    7  HPFS/NTFS
/dev/sda2 * 10988 14410 27495247+ 17 Hidden HPFS/NTFS
/dev/sda3    10341 10987 5197027+   83 Linux
/dev/sda4    14411 14593 1469947+   82 Linux swap / Solaris

Windows bootloader recognize partions by physical position(start cylinder).

So, ntldr sort like this sda1, sda3, sda2, sda4.

have a good day, bye by~

---

