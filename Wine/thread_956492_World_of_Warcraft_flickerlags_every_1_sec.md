---
title: "World of Warcraft flicker/lags every 1 sec"
date: 2008-10-23
forum: Wine
---

### Post by Jepperen on 2008-10-23
Hey

Im enjoying Ubuntu very much, everything is better greater and faster than Windows :D

But when im gaming world of warcraft the game lags/hacks every 1 sec, which is very distubing. It know that the computer can run the game without any problems, because i ran it fine when i used Windows.

The game runs smooth, but then its like it just stop for a very short time. I have no problems with the game running badly bedside it lags every 1 sec.

Anyone know a solution?

I have a mobile Ati x1600 graphic and i installed the lastest driver which Ubuntu recomments.

---

### Post by wownerd87 on 2008-10-23
Well to start off, there a lot of variables of this situation. Try logging on a different toon than your on. and try one that is out of a capital city. etc. tell me if it still does it.

---

### Post by Jepperen on 2008-10-23
ok... i tried with a different char and its the same problem. I notice that it does'nt do it when im in a house or other "small areas"...?

---

### Post by gjoellee on 2008-10-23
Have you set WoW to run in OpenGL? IN your installation directory go to WTF->Config.wtf or RunOnce.wtf and add the following line: ```
set gxAPI "OpenGl"
``` save and close. You may now start playing!

---

### Post by Jepperen on 2008-10-23
yep.

Additional info is that when i run on the run in Duskwood it doesnt do it eihter. Hmm...

---

### Post by Jepperen on 2008-10-24
anyone have anohter suggention?

---

### Post by hikaricore on 2008-10-24
> **Jepperen said:**
> I know that the computer can run the game without any problems, because i ran it fine when i used Windows.

I first want to point out that this kind of logic is flawed.
If your video hardware has poor or no OpenGL support and or the drivers
ATI provides for Linux handle OpenGL badly then you will have trouble.
(^ I can't say if this is the case or not, just providing an example)

A LOT of video hardware these days relies on DirectX (vendor lockin much?)
and supports OpenGL very badly such as many Intel video chipsets.
Regardless of it running fine in ***dows.

Moving right along, are you using any advanced window managers such as Beryl/Compiz or using desktop effects?

---

### Post by Jepperen on 2008-10-25
Thank you for your detailed answer. I do not know if my videocard supports OpenGL badly. My videocard is a Mobile X1600 from ATI and im using the drivers that Ubutuns auto update offers.

I dont know what Berly/Compiz is? But im swicting off all Desktop effects before i start the game, ohterwise the screen goes crazy with flickering the desktop in the game.

So i just have to live with my problem about the constant flicker once every 1 second?

---

