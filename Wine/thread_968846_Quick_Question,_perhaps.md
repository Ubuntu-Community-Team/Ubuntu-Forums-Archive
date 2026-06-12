---
title: "Quick Question, perhaps?"
date: 2008-11-03
forum: Wine
---

### Post by SanctusMessor on 2008-11-03
I am trying to get Guild Wars up to speed on my new install of Ubuntu 8.10 64-bit. This guide 

[http://tombuntu.com/index.php/2007/04/01/guild-wars-on-ubuntu-with-wine/](http://tombuntu.com/index.php/2007/04/01/guild-wars-on-ubuntu-with-wine/) 

informs me to:

> To improve performance, run Wine’s regedit program and add these strings to HKEY_CURRENT_USER\Software\Wine\Direct3D.

    * “DirectDrawRenderer”=”opengl”
    * “OffscreenRenderingMode”=”backbuffer”
    * “opengl”=”enabled”
    * “RenderTargetLockMode”=”auto
    * “UseGLSL”=”disabled”
    * “VideoMemorySize”=”256&#8243;


I don't know how to do the "run Wine’s regedit program" part... also, while going through this I began to wonder if this has been discussed and if there is a more solidified and/or recommended way to get Guild Wars up to speed. My rig stats are below.

C2D E4600 2.4GHz
G.Skill 4 GB DDR2 (4x1GB)
W.D. 500GB HDD (2x250)
EVGA nVIDIA 680i LT
EVGA nVIDIA 8800GTX

---

### Post by MonkeyBoy on 2008-11-03
The regedit feature can be opened by typing regedit on the cli.

I have found that adding the following flags to my Guild Wars launcher have made the game run perfectly well: ```
-dsound -noshaders -dx8 flags -repair -image WINEDEBUG=-all
```For this reason I have never bothered to alter the registry settings.

If you have tried these and Guild Wars runs well, there probably isn't any need to edit the registry. 

Good luck with it.

---

### Post by SanctusMessor on 2008-11-03
> **MonkeyBoy said:**
> The regedit feature can be opened by typing regedit on the cli.

I have found that adding the following flags to my Guild Wars launcher have made the game run perfectly well: ```
-dsound -noshaders -dx8 flags -repair -image WINEDEBUG=-all
```For this reason I have never bothered to alter the registry settings.

If you have tried these and Guild Wars runs well, there probably isn't any need to edit the registry. 

Good luck with it.

Thanks ^_^

---

