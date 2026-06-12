---
title: "Wine 1.0 with Hitman 2 no sound in game"
date: 2008-08-14
forum: Wine
---

### Post by Gcentrex on 2008-08-14
I resonantly moved back to Linux and my choice was Ubuntu 8.04 X64, got most of my requirements met with Ubuntu Steam works HL2 and most other games work when passing DirectX 8.1 string. Diablo II LOD works.

So I try to launch Hitman 2, installed no problem start to play audio in the videos and in the main menu but as soon as I get to the first part to play their is no sound what so ever, this is currently the only thing I have no sound in. Their is nothing listed in the WineHQ app database without sound issues.

I am using the Wine version from the Ubuntu repository.

---

### Post by zono50 on 2010-06-17
I experienced the same problem.  What I did to fix it was enable oss in the wine configuration audio tab.  Hope this works 4 ya.:guitar:

---

### Post by dino99 on 2010-06-18
use the latest wine

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by Sean Hayes on 2010-08-08
> **zono50 said:**
> I experienced the same problem.  What I did to fix it was enable oss in the wine configuration audio tab.  Hope this works 4 ya.:guitar:

Didn't work for me, but sound was already working in other games (I have it installed via Steam). I'm using the latest Ubuntu and Wine.

---

### Post by gster on 2011-02-02
This drove me crazy for a day or so and I couldn't find the solution anywhere.  Eventually, I set audio to emulation mode in wine audio config and now all is good.

---

