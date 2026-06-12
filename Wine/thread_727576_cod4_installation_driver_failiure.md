---
title: "cod4 installation: driver failiure?"
date: 2008-03-17
forum: Wine
---

### Post by Bölvaður on 2008-03-17
I was installing COD4 the other day with WINE 0.957 without a problem. Then when I ran it for the first time, it complained:

```
----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
----- R_Init -----
Getting Direct3D 9 interface...
Pixel shader version is 3.0
Vertex shader version is 3.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support enough textures for the DirectX 9 code path.


Error during initialization:
Video card or driver doesn't support enough textures for the DirectX 9 code path.
```

I had the newest driver for my video card and also reinstalled it via Envy.

My card is 8800GTS 320MB.

I have been running this game on my other OS which I use only to play that single game, and Im getting tired of having to restart the computer.


So... what's up?

---

### Post by Jimmey on 2008-03-18
I can't help you much at the moment because I'm in college, but try running ```
winecfg
``` from a terminal and fiddling with the graphics settings.

---

### Post by Bölvaður on 2008-03-18
I just tried Unreal Tournament 2004 which has DirectX 9b (COD4 had 9c).
UT works in a retarded manner, but the graphics doesn't seem to be flawed.
What can I fittle with in wine config? I don't see a lot of options in the gui.

---

### Post by Jimmey on 2008-03-18
I'm pretty sure there's an unreal tournament client for linux anyway, that shouldn't need to be run through wine.

---

### Post by Bölvaður on 2008-03-18
yes there is, it was just a random game to check if the driver worked at any level at all.

so.. 

DirectX 9b works
DirectX 9c ? unknown ?

but there is a problem with the video still with cod4. cant get to the start menu even.

---

### Post by Bölvaður on 2008-03-19
common, does no one know? :(

---

### Post by spacholka on 2008-06-23
I've been getting the same error as well.

" Video card or driver doesn't support enough textures for the DirectX 9 code path"

I followed the COD4 tutorial PDF but no luck.

Any ideas folks?

---

### Post by FlyingIsFun1217 on 2008-06-23
> **spacholka said:**
> I've been getting the same error as well.

" Video card or driver doesn't support enough textures for the DirectX 9 code path"

I followed the COD4 tutorial PDF but no luck.

Any ideas folks?

Check the listing in Wine's [AppDB]("http://appdb.winehq.com/"). People usually post info on how to get certain programs running.

FlyingIsFun1217

---

### Post by W A L E E D on 2008-12-11
[FONT="Arial"][SIZE="4"][COLOR="Navy"]Hi everybody.
I have the same problem now with Call of Duty 4 - Modern Warfare.
```
----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
----- R_Init -----
Getting Direct3D 9 interface...
Pixel shader version is 3.0
Vertex shader version is 3.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support enough textures for the DirectX 9 code path.


Error during initialization:
Video card or driver doesnt support enough textures for the DirectX 9 code path.
```
any idea how to solve it?
Thanks.[/COLOR][/SIZE][/FONT]

---

### Post by Sifilis on 2008-12-14
> **W A L E E D said:**
> ~cut

any ideas? i'm installing cod5 and it requires directx 
"Video card or driver doesn't support enough textures for the DirectX 9 code path."
why isn't life simpler..

---

### Post by GEARSOFWAR on 2009-01-10
I have the same problem if any one noes how to fix this please write back

---

### Post by orlox on 2009-01-10
There is a howto on getting this to work at appdb:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804)

---

### Post by Brackenn on 2010-01-08
I've got the same error: 

Getting Direct3D 9 interface...
Pixel shader version is 3.0
Vertex shader version is 3.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support enough textures for the DirectX 9 code path.

...and all that.
I'm running 9.04, I have a Nvidia 9500 card, and I'm running the x86-185.18.36-pkg1.run driver. this should be able to handle it. there is a newer driver for download on the nvidia website here===>[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)
I haven't tried it yet. Don't know if it will help.
Would it make any difference if i downloaded the windows driver, and ran it inside of wine?

---

### Post by Bölvaður on 2010-01-14
> **Brackenn said:**
> 
Would it make any difference if i downloaded the windows driver, and ran it inside of wine?

I wouldn't make sense as Linux handles the hardware and wine just uses it's resources, there is no windows kernel running on the hardware when you run wine.


I am not sure if cod4 works now or not. But I have been able to play it on low framerate, cannot remember if it was before or after this post.

things that may help.
use the latest distro, like ubuntu 9.10
follow the how-tos on winehq.org about how to config wine
use winedoors or winetricks.

---

### Post by vitruxv on 2010-10-03
I know this might be out of date, but I had the same issue and went to winecfg - graphics- checked the box to allow pixel shaders.

---

