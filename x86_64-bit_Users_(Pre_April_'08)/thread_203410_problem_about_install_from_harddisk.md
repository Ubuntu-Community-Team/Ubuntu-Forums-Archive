---
title: "problem about install from harddisk"
date: 2006-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by applepark on 2006-06-25
Hi,all:

I download the .iso file in /dev/hda5 and I want to install ubuntu from disk.So when I reboot the PC and when grub shows I pressed c, then I input:

grub>kernel (hd0,4)/vmlinuz root=/dev/ram ramdisk_size=256000 
devfs=mount,dall
grub>initrd (hd0,4)/initrd.gz
grub>boot

but it says as follows:
[I]RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/I]

any idea?

p.s.Why it always stopped at 36% and then no response when I install using a desktop cd?

thanks!
Specs:
AMD Athlon64 2800+
ASUS  nForce 4
1GB DDR 
160 GB IDE HDD (One has a WinXP install, the other is for Linux)

---

