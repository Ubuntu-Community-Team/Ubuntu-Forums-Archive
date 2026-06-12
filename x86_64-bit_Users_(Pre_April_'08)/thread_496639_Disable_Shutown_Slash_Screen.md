---
title: "Disable Shutown Slash Screen"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jon.carstens on 2007-07-09
I installed Ubuntu last week and had problems getting it to load. It works now that I disabled the splash screen at startup but it hangs on shutdown. Right before going to the splash screen the sound loops and the monitor turns off. Which is exaclty the same problem I had with startup.

So how do I disable the shutdown splash screen?

---

### Post by Cappy on 2007-07-09
Remove the "vga=whatever" line on your boot paramater and change "splash" to "nosplash" (or remove "splash" instead of adding "nosplash")

---

