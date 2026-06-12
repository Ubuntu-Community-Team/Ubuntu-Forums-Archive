---
title: "System Freeze on window move"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by LunarEffect on 2009-04-24
Hey guys, I searched the forum and couldn't find any related issues (I hope I did it thoroughly enough, if not, I'm sorry)

I'm having the following issue:

The system starts and runs fine, but at random times, when I click in the title bar of a window and attempt to drag it, the system freezes completely. Not even ctrl+alt+f1 will work. I had this problem under Ubuntu 8.10, but thought I'd wait for 9.04 to see if its fixed.

Anyway, heres my system stats:
AMD Phenom 9850
ATI Radeon HD3870, 512 mb
4GB Ram
Ubuntu 9.04

I'm using the fglrx driver provided by the Hardware Driver menu, under 8.10 I was using the driver from the ATI website.

Thank you for any answers in advance,

Regards, 

LunarEffect

---

### Post by LunarEffect on 2009-04-24
Ok, I've made another observation: Before I install fglrx, my windows can be dragged around smoothly, with fglrx however, the movement becomes choppy and slower.

Does anyone know a solution to this?

---

### Post by djBo on 2009-05-13
Hi forum,

Unfortunately I am experiencing the exact same problem described by LunarEffect.

The system boots perfectly fine, and is completely usable. However, I experience the freeze-up usually in the first five minutes of using it...
Once I have been able to move a window without a problem, the problem does not return in that session.

System specifics:
Ubuntu 8.10 Desktop
AMD Athlon X2 6400+
4Gb RAM
SAPPHIRE HD 3870 Ultimate 512M
Using latest ATI's fglrx driver

Looking at the specs of LunarEffect, I can see that the problem occurs in both 8.10 and the latest 9.04. He has the same vidcard (from the looks of it) & amount of system memory...

My best bet would be to blame the fglrx driver, but I have no idea on how to check this... if I "remove" my xorg.conf the video doesn't come up anymore... I've even tried using the vesa driver (without success)...

Any idea's are still welcome :D
Bo

---

