---
title: "World of Warcraft freezes and stutters periodically"
date: 2008-04-10
forum: Wine
---

### Post by potatan on 2008-04-10
Hi,

I've asked this question on the WineHQ forums with no replies, just wondering if anyone here had any ideas?

When I load World of Warcraft the CPU jumps from an average of 10-15% up to 100% and stays there pretty constantly whilst playing. This doesn't seem to affect gameplay most of the time (and I understand it may be relatively normal behaviour for running games under Wine),** but occasionally I get a complete lock up of the game for about 3 seconds. The game screen freezes completely and the sound stutters during this time.**

These stutters very often follow a mouse-click (for instance when selecting items, or speaking to NPCs), but not exclusively - the game also sometimes locks up while just running around. Also no difference between left or right click for the frequency of the problem.

My frame rate is fine, maybe 50-70fps on average, and my network lag is also fine, about 40-60ms.

I'm running 32 bit Ubuntu Gutsy 7.10 on an AMD 64 3500+ with 2GB RAM, using an Nvidia GeForce 7600 GS, using Wine 0.9.58

I have disabled all my Addons to see if that helps, and it doesn't. I have also added the Wine registry edits and config.wtf amendments suggested elsewhere (particularly in the WoW Wine Wiki).

Any ideas? Or any other info I can provide?

Many thanks in advance.

---

### Post by potatan on 2008-04-10
Some more info

glxgears running in a window give the following after 30seconds:
22456 frames in 5.0 seconds = 4491.038 FPS
22448 frames in 5.0 seconds = 4489.592 FPS
22270 frames in 5.0 seconds = 4453.843 FPS

glxinfo | grep 'OpenGL version' :
OpenGL version string: 2.1.1 NVIDIA 100.14.19

lspci | grep -i nvidia :
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

glxinfo | grep vendor :
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

Thanks.

---

### Post by Perfect Storm on 2008-04-10
Please use our wine forum, also there's a lot of WOW stuff which you can use the search button for.


*Thread moved to Wine forum*

---

### Post by potatan on 2008-04-10
I've been reading up for about 3 months on the WoW problems others seem to be experiencing, without any success at finding a solution to my particular problem, though I realise it was a good suggestion - just in case I hadn't bothered checking previously.

Cheers

---

