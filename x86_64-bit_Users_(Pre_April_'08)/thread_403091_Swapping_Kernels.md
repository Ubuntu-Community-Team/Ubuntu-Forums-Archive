---
title: "Swapping Kernels"
date: 2007-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brian Boyko on 2007-04-06
Is it possible to install a second, x64 kernel on my existing x86 Linux installation - and have it allow me to choose which kernel to load at GRUB bootup time?  x86 is more stable, but I would like to have x64's speed when I know I'm going to be doing something really processor intensive, such as multimedia editing or compiling.

---

### Post by kidders on 2007-04-06
Hi there,

There's a lot more to running a 64-bit OS than installing a 64-bit kernel. What you're describing is *possible*, but wouldn't work ... at least not in the terms you used.

To make it usable, you'd effectively wind up with two Linux installs. If I were you, I would just do that. Another alternative would be to do what most do, and create a 32-bit chrootable environment, so you can swap from one bitness to the other more easily. Having said that, there are some situations where having two entirely seperate OSs is preferable (or even necessary).

---

### Post by Brian Boyko on 2007-04-06
Thanks.  I'll stay with x86 for now then.

---

### Post by Kilz on 2007-04-06
> **Brian Boyko said:**
> Is it possible to install a second, x64 kernel on my existing x86 Linux installation - and have it allow me to choose which kernel to load at GRUB bootup time?  **x86 is more stable,** but I would like to have x64's speed when I know I'm going to be doing something really processor intensive, such as multimedia editing or compiling.

That is not the truth. x86 is not more stable on 64bit hardware. You are talking like there is some flaw in the 64bit version.

---

### Post by ffxr on 2007-04-07
you could probably set up a dual boot setup by just installing from an AMD64 ubuntu disc, as long as you have supported hardware..

i have been using 64 bit ubuntu for a few months now, and once you have ironed out a few minor setup issues.. its rock solid & and runs 'just like' a i386 machine.

---

