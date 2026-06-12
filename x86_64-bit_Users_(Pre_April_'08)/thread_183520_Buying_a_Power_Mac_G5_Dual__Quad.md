---
title: "Buying a Power Mac G5 Dual / Quad"
date: 2006-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by codix on 2006-05-28
Hi guys,

is the graphic card in the power mac series of apple supported by ubuntu linux? 

Or which graphic cards are supported on the PowerPC plattform?

Another question is: Does ubuntu supports the quad-core processor and uses all the cores for calculations?

Thanks!

---

### Post by ssam on 2006-05-28
ati cards tend to be better supported by open source drivers, but you should probably look up specific cards.

---

### Post by darcyb on 2006-05-30
The Live CD of the latest RC doesn't work on my Dual Core G5 2GHz. It starts loading the OS, runs the fans full speed, goes to a black screen and then hangs requiring a forced restart.

---

### Post by kellogs on 2006-05-31
well, not all ATI cards work well even with Dapper.
Im using a powermac G5(dual) with radeon 9600 ati card. 

All the tutorials from ubuntu recommends using Xorg drivers, other people says the Fglrx propietary ones.

What I find humorous is that free Xorg ati drivers do not have 3d acceleration in MACS (Dri/Drm problems) yet even in dapper as of today's date.

And the fglrx drivers are NOT available  for powerpc macs. Ati did not made this architecture.

So if you have a mac and linuxppc and something newer than ati 8000 range cards, the best you can do is wait for a dapper fix or a Xorg drivers fix, as I dont think ATI is going to release new drivers for this specifical platform.

---

### Post by darcyb on 2006-06-01
I've got an NVD 6600LE.

---

