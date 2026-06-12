---
title: "kernel in grub"
date: 2006-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by InvIsiBlekID on 2006-06-22
ok, so i have ubuntu 6.06 amd64 bit installed on my laptop, it works just fine :-\" , but my question is, since software availibiliy is somewhat low for the amd64 version, would it be possible to install the 386, or some other kernel to boot it in 32 bit? i dont really understand much about kernels, but i dont see where a problem would be, i just dont want to screw up my 64 bit install.

thanks in advance!

---

### Post by RAOF on 2006-06-22
No.  You've all 64bit libraries and stuff.  They won't run under a 32bit kernel.  Although 32bit stuff will run under your 64bit kernel.  What you'd have then is a chroot (where you essentially install a 32bit system **inside** your existing setup).  

The problem with software availability is not the kernel, it's all the libraries and stuff.

Alternatively, you **could** keep your /home, and install Dapper32.  That'd keep your config 'n' stuff.

---

### Post by InvIsiBlekID on 2006-06-22
yea after i posted i kinda thought about that, thanks much for your help tho! :D

---

