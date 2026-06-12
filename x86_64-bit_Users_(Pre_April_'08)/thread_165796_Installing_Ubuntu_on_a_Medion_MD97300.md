---
title: "Installing Ubuntu on a Medion MD97300"
date: 2006-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by LonelyStar on 2006-04-25
Hello together,
I am triying Ubuntu 64 bit (v5.10) on a Medion MD97300.
- If I start the kernel without options, it hangs during boot. Last message:
input: AT Translated Set 2 keyboad on isa0060/serio0
- On this page ([http://www.math.hu-berlin.de/~kulshres/md97300.html](http://www.math.hu-berlin.de/~kulshres/md97300.html)) I have found some kernel paramters. They did not help.
- Starting with "linux acpi=off noapic nolapic" results in the kernel booting into a black screen.
Someone any help?
Thanks!
Nathan

---

### Post by LonelyStar on 2006-04-25
Found a solution: starting with "linux acpi=off noapic nolapic vga=771" works (so far).

---

### Post by LonelyStar on 2006-04-25
OK, installation went fine. But after the installation, the screen turned black. Now, when I start the computer the screen turns black after booting.
Any help?
Thanks!
nathan

---

