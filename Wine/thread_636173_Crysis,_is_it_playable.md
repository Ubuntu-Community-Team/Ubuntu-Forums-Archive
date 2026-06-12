---
title: "Crysis, is it playable"
date: 2007-12-09
forum: Wine
---

### Post by dethredic on 2007-12-09
I searched the forum and surprisingly there is nothing on Crysis, other than a font.

Does anyone know if this game will work under wine, if so how well?

I have an E6420 @ 3.0Ghz, 2gigs 960mhz Ram, and a 8800GTS 640mb, so I should be able to handle the game.

---

### Post by cogadh on 2007-12-09
Check Wine's Application Database next time:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880)

---

### Post by dethredic on 2007-12-09
I did.

It is a little out of date: "Crysis is an **upcoming** science fiction first-person shooter"

It seems there are no reports on the game yet, which is why I asked here.

---

### Post by cogadh on 2007-12-09
However, if the demo and beta test both have a garbage rating, it stands to reason that the release game will also not work well, if at all. Generally speaking, brand new games never work in Wine at the time of release. It usualy takes at least 3 or 4 Wine updates before you start seeing any progress on them.

---

### Post by Sockerdrickan on 2007-12-09
There are some bronze ratings and some of the pics looks really good actually. It will be interesting when this game runs solid and Vista has got nothing.

---

### Post by dethredic on 2007-12-09
Well, I guess I shouldn't ask for it for Christmas then.

---

### Post by Sockerdrickan on 2007-12-09
Get Quake IV or something instead!

---

### Post by MickLionheart on 2007-12-09
Quick Answer: No

Long Answer: Not right now, but eventually DirectX 10 will most likely be working in wine for the most part.

---

### Post by cogadh on 2007-12-09
Crysis will run in DX 9 mode on Windows (it can run on both XP and Vista), so the fact that DX 10 is not in Wine yet isn't really holding it back from running, it should just keep it from running at its fullest. Chances are the problem that keeps it from running is some advanced function of DX 9 that hasn't been implemented in Wine yet. While the Direct3D functions of DX 9 are about 95% complete, many of the DirectInput, DirectShow, DirectMusic and other DX support functions are less than 50% complete:
[http://www.winehq.org/site/status_directx](http://www.winehq.org/site/status_directx)

---

### Post by bastiegast on 2007-12-10
Even though directx9 is about 95% complete as you say, performance is not very good to say at least.

---

### Post by cogadh on 2007-12-10
> **bastiegast said:**
> Even though directx9 is about 95% complete as you say, performance is not very good to say at least.
No I said Direct3D is 95% complete, there is much more to DirectX than just Direct3D. Direct3D performance is nearly as good as it is on Windows (depending on the game).

EDIT - Actually, if you combine status of all of the Direct3D DLL's plus all of the support DLLs that are not directly part of Direct3D but may be required for full Direct3D functionality, it's probably about 20-30% complete. However, the core Direct3D DLLs are 95% complete and you can usually get around the incomplete status of the support DLLs with library overrides.

---

### Post by dethredic on 2007-12-10
So it will be more than a couple months before Crysis is playable?

Guess I better reinstall windows :P

---

### Post by Sockerdrickan on 2007-12-10
You think it's *that* good?

---

### Post by dethredic on 2007-12-10
Yes. :P

Well, possibly, but I found out I am getting it for Christmas, and I would like to play it.

---

### Post by Sockerdrickan on 2007-12-10
Don't get your hopes up!

---

### Post by bastiegast on 2007-12-10
> **cogadh said:**
> No I said Direct3D is 95% complete, there is much more to DirectX than just Direct3D. Direct3D performance is nearly as good as it is on Windows (depending on the game).

EDIT - Actually, if you combine status of all of the Direct3D DLL's plus all of the support DLLs that are not directly part of Direct3D but may be required for full Direct3D functionality, it's probably about 20-30% complete. However, the core Direct3D DLLs are 95% complete and you can usually get around the incomplete status of the support DLLs with library overrides.

Which is what i meant, direct3d. I know I am going to give an isolated example and direct3d might not be the cause of my trouble but for me switching from dxlevel 81 to 90 in portal and hl:ep2 results in a massive performance drop. Note that I am pretty much able to play on high settings, dx9 in windows. So from that logic performance is not that good. Well it'll probably be one of those 5% that is not complete that is causing the slowdowns.

---

