---
title: "What kind of performance can I expect in WOW"
date: 2008-07-10
forum: Wine
---

### Post by Bochenekgsx on 2008-07-10
I'm very new to Ubuntu and linux in general, but I love what I have learned so far. Anyway, I'm downloading WoW + BC right now, and wanted to get an idea of what kind of performance I'm going to get once I get it all up and running. It will be a fresh install in Wine.

Wine 1.1
Ubuntu 8.04 (64bit)
AMD Athlon64x2 5200
2GB DDR2-1066 (Dual channel enabled)
EVGA GeForce 8600GT 256MB PCIe

I've heard good and bad, and most of the bad I hear is from people using integrated graphics -OR- ATI cards.. I just replaced my HD2600XT for the 8600gt in hope of curbing any potential problems.

I also know that windows uses DirectX (direct3d) for rendering games (WOW) and that Ubuntu utilizes OpenGL. Will I notice a performance increase, decrease, or no change (with regards to gaming) from my shift to Ubuntu from winblows XP.

---

### Post by michaeel on 2008-07-10
WOW should be well playable on your box ;)

WOW runs fine on my PC (intel 2x 2.6mhz, gforce 7950gt, 4gb ram and ubuntu 64Bit) with about 55-115FPS.
i use CX-Games to play it, it runs out of the box without any errors. CX-Games is not free but therefore i doun't need to mess around with any config settings. O:)

---

### Post by thisismalhotra on 2008-07-10
To michaeel: It depends on your graphics card a drivers but it works very well, on my nvidia 8800gt always maxed out at 60FPS even in shatt. Btw WoW maxes out at 60FPS.

---

### Post by Akingboy on 2008-07-12
No it doesn't max at 60 fps if you just don't have refresh rate of your monitor at 60hz and Vsync ON.

I get sometimes 300 fps when looking in the sky.

I noticed very low fps like 10-30 when terrain distance is high but when at lowest its 100+
I don't understand that but helped me to gain 100 fps to reduce only terrain distance. I got high end computer that runs all games on good graphics. Atleast on windows =/

---

### Post by collinp on 2008-07-13
What do you consider "High End"? High end would be Core 2 Quad Overclocked at 4.0GHz, 2x Nvidia GTX 280 in SLI, Western Digital Raptor hard drives in Raid 5 config, Nvidia 750i SLI Motherboard, Sound Blaster XF-I (i think that is what it is), Blu-Ray RW Drive, 24" LCD Monitor.

---

### Post by OliW on 2008-07-13
You'll get a slight performance drop but you should be fine and extremely playable on your system. As you correctly mentioned, Blizzard use OpenGL and Wine passes those calls straight through to native OpenGL libs. WoW is one of the best Wine supported games.

And good choice on moving off ATI. Their open drivers are miles off being feature-complete... When they're "finished" they'll probably be better than nvidia's drivers but we're years from getting equal quality drivers. As much as some people detest closed-source binaries, the nvidia driver does what users need it to 99.9% of the time.

---

### Post by webbed on 2008-07-13
I personally used an AMD Athon64 3200+, NVIDIA GeForce 8500GT 512MB and get FPS usually around 60.

But if I look at stuff like the sky or something with out that much for it to render it goes up to 100+ FPS.

BGs and Raids are around 20 FPS unless I'm using Lowerping then it goes down to 1-5 FPS or hangs the game.

---

### Post by darkaudit on 2008-07-14
On a HP Pavilion a1637c, AMD Athlon 64x2 4200, 4GB RAM, Nvidia 7800GS, and most video settings turned down to slightly below default (spell effects at max, though), I get ~50-60 fps in quiet zones and ~20fps in Shattrath on Dark Iron.

That will vary depending on what WM I'm using. GNOME and KDE give the lowest frame rates, XFCE a little better, and Fluxbox the best of all (that I use). With GNOME I'd see an average of ~15 fps in Black Temple during fights. That went up to ~20 with Fluxbox.

On a quiet afternoon in Eversong Woods, I saw a ping rate of ~75ms (my latency is consistently better in WINE than native Windows) and a frame rate of ~100fps. 

I can raid effectively with my setup. Except for memory, OP has a higher-end rig than mine. So results may be even better.

Short version: latency and load times are better in WINE in my experience. There's a slight frame rate hit, but not so much as to negatively affect gameplay.

(That said, I haven't tried any BG's in several weeks. None at all with WINE.)

---

