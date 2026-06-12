---
title: "USB Creator &amp; BOOT ERROR"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by john_navarro on 2008-11-15
Using Intrepid 64-bit to create a bootable flash drive results in BOOT ERROR when attempting to boot from the device. I verified that the .ISO was valid by booting it from within Virtual Box.

What fixed this issue was reformatting the USB stick using FAT32. The device was originally formatted in FAT16. I am now able to boot from the USB device without problems.

---

