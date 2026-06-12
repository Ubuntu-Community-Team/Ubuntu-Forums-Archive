---
title: "Is it possible to run PORTAL under WINE?"
date: 2008-04-08
forum: Wine
---

### Post by volanin on 2008-04-08
I am having problems running PORTAL under WINE.
The game just freezes when it gets to the loading screen after the Valve video.

Can anybody help me?

I am running Ubuntu Gutsy with the latest WINE 0.9.58.
I also have a MacBook with an Intel 950 graphics card.

Thanks a lot!
:)

---

### Post by alexforcefive on 2008-04-08
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9432](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9432)

---

### Post by LinuX-M@n1@k on 2008-04-08
> **volanin said:**
> The game just freezes when it gets to the loading screen after the Valve video.

Try running the game with parameter "-dxlevel 81". Example:
```
$ wine ~/Portal/hl2.exe -game portal -dxlevel 81 -novid
```
-game portal = run Portal instead of HL2
-dxlevel 81 = run the game with DirectX 8.1 << this should fix it >>
-novid = skip the video intro

---

### Post by volanin on 2008-04-08
Yes, I tried both the flags in the WineHQ page and the -dxlevel 81 flag.
No dice though.

That's why I am thinking it might be my intel card.
Everybody that reported PORTAL working had an nvidia.

Has anybody with an intel card been able to make it run?
:)

---

### Post by soxs on 2008-04-09
I've got an AMD/ATI card (RadeonHD 3870 OC) and I have the same issue.. after the vlave intro video the portal closes, no error, nothing.

---

### Post by DJKMan on 2008-04-10
Well, for me I have an ATI X1200 Radeon that is built in the Toshiba Laptop and it gets to the menu just fine. I just can't load a level. I noticed that the framerates are pretty low no matter what I do and the bloom effect is off. Anyone got an update?

---

### Post by Spydr4590 on 2008-04-10
For ATI users try using Opengl instead of directx. To do this goto [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Look for DirectDrawRenderer and use opengl. If it's not there you'll have to add the key. Then you'll need to mess with OffscreenRenderingMode flags. This should make portal run for ati users.

---

