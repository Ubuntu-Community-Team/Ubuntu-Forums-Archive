---
title: "Can't install windows XP, &quot;Can't find HD&quot;"
date: 2008-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by nvcls on 2008-03-30
I read somewhere that I should change something i BIOS, but I couldn't find that function. What to do?

Thanks

---

### Post by TenPlus1 on 2008-03-30
Your hard-drive *might* be a SATA one as Windows can only see sata drives on newer motherboard since the old one's require a driver on a floppy-disk for Windows to see it properly...

---

### Post by Roaster on 2008-03-30
Format the hard drive to NTFS. Windows will not see anything but that or fat32. Maybe??

---

### Post by paulisdead on 2008-03-30
Depending on the motherboard and chipset, you could try setting AHCI to disabled, and if it has it, compatible mode.  You unfortunately lose the ability to hotplug when you do that, also cache reads can be lower.  There are tricks if you google around on how to change to AHCI after installing windows, since if you change it later it won't boot.

---

