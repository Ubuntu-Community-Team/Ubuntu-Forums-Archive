---
title: "Hardy upgrade = SLOW system"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by shadowplane676 on 2008-05-09
ok, i have an HP zv6000 laptop with:
2GB ram
AMD64 4000+ CPU
80GB IDE HDD
ATI 200M Integrated Graphics

I originally was running feisty x64, but decided to upgrade to gutsy, and a couple weeks after that, upgrade to Hardy. Now my system is running WAY slower than it did in ether gutsy or feisty. Burning a CD or DVD takes up to 3 times as long with the buffers (both software and device) in K3b depleting continuously. Burning a CD or DVD also hangs my system so bad, i cant really do anything at all while its burning. I never had these problems with feisty/gutsy.

I also have had mount errors on boot as apparently Hardy doesnt like my fstab file from before. Could any of these be causing such abnormally godawefully slow system/hdd access issues?

---

### Post by philinux on 2008-05-09
Have you checked top to see if anything obvious?

---

### Post by shadowplane676 on 2008-05-09
htop doesnt show anything obvious. When burning, it hits 100% due to k3b and X, other slowness doesnt really show up on htop. hdparm returns 

Timing buffered disk reads:  112 MB in  3.01 seconds =  37.22 MB/sec

so the drive itself ISNT slow, its hanging somewhere in the system.

---

### Post by philinux on 2008-05-09
Hard to say whats causing this. 

My gut feeling is this.
1. Backup home. Double check it.
2. Put it on its own partition.
3. Do a clean install without formatting /home

Maybe someone can come up with something simpler.

---

