---
title: "Nvidia Driver causes system slow down"
date: 2007-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by bd1308 on 2007-03-08
Hello. I recently built a new system and couldn't wait to try beryl out on it!

Specs:
AMD Athlon FX-60
1GB Ram
80GB SATA drive (I have a file server too)
Nvidia 7800 GT


It's a decent system I would say. Anyway, I installed the x64 version of Ubuntu with hopes that it would run the best (fastest) for my system.

And it did...

But, when I was installing the Nvidia Driver (both the nvidia-glx and the Nvidia Web page driver) the screen drawing is just too slow....

I mean it takes five seconds to draw windows...it's like running Kubuntu on my G3 366.

Now, this did not occur until my update of the nvidia driver (everything works with the built-in nv driver...VERY VERY FAST!)

britt@britt-desktop:~$ glxinfo | grep direct
direct rendering: Yes
britt@britt-desktop:~$

If anybody could help out, I would appreciate it .

---

### Post by renzokuken on 2007-03-08
could you post your xorg.conf ( /etc/X11/xorg.conf ).

another easy way to install the latest nvidia driver is using the Envy script, [www.albertomilone.com](www.albertomilone.com) and look at projects and guides

---

