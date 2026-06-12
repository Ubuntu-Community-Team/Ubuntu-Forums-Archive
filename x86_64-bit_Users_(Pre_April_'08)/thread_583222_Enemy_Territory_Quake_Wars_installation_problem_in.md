---
title: "Enemy Territory Quake Wars installation problem in 64 bit Gutsy"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-20
```
chris@ubuntu:~/Desktop$ sudo ./ETQW-demo-client-1.1-full.r5.x86.run 
[sudo] password for chris:
STUBBED: ftell is 32 bit!
 at /home/timo/Build/mojosetup/fileio.c:246
chris@ubuntu:~/Desktop$ 
```

---

### Post by Tryke on 2007-10-20
I noticed that too. It's still installed, but when I run "etqw", the tail of the output looks like this:

```
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082cc6d1]
[0x082bc82f]
[0xffffe600]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
thread priority set to 0
ryan@Trykubuntu:~/etqw$ 

```

I'll be sure to check this thread if I find a fix. There's obviously something segfaulting.

---

### Post by Tryke on 2007-10-20
Hah, I just noticed that my graphics card stopped doing direct rendering. I swear it was working last night. Maybe this changed while I was playing with KDE4... will post again when I get things working.

---

