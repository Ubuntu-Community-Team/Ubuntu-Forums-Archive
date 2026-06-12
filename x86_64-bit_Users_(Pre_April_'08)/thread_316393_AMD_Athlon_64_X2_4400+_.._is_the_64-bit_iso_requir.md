---
title: "AMD Athlon 64 X2 4400+ .. is the 64-bit iso required?"
date: 2006-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by guarnibl on 2006-12-10
Hey guys,

I'm trying to install Ubuntu 6.10. However, when I boot to the live cd (32-bit x86 ISO), it simply hangs after going to the x-server. I just get a tan screen with some ugly lines.

Anyway, this worked fine on my Conroe machine (Intel Core 2 Duo)... what's going on? Do I absolutely need the 64-bit version of Ubuntu to get this thing to work, or will the 32-bit version work and I'm just doing something wrong?

Thanks!

---

### Post by guarnibl on 2006-12-10
Anyone have any ideas?

---

### Post by Pinoy915 on 2006-12-10
No, it is not required as the AMD processors have both the 32 bit and 64 bit instructions. I ran both Ubuntu 6.10 64 and 32. Currently, I'm using the 32 bit version.

---

### Post by heinouskyle on 2006-12-10
I had nothing but problems with the 64 bit version. 32 bit works like a charm though.

---

### Post by roberts3000 on 2006-12-10
I have AMD Athlon64 X2 3800+
nvidia 6800XT
SATA hard drives

I had many problems with the 32 bit version. 
1) would have to restart the machine several times to get live CD to load.
2) took 4 tries to get install to work.
3) ran very slow after install. 

loaded 64bit, had no problems. everything works great. Very fast.

---

### Post by napsilan on 2006-12-11
> it simply hangs after going to the x-server

you wouldn't happen to be using a 7800gt would you?

I had the same problem, it was my video card that wasn't compatible with the nv or vesa drivers on the disc.  I had to do a text mode install then install the nvidia drivers afterwards.  The installed vesa driver might have worked (I forget at this point), but if it doesn't, using a different livecd (I prefer knoppix or sabayon) to download the driver is required.

---

