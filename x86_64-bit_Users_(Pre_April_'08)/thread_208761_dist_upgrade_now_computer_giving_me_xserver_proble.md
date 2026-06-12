---
title: "dist upgrade now computer giving me xserver problem"
date: 2006-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosmoshell on 2006-07-04
i add some extra repositorys and lateron did a dist upgrade now i get that anooying faild to start xserver screen. also since this happend i havent been abled to connect to the internet threw w3m. Is there a way to undo this without loosing all my settings.

---

### Post by Slurm on 2006-07-07
You did an upgrade and your Xserver failed to start.  I had the same problem with my system.  But first I must mention that I am using an Nvidia graphics card.  

The reason why my Xserver failed to start was because the upgrade upgraded my kernel also.  When this happens, the kernel header is no longer recognized by the Nvidia Driver which causes the Xserver and Xorg to fail.  

Check to make sure the linux header and the header for the graphics driver match.  Follow the procedure outlined by Tseliot (I don't know the thread) and it will fix it.  

IF you have a different video card, then I don't know.  But I hope this helps.

Slurm

---

