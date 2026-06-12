---
title: "Keyboard not working in windows xp after install of ubuntu"
date: 2007-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by adammouse on 2007-04-16
This is maybe not the best place to post a problem but my keyboard only stopped working directly after installed Ubuntu I may aswell try here first.

My keyboard has stopped working, but only in Windows XP. It happened after installing Ubuntu 6.10 on a seperate partition on the end of my SATA Hard drive. The keyboard is a Logitech with a PS/2 connector. The motherboard is an Asus m2n32 sli deluxe.

Any help appreciated, Adam.

---

### Post by ronocdh on 2007-04-17
> **adammouse said:**
> This is maybe not the best place to post a problem but my keyboard only stopped working directly after installed Ubuntu I may aswell try here first.

My keyboard has stopped working, but only in Windows XP. It happened after installing Ubuntu 6.10 on a seperate partition on the end of my SATA Hard drive. The keyboard is a Logitech with a PS/2 connector. The motherboard is an Asus m2n32 sli deluxe.

Any help appreciated, Adam.

To be clear, the keyboard is not responding when Windows XP is fully booted and running, right? If so, this means that A) it responds fine in Ubuntu and B) it also responds fine on the GRUB screen (because you were able to choose XP).

Have you tried hooking up a USB keyboard instead of the PS/2, and seeing whether that's responsive?

---

### Post by adammouse on 2007-04-17
Yes, works at boot screen, GRUB boot loader and ubuntu. Just when Windows XP is fully loaded it doesm't work. I haven't tried a USB keyboard, will report back with results later.

---

### Post by thelinuxguy on 2007-04-17
> **adammouse said:**
> Just when Windows XP is fully loaded it doesm't work.

Used to happen with my system sometime back. But I did not have Ubuntu at that time and so can't relate the two. I used to disconnect and reconnect the PS/2 keyboard while Windows was loaded and then reboot. Couldn't find the relation but this worked for me.

---

### Post by Zorael on 2007-04-17
[quote=Thelinuxguy]I used to disconnect and reconnect the PS/2 keyboard while Windows was loaded and then reboot. Couldn't find the relation but this worked for me.[/quote]

Ouch!

[quote=Wikipedia]PS/2 ports are designed to connect the digital I/O lines of the microcontroller in the external device directly to the digital lines of the microcontroller on the motherboard. They are not designed to be hot swappable. Hot swapping PS/2 devices usually does not cause damage due to the fact that more modern microcontrollers tend to have more robust I/O lines built into them which are harder to damage; however, hot swapping can still potentially cause damage. Shorting one pin to another on a PS/2 port can easily kill one or both microcontrollers.[/quote]

---

### Post by thelinuxguy on 2007-04-17
[QUOTE=Wikipedia]
PS/2 ports are designed to connect the digital I/O lines of the microcontroller in the external device directly to the digital lines of the microcontroller on the motherboard. They are not designed to be hot swappable. Hot swapping PS/2 devices usually does not cause damage due to the fact that more modern microcontrollers tend to have more robust I/O lines built into them which are harder to damage; however, hot swapping can still potentially cause damage. Shorting one pin to another on a PS/2 port can easily kill one or both microcontrollers.
[/QUOTE]

I wasn't aware of this. And luckily I didn't damage my keyboard and worse, the port. Thanks for this vital update.

---

