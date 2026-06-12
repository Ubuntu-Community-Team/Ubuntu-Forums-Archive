---
title: "Wine on Breezy-64? Or in chroot32?"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-28
I have tried my damnedest to be a purist, but it turns out I need Visio (no, Kivio can't do it). I'm pretty sure Visio runs under Wine, but I can't figure out how to install Wine. Synaptic lists wine-doc only. Not sure why it lists only the documentation -- not very useful without the software.
I also have a chroot envionment where I run Firefox32, RealPlayer, Flash and Adobe Reader 7.0. I opened Synaptic32 within the chroot environment, but it doesn't list Wine at all.
So where's the Wine?

---

### Post by skylark on 2006-01-29
Yeah, at the moment you have to run it from your chroot.

From my chroot:```
$ apt-cache showsrc wine
Package: wine
Binary: libwine, wine-dev, libwine-dev, wine
Version: 0.0.20050725-0ubuntu1
Priority: optional
Section: universe/otherosfs
```So I think it is in "universe". 

So make sure you have breezy universe enabled in your chroot: /etc/apt/sources.list

To do this: 
1. from a terminal type: dchroot
2. sudo nano /etc/apt/sources.list
3. Look through it and change it so universe lines are uncommented

Then in synaptic you should be able to update the list of packages and see wine.

---

