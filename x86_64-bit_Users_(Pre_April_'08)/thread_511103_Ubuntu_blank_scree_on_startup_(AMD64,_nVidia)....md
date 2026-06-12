---
title: "Ubuntu blank scree on startup (AMD64, nVidia)..."
date: 2007-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by seguro on 2007-07-27
Hi, there! 

I'm newbee to Lnx. But for 15 years using Win I have had it!!! Want to be Ubuntu usr :P

I've red and tried many posts from here about this problem, but haven't found any solution which I could apply to my case.

After installing Ubuntu 7.04, when system starts, screen goes blank. Do not work ctrl+alt+F1 etc.

In GRUP I've got only 2.6.20-15 kernel. No -16... 

Tried to delete xorg.conf, to run dpkg-reconfigure... Nothing helps :(

My box is: AMD X2 64 6000+, 2Gb RAM, eVega NVIDIA 8800 GTS, wide 22" screen.

Need your help, I'm really desperate and thinking 'bout Fedora (which is working allright on my box). But I want to use Ubuntu...

BR, Seguro:confused:

---

### Post by darknightuk on 2007-07-27
well know bug wit lots of solutions search for it

---

### Post by cprofitt on 2007-07-27
You need to edit your grub menu.lst and change the following:


> 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f0a01578-d1e4-44bd-835f-f58ea47f81b3 ro quiet splash


to

> 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f0a01578-d1e4-44bd-835f-f58ea47f81b3 ro quiet


Its a bug that has been around for several versions in Ubuntu -- why I am testing Debian right now. I love apt-get, but can't deal with some of the minor annoyances that are present in Ubuntu.

---

### Post by seguro on 2007-07-27
Thank You!!! It's Alive :)

---

