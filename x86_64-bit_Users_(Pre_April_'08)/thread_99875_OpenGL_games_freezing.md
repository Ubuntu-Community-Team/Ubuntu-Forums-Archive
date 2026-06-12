---
title: "OpenGL games freezing"
date: 2005-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by sanmadjack on 2005-12-06
Lately while playing OpenGL games under Linux, my games have been freezing the system, complete with visual artifacts. It wasn't too bad until just recently, Ut2004 can't be played for more than a few minutes without it happening. I don't think it's my video card overheating or anything hardware related, because I can play games like F.E.A.R. and Half-Life 2 under windows for many many hours without any problems. Anybody have any ideas? My specs in case it helps:

AMD64 3000+
1024MB RAM
300GB SATA
40GB ATA
GeForce FX 5700
Generic DVD-ROM/CD-RW
Ubuntu 5.10 AMD64

---

### Post by tL0z on 2005-12-06
Hello,

I'm having a problem like yours. When a play an OpenGL 3D game is runs very slowly and breaks a lot! 
I have an AMD 64 3200+ and an ATI Radeon 9600 XT. Can anyone help us?

Thanks

---

### Post by sanmadjack on 2005-12-06
Okay after further analysis th problem is even weirder. When ut2004 "locks up" the sound intermitently keeps playing. From the sound of it the game keeps going (Double kills and point captures are anounced, albeit brokenly). I attached a picture I took with my digital camera of what it looks like when it stops. I've so far tried installing the official nvidia binary package (rather than the ubuntu provided packages), running the 32-bit ut2004 binary (in and out of a 32-bit chroot), as well as reinstalling the game, but it keeps happening.

---

### Post by tburns on 2005-12-08
[QUOTE=sanmadjack]Okay after further analysis th problem is even weirder. When ut2004 "locks up" the sound intermitently keeps playing. From the sound of it the game keeps going (Double kills and point captures are anounced, albeit brokenly). I attached a picture I took with my digital camera of what it looks like when it stops. I've so far tried installing the official nvidia binary package (rather than the ubuntu provided packages), running the 32-bit ut2004 binary (in and out of a 32-bit chroot), as well as reinstalling the game, but it keeps happening.[/QUOTE]


Have you applied the UT2004 patches? My UT2004 would crash randomnly, but the patches fixed that up real good.

---

### Post by sanmadjack on 2005-12-08
Ive tried a fresh isntall, the patch jsut vefore the current one, and the current one. All behave the same.

---

### Post by tburns on 2005-12-08
[QUOTE=sanmadjack]Ive tried a fresh isntall, the patch jsut vefore the current one, and the current one. All behave the same.[/QUOTE]


Is your nvidia card AGP or PCI-Express?

---

### Post by sanmadjack on 2005-12-08
Agp.

---

### Post by tburns on 2005-12-08
[QUOTE=sanmadjack]Agp.[/QUOTE]

Trying running UT2004 from a terminal, it might give you some clues. Also I would check the UT2004 log.

---

### Post by sanmadjack on 2005-12-09
I don't see anything in my log that would point to the cause, I attached the log in case someone sees something I don't.

I always run ut2004 from a terminal, but, being fullscreen, I've never seen what it says. I'll switch ut2004 to a window then check it.

---

