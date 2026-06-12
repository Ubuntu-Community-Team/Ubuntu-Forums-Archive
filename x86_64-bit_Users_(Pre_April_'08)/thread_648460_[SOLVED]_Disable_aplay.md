---
title: "[SOLVED] Disable aplay"
date: 2007-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by drfox on 2007-12-23
How do I disable aplay as a service?
I've reinstalled Gutsy 64 several times because one of these packages (or, more likely, their dependencies) has borked my installation: TuxPaint, TuxType, FrozenBubble
What is consistent is that at first reboot, my sound disappears, and at 2nd reboot I start having panel problems and the computer will not shut down without cold reboot. 
System monitor shows aplay as uninterruptible. Also, when I start firefox, firefox-bin is uninterruptible.

I'd like to disable aplay and see if I can use these programs and still get sound.  Thanks.

Larry

---

### Post by Ehtetur on 2007-12-23
> **drfox said:**
> How do I disable aplay as a service?

If you want to disable the alsa-utils service:
System --> Admininstration --> Services
Unchecking the box by alsa-utils  prevents it from starting at any runlevel.
You can right-click on alsa-utils  --> properties to select any specific runlevels (ie 3) that you want it to start.
20 is a good # for starting this service.

---

### Post by drfox on 2007-12-24
> **Ehtetur said:**
> If you want to disable the alsa-utils service:
System --> Admininstration --> Services
Unchecking the box by alsa-utils  prevents it from starting at any runlevel.
You can right-click on alsa-utils  --> properties to select any specific runlevels (ie 3) that you want it to start.
20 is a good # for starting this service.

Thanks!

Larry

---

