---
title: "Diablo III not starting with POL : Shell running endlessly"
date: 2014-04-24
forum: Wine
---

### Post by matthieu.astro on 2014-04-24
Hello
 
I've a persistant problem with Diablo III.
 
_Diablo III worked correctly on my computer running with Ubuntu 13.10_ with Wine and PlayOnLinux. Few days ago I upgraded it to Ubuntu 14.04 LTS and since I did it, DIII doesn't run anymore. The shell show me the same endless 3 lines following :

 ```
direct3d9 is not available without opengl
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
```
 
I've already checked than OpenGL is installed (and it is). I've checked wine configuration and I've not seen anything unusual. I've done also internet researches and I found lot of things but all I see was concerning nvidia graphic card and I have an _Intel® Sandybridge Mobile_ one. So I don't know what are the equivalent manips for this kind of card.

I tried to uninstall and purge wine and POL. I also removed all DIII directories. Then I installed again everything from the battlenet downloaded launcher. There was no problem to install again DIII. However I receive an advertising message : my graphic card hasn't enough memory to allow the game running correctly. _It is the first time this message appears_ and I can't work out why because DIII worked well before upgrading.
 
Now I still can't make the game running but symptoms are a bit different. I start by running DIII in a shell. Then battlenet conexion run perfectly. Next computer propose me to play and when I click on « play » the shell doesn't show me the direct3d9 error, but run without neither stop nor lead to something.
 

 My material :
 OS : Ubuntu 14.04 LTS 64 bits
 Memory : 3.8 Gio
 Processor : Intel® Core&#8482; i3-2330M CPU @ 2.20GHz × 4
 Graphic Card : Intel® Sandybridge Mobile
 Disc : 625,8 Go

---

### Post by matthieu.astro on 2014-04-27
up.

I've still the same problem and I haven't succeed to resolve it.

---

