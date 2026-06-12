---
title: "Trouble running winetricks"
date: 2013-03-15
forum: Wine
---

### Post by DarrenVortex on 2013-03-15
Hi,
I recently switched to Ubuntu 32-bit and am trying to run some windows-specific programs using Wine. I had to patch the source a bit and compile wine myself, and it all went well but right now I'm trying to run winetricks (which I assumed is part of the source I compiled), and I get the following prompts:
"WINE is wine, which is neither on the path nor an executable file" -> when I am in the wine source directory, where I compiled it.
"wineserver not found!" -> when I'm anywhere else.
running "wine" itself works fine when I'm in the source directory but anywhere else, it's not found.
I'm also not sure where wine is installed, i just used the default prefix. Winetricks also shows up in the Unity search panel as an application, but when I click it nothing happens.
Any ideas?

---

### Post by QIII on 2013-03-15
*Moved to **&#8203;Wine***

---

### Post by DarrenVortex on 2013-03-15
*bump

---

### Post by mörgæs on 2013-03-15
Please show patience and don't bump your thread.

---

### Post by DarrenVortex on 2013-03-16
ok I found the solution! :)
I simply forgot to run "sudo make install", I only did "make". "sudo make install" solved the problem!

---

