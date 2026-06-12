---
title: "from 32-bit 6.06 to 64-bit 6.10"
date: 2006-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by raterwil on 2006-11-14
Several months ago, I installed the 32-bit x86 version on my machine. I now realize that it is a 64-bit machine (EM64T). Can I upgrade to 64-bit 6.10 without starting from scratch (i.e. wiping the disk) ?

Many thanks,

Robert

---

### Post by kleeman on 2006-11-14
I would suggest a fresh install but do not wipe your home partition (assuming you have such a beast) so you don't lose a whole bunch of personalized stuff.BTW I have that system (em64t) with xeons and the 64bit OS made a very noticable difference in speed and responsiveness. YMMV

---

### Post by RAOF on 2006-11-14
> **raterwil said:**
> Several months ago, I installed the 32-bit x86 version on my machine. I now realize that it is a 64-bit machine (EM64T). Can I upgrade to 64-bit 6.10 without starting from scratch (i.e. wiping the disk)?


Not without some **serious** manual crazyness.  You **will** need to install from a AMD64 install disc, and it will wipe your / partition.  However, if you've got you /home directory on a separate partition you will keep all your documents/settings/etc.  Still, **backup recommended** :).

In particular, you **won't** be able to upgrade using the update-manager.

---

