---
title: "GTA:SA problem."
date: 2008-08-29
forum: Wine
---

### Post by Whisper45 on 2008-08-29
Hey. I'm having problems with my GTA San Andreas game. First of all, I've installed Wine, and the game works. The problems are that its verry jumpy and laggy when I enter a vehicle, also, the cars are simple frames, just black. This is either my Graphics driver, or my Direct x is not up to date.

I've tried installing a graphics driver from the nVIDIA website, but I have had LOTS of trouble installing it, which in the end, ended up me having to re-install ubuntu.

As for the Direct x, does anyone know where I can download Direct x 9.0 for ubuntu, which is what the game requires to be played.

Thanks.

Yours,
Whisper.

---

### Post by Whisper45 on 2008-08-29
:o sorry, justread the stikki, please can you move it to > [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Thanks!

---

### Post by Whisper45 on 2008-08-29
Sorry for yet again another post but I forgot a detail: After I closed GTA:SA the resolution sets itself BIG.

---

### Post by Whisper45 on 2008-08-31
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2599](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2599)

it doesnt say anywhere on there that it doesnt work with wine...?

---

### Post by Whisper45 on 2008-09-18
bump

Please help :)

---

### Post by aoanla on 2008-09-18
Firstly, you want to use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install the latest nVidia drivers for your card.

Secondly, the AppDB entry /does/ mention that pixel and vertex shaders can be a problem for this game under Wine. Use winecfg to fiddle with the settings for shaders and see if that helps with the display.

Thirdly, there's no such thing as "directx for ubuntu" - DirectX is a Microsoft Windows API for multimedia applications (but mainly, now, a 3d graphics API). It is not available for any other platform. 
One of the things Wine does that makes Windows games work in Linux is to map DirectX function calls onto OpenGL function calls (OpenGL being an open standard API for 3d graphics). Thus, Wine is doing "DirectX 9.0" for you.

---

