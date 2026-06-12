---
title: "libgl.so.1"
date: 2009-09-28
forum: x86 64-bit Users
---

### Post by Raiju on 2009-09-28
I am trying to run a program in wine(mameppk)
The program ran perfectly under 32-bit. when i run it now it crashes and gives me this.
```
Backtrace:
=>0 0x7d878be6 in libgl.so.1 (+0x52be6) (0x00000009)
  1 0x00000000 (0x00000000)
```
i was told my xserver could be missing the 32-bit libgl
How would i check to see if its installed and install it if it's not installed?

---

### Post by Arup on 2009-09-28
Have you installed drivers for your video card?

---

### Post by Raiju on 2009-09-28
yes i have, i had to install the driver manually. ubuntu doesnt install the driver right when you have two video cards in(or i am missing a step doing it the "hardware drivers" way)

---

### Post by Arup on 2009-09-28
> **Raiju said:**
> yes i have, i had to install the driver manually. ubuntu doesnt install the driver right when you have two video cards in(or i am missing a step doing it the "hardware drivers" way)

Depends, if you have two video cards of different makes like a nvidia and intel or ati, you might run into trouble. lobgl.so.1 are x32 libs needed by programs like Google Earth, Picassa and others as they are x32 programs running under Wine in a x64 bit environment. The ncurses based nvidia hardware driver installer sometimes doesn't install it correctly so removing and then reinstalling the drivers solve the issue.

---

### Post by Raiju on 2009-09-29
Thank you, reinstalling the driver worked :D

---

