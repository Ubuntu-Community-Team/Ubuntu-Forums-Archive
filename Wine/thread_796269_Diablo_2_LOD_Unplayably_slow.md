---
title: "Diablo 2 LOD Unplayably slow"
date: 2008-05-16
forum: Wine
---

### Post by Flubs4u on 2008-05-16
I'm running wine 1.0-rc1 on 8.04 and this game is SLOW. My hardware is an amd 64 3200+, 1.5gb ram and an Nvidia 6800 gt (nvidia driver).  I'm at work right now, so I don't have access to the logs but I didn't see anything worth mentioning.  Has anyone experienced this or know how to fix it?

---

### Post by Akingboy on 2008-06-30
Same here but it's because you use direct3d.

If someone knows how to boost performance on direct3d please tell.
It looks so much better on it than directdraw.

Got ati graphics card and drivers.
wine is 1.1.0

---

### Post by Akingboy on 2008-07-02
(Bump)

Anyone?

Why diablo runs extremely slow with Direct3D but not with directdraw?
I got ATI drivers.

---

### Post by brad_c6 on 2009-08-09
The problem has something to do with being full screen run it with the "-w" for window flag and it is really really fast. Cheers

env WINEPREFIX="~/.wine" wine "C:\Program Files\Diablo II\Diablo II.exe" -w

Thats the command I use

---

### Post by brad_c6 on 2009-08-09
Just figured out how to make it work all the way, run the Diablo 2 Video test program "Select Direct Draw" and then start Diablo 2 and wham! it works quickly :)

---

### Post by khelben1979 on 2009-08-09
I always use the -opengl parameter when I'm running games with Wine.

---

### Post by hikaricore on 2009-08-09
> **khelben1979 said:**
> I always use the -opengl parameter when I'm running games with Wine.

The opengl flag isn't supported by all games even games from blizzard.
This command line addition is actually part of the application and has nothing to do with WINE.

---

### Post by khelben1979 on 2009-08-09
> **hikaricore said:**
> The opengl flag isn't supported by all games even games from blizzard.
This command line addition is actually part of the application and has nothing to do with WINE.

The versions of Wine that I have tried without the -opengl parameter made the games unplayable because of extreme low speed.

---

### Post by Soulcage on 2009-08-09
Run glide using [http://www.svenswrapper.de/english/index.html]("http://www.svenswrapper.de/english/index.html") you can run it fullscreen at your desktop resolution.

---

### Post by russ723 on 2009-08-10
I'm glad to know I'm not the only one still addicted to D2. It is 2009 and I'm still collecting Unique crap.

---

