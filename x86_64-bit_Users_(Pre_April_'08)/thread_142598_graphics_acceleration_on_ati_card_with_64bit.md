---
title: "graphics acceleration on ati card with 64bit"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bannerboy on 2006-03-10
I have an ATI Radeon card, and a little problem. I've installed the latest drivers from ati, I had to do it manualy, but I got it installed. X works, and glxgears works just fine with a speed of 500 fps or so. but when I run fglrxinfo it tells me that I'm using MesaGL. I should be getting glxgears speeds of 8500 fps or so. what do I do in order to get it to use accelerated OpenGL?

---

### Post by jecos on 2006-03-11
I don't know why but everyone posts of ATI problems but never posts what SPECIFIC VIDEO CARD IT IS!!

---

### Post by bannerboy on 2006-03-12
It's a Radeon X900, but that shoulden't make any difference. The card is WORKING with the fglrx drivers, but MesaGL is being used for OpenGL instead of using the graphics card acceleration. I know this card will work, because I got it working under Gentoo.

---

### Post by nibbo on 2006-03-14
I got the exact same problem but i am using a radeon x800pro.

---

### Post by Bandit on 2006-03-14
[QUOTE=bannerboy]I have an ATI Radeon card, and a little problem. I've installed the latest drivers from ati, I had to do it manualy, but I got it installed. X works, and glxgears works just fine with a speed of 500 fps or so. but when I run fglrxinfo it tells me that I'm using MesaGL. I should be getting glxgears speeds of 8500 fps or so. what do I do in order to get it to use accelerated OpenGL?[/QUOTE]
Did you edit xorg to reflect the "fglrx" driver insted of the "ati" or "radeon" drivre?

---

### Post by bannerboy on 2006-03-24
yes, I did, everything seems to be set up properly, it's set to fglrd in the xorg.conf file, but it still uses the mesaGL drivers.

---

