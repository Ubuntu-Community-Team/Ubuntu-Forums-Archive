---
title: "Dual head?"
date: 2006-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by cassowary on 2006-05-08
Does anyone know if it's possible to use a dual head setup on Macs with NVidia video cards? I've got a Rev A iMac G5 with the extended desktop "patch"... I have two framebuffer devices (/dev/fb[01]), and I can show images out to the two screens independently like that (the the colors are wonky). Dual head also works fine in Mac OS X.

The iMac G5 has an NVidia GeForce Go5200 [Mac]. From what I've gathered on the internet, the nv drivers *do* support dual head stuff, but most people who have success do so by using the nvidia drivers, which of course aren't available for PPC64 computers.

I'm able to get Xorg to output to either the built-in LCD or my external one, but not both. If I configure it up for both, it just goes to the internal one without complaining about anything...

Has anyone had any success with this, or perhaps you've got some pointers?

---

