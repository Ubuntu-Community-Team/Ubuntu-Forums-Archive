---
title: "Unresolved graphics card issue"
date: 2009-08-13
forum: x86 64-bit Users
---

### Post by dark_angel_akira on 2009-08-13
Hello!

I have a problem with my newly upgraded ubuntu 9.04 (wel, actually, it was an issue in my 8.10.) When i shutdown my pc or try to hibernate, the computer screen turns black, flickers and crashes for some reason. It also happens when i press CTRL + ALT + F2 (or any console)

I'm using an ACER Aspire 4520. 64x2 turion processors and a GeForce 7000M. I have tried installing the drivers from NVIDIA website, the one from Xorg and even EnvyNG. All of them were installed successfull and were working fine(in terms of graphics modes or compiz), except for that issue. I can't shutdown or hibernate or go to console. It doesn' happen in VGA mode so i think it's got something to do with the driver or something. I'm still kinda new and learning the Linux way. ^_^

I have been trying all sorts of things and ideas from guides all around the net(maybe i just missed it if there is anything that can solve this and i've ran out of ideas).. still hasn't solved this problem.

Many thanks in advance!

---

### Post by dark_angel_akira on 2009-08-13
please marked as solved. i was reviewing one of the items in my tabs... and yes, it was the answer. hurray for me! 

^_^

the answer was removing the "splash" option in grub menu.lst and changing it with vga=791. ^_^

---

