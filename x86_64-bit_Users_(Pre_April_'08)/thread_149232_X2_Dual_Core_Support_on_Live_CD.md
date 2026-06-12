---
title: "X2 Dual Core Support on Live CD"
date: 2006-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by douirc on 2006-03-23
Does the latest version of the Live CD offer dual core support?  From what I can gather the answer is no, but I'm a complete noob at this, so any answers on this are greatly appreciated.

thanks!

---

### Post by nife on 2006-03-23
I don't think so.  But an easy way to tell is to open a terminal and then

cat /proc/cpuinfo

If there are two almost identical entries in there then the kernel sees the X2 well. I just installed and I had to install the smp kernel to get it to work correctly.

---

### Post by allupinya on 2006-03-27
Last nite at home i downloaded the breezy live 5.10 64 bit..It booted right up and got all my hardware to install as oem...worked well on amd x2 4200+ and asus A8V m/b with 2 gig ram...Install went perfectly as well...

---

### Post by kakashi on 2006-03-28
oh nothing will go wrong in the install. only that onoly one core is seen. you need to install the smp kernel to use the second core.

---

