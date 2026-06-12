---
title: "World of Warcraft gives me this error..."
date: 2008-09-20
forum: Wine
---

### Post by residualbit on 2008-09-20
this happens whenever I try to run the game...

I get a pop that says:

The application has encountered a critical error.
ERROR #132 (0x85100084) Fatal Exception


The instruction at "0x713350" referenced memory at "0x000000"
The memory could not be "read"



I am running 32 bit 8.04.
and the wow install has all of the patches installed.


any ideas?

---

### Post by residualbit on 2008-09-20
anything?

---

### Post by Bochenekgsx on 2008-09-21
did you edit your config.wtf file to disallow the use of directx and rather reference OpenGL? I got the same error each time i tried to load WOW before editing that file.


edit: can you post your system hardware?

---

### Post by residualbit on 2008-09-21
i dont have that file yet because I havent been able to successfully run the game at all yet.

MCP67m chipset
NVIDIA GeForce Go 7150M 
4 Gigs of ram.

---

### Post by Bios Element on 2008-09-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

You'll no doubt find that interesting. Edit the registry and you'll probably have better luck.

---

### Post by residualbit on 2008-09-21
so the problem was...or at least i think it was...

i run ubuntu natively in 1280x800 and the game wants to run in 1024x768.

switched and it worked perfectly. weird.

---

