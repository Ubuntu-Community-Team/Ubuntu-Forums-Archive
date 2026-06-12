---
title: "Can't boot into Windows (Dual Boot)"
date: 2005-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by snapmando on 2005-06-23
Ok, I am running a dual boot system on 2 Hd's.

SATA Drive is Windows XP formatted in NTFS
IDE Drive is formatted with Ubuntu 64 Bit

I installed Windows first on the SATA Drive, Then installed Ubuntu on the IDE Drive.

I rebooted, and the Bootloader showed Windows Xp.

My problem is I can't get into XP, Ubuntu boots up fine.

When I try to boot into Windows I get this and the system just hangs........

Booting 'Microsoft Windows Xp'
Root (hd 1,0)
Filesystem Type Unknown, Partition type 0X7
Save Default
Make Active
Chainloader +1

Now Linux is (hd0) /dev/hda
Windows   is (hd1) /dev/sda

Any Ideas on my next move, to get this working?
Please speak Noobish to me, as I am a sqweeky clean Noob......

Thanks

---

### Post by Digitallysick on 2005-06-24
Check your bios, make sure your first and second harddrives are showing up in the correct order, and not on "auto" that fixed the problem for me

---

### Post by dirtydan on 2005-06-24
> Now Linux is (hd0) /dev/hda
 Windows is (hd1) /dev/hda 

This looks strange to me, they shouldn't both be /dev/hda. I've got Win2k on a SATA drive and it's identified as sda.

---

### Post by snapmando on 2005-06-24
dirtydan my mistake, you are correct.

I edited my original post.......

---

