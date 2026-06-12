---
title: "x800 GTO PCIe"
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by charper_99 on 2007-07-30
I'm one of the lucky ATI x800 GTO people and an almost-noob trying to run 64 bit Feisty.  Yes, I realize there's a lot of forum posts/articles on the internet - and I've looked through a lot of them, but I can't find any answers.  Ok - here's my main problem: I can run ATI's drivers and get 3d Acceleration (although I still can't utilize it for steam games in Wine - but that's another problem), but my computer will not shut down.  I mean, I can't shut down, restart, ctrl alt back, alt f2, or anything without getting a black screen and forcing a hard reboot.  The Mesa drivers (usually) allow me to restart without any problems, but I lack the 3d acceleration.

The story gets a bit stranger though - because after switching drivers and different techniques, etc in and out; I can't access my restricted drivers manager anymore.  It now gives the error "Your hardware does not need any restricted drivers."  

Basically put, anybody know a way to get 3d accelerated drivers and keep the ability to restart?

P.S. don't know if this is related or not; but the computer also crashes if I allow it to display the splash screen on boot.

Rest of my computer (if it helps):
MSI N4SLI-A9 socket 939 mobo
Athlon 64 x2 4400+
3.0 GB Ram
ATI X800 GTO PCIe
500 GB SATA (Software) Raid

---

### Post by Cappy on 2007-07-30
take off any line in your GRUB like "vga=777" or "splash" and put "nosplash", that may fix the crashing.

---

### Post by charper_99 on 2007-07-30
Already done that - as I said in the post, taking away splash fixes the crash that would occur if I allowed splash - so I've removed that.  I currently don't run with any kernel arguments, although I have tried setting some acpi arguments explicitly, but it didn't help either.   Thanks for the tip though - I'm sure it'll help somebody.

---

### Post by charper_99 on 2007-08-01
*bump* any more ideas, anybody?

---

