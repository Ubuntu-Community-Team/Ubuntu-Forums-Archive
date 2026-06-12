---
title: "World of warcraft startup crash."
date: 2008-07-11
forum: Wine
---

### Post by jean9120 on 2008-07-11
Heres the problem. I installed wow without errors and everything went smoothly but when i go to open wow it just crashes and this is what it says 


This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:73467530

The instruction at "0x73467530" referenced memory at "0x00000000".
The memory could not be "read".

---

### Post by Neurasthenic on 2008-11-11
I'm having the same problem, any ideas? I've looked through all the troubleshooting pages I could find.

---

### Post by Rody on 2008-11-11
you need to have it start and run in opengl

edit your config.wtf file and add
SET gxApi "opengl"

ubuntu specific instructions for setting up world of warcraft
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Neurasthenic on 2008-11-12
> **Rody said:**
> you need to have it start and run in opengl

edit your config.wtf file and add
SET gxApi "opengl"

ubuntu specific instructions for setting up world of warcraft
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
There won't be any Config.wtf file if the game hasn't run yet. So to the original poster, create your own Config.wtf file with the SET gxApi "opengl"
line, and save it in Program Files\World of Warcraft\WTF.

---

