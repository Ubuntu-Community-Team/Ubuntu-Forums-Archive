---
title: "x86 packages on AMD64 server"
date: 2006-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by grough on 2006-10-09
I am currently running the i386 version of Ubuntu server on an AMD64 machine.

I installed the AMD64 Ubuntu when I first got the machine, but had big problems installing some packages. To save myself the hassle and time, I installed the x86 version, and everything has been running smoothly ever since.

I don't know much about this stuff, so forgive me if this is a stupid question:

Since the x86 version will run happily on the AMD64 platform, I'm wondering if it's possible to install an AMD64 version of Ubuntu server, specify that x86 packages should be installed by default, and optionally force 64-bit software installs if there would be a worthy performance improvement.

Is it possible for the OS run in two modes like this? For example, would it be possible to run 32-bit Perl, and 64-bit Ruby on the same Ubuntu install?

Thanks

---

### Post by kuja on 2006-10-09
Well, you can use a 64-bit install, and force in 32-bit packages as necessary, but you can't do it the other way around. (the other way around being a 32-bit install forcing in 64-bit packages)

---

### Post by grough on 2006-10-09
What is the easiest way to force 32-bit package installs in synaptic?

---

### Post by Kilz on 2006-10-09
> **grough said:**
> What is the easiest way to force 32-bit package installs in synaptic?

[I wrote a small howto on]("http://www.tghc.org/staticpages/index.php/32bitapplications") installing 32bit applications in 64bit. It is not possible to use synaptic to install 32bit applications on a 64bit system.

Exactly what applications were hard installing onto a 64bit server?

---

