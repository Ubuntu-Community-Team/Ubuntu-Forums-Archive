---
title: "free virtulation software for ubuntu on mac?"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by shizow on 2006-02-22
is there any free virtual machine software for mac os x as a host and linux as a guest OS?

---

### Post by jdp on 2006-02-22
Try [Mac-On-Mac](http://maconmac.bastix.net/), which is the port of Mac-On-Linux to OS X.

---

### Post by shizow on 2006-02-22
[QUOTE=jdp]Try [Mac-On-Mac](http://maconmac.bastix.net/), which is the port of Mac-On-Linux to OS X.[/QUOTE]

is this really working with ubuntu?

from the website
```
Setup an Linux VM

There is currently no proper Linux support. (alpha limitation)


If you want to try it anyway you have to make sure that "Image 1" contains
the full path of the Linux Kernel you want to boot and "Image 2" the
initial Ramdisk. Don't select any boot flag. Just check the mount flags.
If your VM crashes you'll have a problem ;)

more to come...
```

this doesnt seem like a good solution
what is meant by image 1 and 2 
i never installed a virtual machine

---

### Post by flummox on 2006-02-22
Qemu [1] might be a good solution. It can emulate an x86-PC (slow), PPC (fast) and a few others.

As far as I know a prebuilt Ubuntu-VM exists somewhere too.

[1] [http://qemu.org/about.html](http://qemu.org/about.html)

flummox

---

### Post by shizow on 2006-02-22
but how does this all work, i install e.g. qemu and then i install ubuntu for PPC or ubuntu for i386?

---

### Post by george_apan on 2006-02-22
AFAIK qemu does not support virtualization by itself. You need the kqemu module for that and I believe this is only available on x86. So we're really talking about emulation here and therefore it should be about the same to use install ubuntu ppc or ubuntu x86 inside qemu. The speed should be usable but nowhere near native speeds.

---

### Post by flummox on 2006-02-23
The most easy way on OSX is to install Q[1].

It supports, experimentally, PPC virtualization thus you should try to install the PPC version. See the Q documentation[2] for further informations.

I run OpenBSD PPC within Q and it works quite well. :)

[1] [http://www.kberg.ch/q/](http://www.kberg.ch/q/)
[2] [http://www.kberg.ch/q/documentation/index.html](http://www.kberg.ch/q/documentation/index.html)

flummox

---

