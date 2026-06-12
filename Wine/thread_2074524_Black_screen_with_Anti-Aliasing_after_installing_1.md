---
title: "Black screen with Anti-Aliasing after installing 12.10"
date: 2012-10-21
forum: Wine
---

### Post by relik1989 on 2012-10-21
I am having issues with Anti aliasing in wine since freshly installing 12.10 64bit. 

System Spec:
Ubuntu 12.10 64bit
Wine ver 1.5.15
AMD Phenom II X4 955 @ 4GHz
AMD Radeon HD 7870 (Using fglrx provided by Ubuntu)

The game in question is World of Warcraft. I have never run WoW in OpenGL simply because DirectX mode offers AA, Shadows, and higher water detail. Earlier today in 12.04 I was playing wow, 8xAA, High Shadows, Fair water, etc...(basically as high as it will go in wine) I was getting about 50-60fps. 

After reformatting and installing 12.10 any time I enable AA the screen goes black. When this happens, I still have full sound, and I can still see/move the cursor. I do not know what could be causing this issue. 

I have tried the following:
-Running in OpenGL mode: Works fine but not what im trying to accomplish.

-Enabling the AA registry key in wine: nothing

-Changing "Offscreen rendering mode"
           -FBO: nothing
           -pbuffer: nothing
           -backbuffer: works, however when using this mode there is a very large square on the screen that basically shows a flipped copy of the world.

-Changing between 32bit and 64bit prefixes: nothing

-Tried several different versions of wine: nothing

-Forcing AA in Catalyst Control Center (AMD Driver): nothing

-Tried both "fglrx" and "fglrx-updates": nothing

This is getting very frustrating for me today. So far I'm not thrilled with 12.10 as this is the 3rd issue I've had so far. Albeit this one is pretty minor compared to the other two. 

Can anyone help me out on this?

EDIT: I found more issues. Even in OpenGL there&#8217;s are what appears to be large amounts of missing textures. I believe it may be a shader issue or something along those lines. I noticed it mainly in a hallway which I know has a bit of lighting effects, and everywhere there should have been light there was just transparency. Example was that I could see right through the floor, I can see through large parts of the walls. If anyone wants I can take some screen shots.  All I know is that something is really wrong here.

---

### Post by netrick on 2012-11-24
I have the same problem in Guild Wars. In 12.04 64 bit everything worked perfectly, in 12.10 64bit without anti aliasing guild wars runs great, but when i set anti aliasing i just get black screen (i only hear sound and have the in-game cursor, and nothing more). My gpu is radeon hd 6870. I tested both fglrx and fglrx-updates, wine 1.4, wine 1.5, play on linux's wine versions and the bug is everywhere. Using nvidia gpu, there is no problem. Is there any workaround? I love 12.10 but it looks like I must go back to 12.04 :(

Thanks!

EDIT:
I changed drivers to default open source amd drivers and the bug is still present. Damn, on 12.04 everything works fine, I have no idea... I hope you guys can help me.

---

