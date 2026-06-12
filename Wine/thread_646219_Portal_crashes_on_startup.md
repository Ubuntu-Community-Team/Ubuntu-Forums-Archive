---
title: "Portal crashes on startup"
date: 2007-12-20
forum: Wine
---

### Post by sb676 on 2007-12-20
Hi,
I'm relatively new to Ubuntu (got it a month ago), and I'm not sure whether this is the right place to put it, but...

Today I installed Portal using Wine. The installation went perfectly, but the problem is that it crashes about 10 seconds after the Valve logo shows up. I have tried using -novid, changing it to windowed and setting the resolution to 1024x768, but it still doesn't work. Here's my hardware:

CPU Speed - 1.73 GHz
Memory - 512 Mb
Video - ATI Mobility Radeon X300

Portal is the only game I've tried, but I'm pretty sure it's the same for all of the games in the Orange Box. Also, is it worth installing?

Thanks.

EDIT: I forgot to mention - I'm using Gutsy.

---

### Post by aoanla on 2007-12-21
The ATI graphics card is your problem - several driver releases for it seem to cause Wine severe problems when playing games in Steam. You might try upgrading to the latest Catalyst driver, released just yesterday, to see if that improves matters.

Also, try different versions of Wine - I found that versions around 0.9.42 to 0.9.45 are most stable with ATI cards, so you might want to try a couple from that version range.

---

### Post by sb676 on 2007-12-21
I thought it might have been the graphics card...

Anyway, I tried all the Wine versions from 0.9.42 - 0.9.45, but none of them worked. I also got the latest Catalyst driver from ATI, but that didn't help either. I don't want to have to get a new video card:(

---

### Post by aoanla on 2007-12-22
Have you tried adding 

-dxlevel 81

to the launch options? DX9 can be a little unstable for some games, still (and this includes Source engine games, even on nVidia cards).

---

