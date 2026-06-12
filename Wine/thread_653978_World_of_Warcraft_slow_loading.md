---
title: "World of Warcraft: slow loading"
date: 2007-12-30
forum: Wine
---

### Post by Starmartyr on 2007-12-30
I just built a new rig and I have installed Ubuntu 7.10, running Compiz, and everything works great.  I also have World of Warcraft running under Wine 0.9.52, and runs nice, but when I try to join Alterac Valley, a battleground with 80 players, it slows on load, then freezes.  I have to "force Quit" to exit and restart.  It also slows on Eye of Storm, a 30 player battleground, freezes for 1-2 minutes, then loads.  The other 2 battlegrounds are slow on load, but no long freeze time.  So, Alterac Valley is the only one I can't play.

System Specs:
mb: MSI K9NBPM2-FID
AMD X2 5200 2.6GHz
EVGA 8600 GT 256mb
4g RAM: G.Skill DDR2 800
Seagate 250g SATA 3.0

I run one Screenlet, system runs at 22% memory in use by programs, so I am clearly not using my RAM at full.  Is it the graphics card?  What settings should I change to be able to run WOW with no freezing?  Is this a Wine issue?  Need help.

Thanks :)

---

### Post by TidusBlade on 2007-12-30
Your specs are really good, the only thing I can think of is that addons could be slowing it down, or that it needs to load alot, so maybe try lowering the video settings significantly, and posting back the results? Also try with no addons?

---

### Post by Starmartyr on 2008-01-03
Ok.  Finally got an error message:

The application has encountered a critical error
Not enough memory
Program: ....wow.exe
File .\src\lmempool.cpp
Line 311
Requested 640 bytes of memory

I did install the latest nVidia driver 169.07 and everything works great, just doesn't correct this problem.

---

