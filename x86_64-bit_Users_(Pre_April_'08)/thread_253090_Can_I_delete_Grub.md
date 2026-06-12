---
title: "Can I delete Grub?"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeescott on 2006-09-07
After I flashed my bios, Grub will not load. I also cannot get the Ubuntu live cd to load. If I go into the bios and change the sata and pata to compatible from enhanced, everything loads fine. The problem there is when I change this setting in the bios, my 74gb Raptor drive with 64bit Windows disappears. Ubuntu is on a 320gb WD sata drive and 32bit Windows is on a 300gb Maxtor pata drive. They both seem to work ok in this setting, but I have to change the bios to get into 64bit Windows. Does anyone know why this is happening or how to fix it?

---

### Post by mikeescott on 2006-09-08
Now Grub will not load at all and I cannot get into 32bit Windows. I need to scan some paperwork and I can't get to my scanner. I keep getting "Error 17" when Grub tries to load and Ubuntu keeps hanging up on "Mounting root file system". I tried 32 and 64 bit Ubuntu cds and neither will load. Can I delete or alter Grub somehow so I can get around it and into Windows? Please help. Thnaks, Mike

---

### Post by hizaguchi on 2006-09-08
Sounds like your harddrives just aren't getting along.  I know nothing about sata and I've never heard of pata, so I have no clue how to help you with that.

For a quick fix, you could probably put grub on a bootable floppy or USB drive and manually fill out your boot options.  That would probably get you into Windows to use your scanner, since you wouldn't be relying on a drive that connects in any funky way (IDE/sata/pata).

---

### Post by maubp on 2006-09-08
PATA = Parallel ATA, is the new name for IDE.  I think.

---

