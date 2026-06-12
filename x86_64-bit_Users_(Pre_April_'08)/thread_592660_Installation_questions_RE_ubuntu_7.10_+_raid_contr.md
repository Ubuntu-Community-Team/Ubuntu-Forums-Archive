---
title: "Installation questions RE ubuntu 7.10 + raid controller"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by SimonHF on 2007-10-26
I've got the following setup: Intel Core Duo + 4GB RAM + WinXP + 4x 400GB drives; two of these drives are mirrored for secure-ish backups etc, and two of these drives are in a stripes for booting and running XP fast.

I am attempting to install Ubuntu 7.10 as a dual boot and I have the following plan to do this:
Step #1. Boot from the Ubuntu 7.10 DVD into 'Live' mode
Step #2. Use gparted to shrink the WinXP partition in order to create room for a boot partition for Ubuntu 7.10

Step #1 works fine. In step #2 then gparted only 'sees' one unformatted 400GB drive instead of one NTFS 800GB drive and one NTFS 400GB drive. How can I get gparted to recognize the raid drives?

(I've checked in other forums for P5B mainboard with jmicron raid controllers and messages seem to suggest that problems with this combination only existed up to kernel versions 2.6.17...)

---

