---
title: "New Ubuntu kernel crashing on auto-disk fsck"
date: 2006-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by petriborg on 2006-06-17
Hi all,

I installed the new Linux kernel image for version 2.6.15-25 on x86_64 today, and when I rebooted it crashed/hung when it tried to do an automatic disk check with fsck. I checked /var/log but didn't anything interesting for /dev/sd*

Luckly, it was doing this only on my secondary drives and not the drives that support the kernel or user directories!
I had to unplug the harddrive and change the fstab settings from 2 to 0 so that it would skip the checks at boot. Now I'm worried that when my primary drives gets around to the next disk check that it will hang too.

So with that said, has anyone else had this problem?

stats:
dapper 6.06, completely up to date
4 SATA drives
AMD64
Neo2 MSI mobo
nvidia 6800 gfx


--
pete

---

### Post by petriborg on 2006-06-17
On a side note, does anyone know how, or maybe have a link to the best way to  manually use fsck to do a disk check? Some sites suggested booting to a LiveCD and then "just do it" but a little more detail would be required imho :-)
--
pete

---

