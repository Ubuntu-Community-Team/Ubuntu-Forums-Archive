---
title: "it wont start at all"
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by jimmy2nd on 2005-12-07
when i have installed ubuntu and it has to reboot take cd out it says disk boot failure insert system disk and pres enter. got no idea why it wont work it works fine on my other comp :rolleyes:

---

### Post by gadfium on 2005-12-08
[QUOTE=jimmy2nd]when i have installed ubuntu and it has to reboot take cd out it says disk boot failure insert system disk and pres enter. got no idea why it wont work it works fine on my other comp :rolleyes:[/QUOTE]

I had a similar problem on my system which has both a SATA drive and an IDE drive. I was installing to the SATA drive but I think the boot loader was being put on the IDE drive. (Windows XP made the same mistake - maybe something in the BIOS setup is wrong). At any rate, I disconnected the IDE drive (which is there to do quick backups to) during the Kubuntu installation and everything was fine. After the installation, I reconnected the IDE drive and added it into /etc/inittab.

---

### Post by bigtom2 on 2005-12-11
my machine gets to gnom loader an it says failed i loaded it three times any 
help please

---

