---
title: "*buntu install gives strange display after boot."
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by keratos on 2008-03-17
Hi

This is a really weird on. 

I've installed x64 kubuntu and ubuntu no probs.

Tried to see what x86 would run like so installed 7.10 32bit both from alternate and live CDs.

In both cases, boots up fine but when the GUI starts I get what looks like the framebuffer device at the top half of the screen, split into two , each side a mirror copy of the other. Lines are unreadable (look like about 5px in size and green), and the ubuntu  gdm is all "squashed" into top half of the screen.

The bottom half is the remainder of the GDM and looks "fine"  (as half images go)  but clearly not usable.

I've analysed the Xorg.0.log which is using vesa xorg (1.3) module driver and no errors.

ANy ideas?

---

### Post by Joeb454 on 2008-03-17
What video card do you have?

Sounds like it might need a restricted driver, in which case it's not too weird ;)

---

### Post by keratos on 2008-03-17
Via K8M890

Works fine under x64 *buntu, Zen, PClinux and Vector.

It flies under Zen BTW but that is using Xorg v1.4 , wheres here its 1.3 

whatever..

I've just logged back into here from my x86 kubuntu and what was weird  was that when I started X over in x86, I could see a corrupted image of this post from my x64 install !!!! despite resetting the machine !!!! ??

Defo something strange.

I also copied the xorg.conf from this working kubuntu (x64) over to the x86 install, but this didnt change anything.

??????

---

### Post by keratos on 2008-03-17
The unichrome and VIA proprietary drivers do not support this chip

The openchrome is slow - I've logged a but at their mailing lists.

Like I said, the x64 *buntu-s work, the x86 (i32) do not.

---

