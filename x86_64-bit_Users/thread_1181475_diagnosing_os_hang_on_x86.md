---
title: "diagnosing os hang on x86"
date: 2009-06-07
forum: x86 64-bit Users
---

### Post by willing on 2009-06-07
I've been happily installing and using Ubuntu for a couple of years but recently ran into a problem on a new machine and would be grateful for some help on  diagnosing its cause: the system hangs sporadically and needs to be powered off. Mouse cursor still tracks but UI/keyboard are unresponsive (clock stops updating; ctl-alt-backspace will not restart X).

 This was my first x86-64 install. Hardware is a Dell Optiplex GX620, usb keyboard/mouse
8.04.2 x86_64 kernel 2.6.24-24-generic. Using gnome, tried xfce but had no effect. Any suggestions on how to identify the cause problem? 
thanks.

---

### Post by Arup on 2009-06-08
Run a memtest and check your power supply.

---

### Post by reeseslover531 on 2009-06-08
> **Arup said:**
> Run a memtest and check your power supply.

Yep, that definately sounds like a memory issue.

---

### Post by willing on 2009-06-10
thanks for the suggestions. I tried running memtest for a couple of days and it reported no problems. My next step will probably be to install an additional os - which should determine whether it's a hardware problem. I was hoping there might be some clues in one of the system logs which would help pin down at what layer things are blocking.

---

