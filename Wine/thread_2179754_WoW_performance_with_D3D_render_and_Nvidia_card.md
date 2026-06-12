---
title: "WoW performance with D3D render and Nvidia card?"
date: 2013-10-09
forum: Wine
---

### Post by Melhisedek on 2013-10-09
Well I'm fooling around with WoW and D3D renderer to see what performance I can get. So far on my

3570k @ 4.4 GHz
GTX 770
8 GB RAM

I get around 30-40 FPS in Pandaria and a bit more in other cities. This is at high settings. It feels I should have more with my rig but sadly no go. 
I'm using latest wine and 331 drivers from xorg PPA.

What is your experience with D3D and WoW?

P.S. I've tried OpenGL but it disables a lot of settings (shadows at low among others) so I'm not really liking it.

---

### Post by Tweak42 on 2013-10-12
Unfortunatly the low performance in D3D and OpenGL is probably caused by wines muti threading handling with multi core cpus.
[http://bugs.winehq.org/show_bug.cgi?id=11674](http://bugs.winehq.org/show_bug.cgi?id=11674)  (relevant stuff is mainly at the end)

There is some dev work to address this on the horizon in wine, and since you are running nvidia you can try the __GL_THREADED_OPTIMIZATIONS=1 option; see this thread:
[http://ubuntuforums.org/showthread.php?t=2071968](http://ubuntuforums.org/showthread.php?t=2071968)

Also you can try this experimental patched version of wine aimed at guildwars2:
[https://launchpad.net/~foresto/+archive/winepatched/](https://launchpad.net/~foresto/+archive/winepatched/)

> **Melhisedek said:**
> Well I'm fooling around with WoW and D3D renderer to see what performance I can get. So far on my

3570k @ 4.4 GHz
GTX 770
8 GB RAM

I get around 30-40 FPS in Pandaria and a bit more in other cities. This is at high settings. It feels I should have more with my rig but sadly no go. 
I'm using latest wine and 331 drivers from xorg PPA.

What is your experience with D3D and WoW?

P.S. I've tried OpenGL but it disables a lot of settings (shadows at low among others) so I'm not really liking it.

---

### Post by Melhisedek on 2013-10-13
Thanks mate, I tried out that patched wine version and it increased my FPS to 50-60 in Pandaria now. definitely an improvement, still looking for tweaks though :)

---

