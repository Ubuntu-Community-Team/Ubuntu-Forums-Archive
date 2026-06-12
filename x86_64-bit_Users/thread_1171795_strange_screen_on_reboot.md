---
title: "strange screen on reboot"
date: 2009-05-27
forum: x86 64-bit Users
---

### Post by 1feistymedic on 2009-05-27
I have a big problem.  I installed ubuntu 9.04 on my laptop.  Whenever I reboot, the display area of the desktop, which usually takes up the whole lcd screen, only takes up a small portion to the left and upper area of the screen.  This happens on all display (resolution)settings and has to be reset manually.  Once I reboot, it does it again.  Any suggestions?

---

### Post by cariboo on 2009-05-28
You're missing a bit of important info, what graphics adapter and driver does your laptop use?

---

### Post by Yellow Pasque on 2009-05-28
You'll probably have to manually specify the virtual screen size in your xorg.conf

---

### Post by pixel :-) on 2009-05-28
try xrandr first

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

