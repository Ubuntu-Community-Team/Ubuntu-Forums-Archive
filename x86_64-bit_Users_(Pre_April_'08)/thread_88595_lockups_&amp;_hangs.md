---
title: "lockups &amp; hangs"
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by yohan on 2005-11-10
I am running ubuntu 64 bit 5.10 and recently ive been experiencing a lot of lockups where everything freezes and I can only move my mouse horizontally and not vertically. Music works but I cant do anything...closing anything with shortcuts or trying to close X doesnt work either.

im using flgrx, radeon 9800 amd 64 3200+ and this happens when im running firefox32 on through my chroot. Im not 100% sure about why these lockups happen but i cant remember not being in firefox at the time...

help!

---

### Post by yohan on 2005-11-10
actually 5 seconds after i wrote that i had another lockup and had to reboot....i was scrolling at the moment, maybe that has something to do with something?

anyways help please!

---

### Post by AndersAA on 2005-11-10
try not using fglrx, also try not using 32bit.

it could be either just fglrx, or fglrx in combination with your chroot.

and make sure the chroot is using the same fglrx libs as your 64bit system does.

---

### Post by yohan on 2005-11-12
ive now installed 32bit fglrx drivers on my chroot and 64 ones on my system. Both are 8.19.10 and they seem to work fine. I also tried firefox 64bit with no problems so it must have to do with my chroot and 32bit...the only difference i see when using 32bit version is that my cursor is different? why is that?

---

