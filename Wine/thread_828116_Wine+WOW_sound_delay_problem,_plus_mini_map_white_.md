---
title: "Wine+WOW sound delay problem, plus mini map white indoor"
date: 2008-06-13
forum: Wine
---

### Post by chuugokujin on 2008-06-13
Ubuntu 8.04 + Wine 1.0 rc4 + ATI x850x

sucessfully run WOW finally, but there are some glitches:

1) Sounds delay for like 0.5s or 1s when in the game, should I go winecfg->audio to change something?

2) The minimap becomes all white when you go into indoor world.
Any indoor houses, or even Iron Forge, or middle of Shat City. I have searched some posts it seems it's an unfix glitch up todays?

Thanks!

---

### Post by Faud on 2008-06-13
I dont know about the sound... do you have it on alsa drivers ? The white minimap is due to your ATI card and there is currently no fix.  The good news however is that ATI is working on the fix for it and hope to have the fix released in the next couple driver updates to their linux buyers.

---

### Post by chuugokujin on 2008-06-19
> **Faud said:**
> I dont know about the sound... do you have it on alsa drivers ? The white minimap is due to your ATI card and there is currently no fix.  The good news however is that ATI is working on the fix for it and hope to have the fix released in the next couple driver updates to their linux buyers.

I have esound as the sound driver, and I installed pulseaudio-esound package. If you choose either Alsa or OSS there is no sound out.

I really hope ATI would pay attention to so many problems under Linux. They will be defeat by nVidia in a long term if they still keep their door closed. BTW, does nVidia cards have this problem?

---

### Post by reinderien on 2008-08-03
> **chuugokujin said:**
> Ubuntu 8.04 + Wine 1.0 rc4 + ATI x850x
(...)
2) The minimap becomes all white when you go into indoor world.
Any indoor houses, or even Iron Forge, or middle of Shat City. I have searched some posts it seems it's an unfix glitch up todays?

Thanks!

I'm running the same version of Ubuntu, (probably) the same version of Wine, just the one that comes from apt; and an ATI Mobility Radeon M200, and have the same white minimap problem. I ditched my Windows partition when I got WoW working in Wine and this is more or less the only glitch left to fix. If I find out any solution I'll post here.

---

### Post by dre_in_ham on 2008-11-30
Hi, i have the same 2 issues on 8.10 and i didnt have them on 8.04!
Since there is a new fglrx in 8.10 that could well be the issue with the mini map. As for the sound, im not sure if anything is different in the 8.10 release (i used pulse in both). 

I additionally have bad sound quality in 8.10 which i didnt have in 8.04, any ideas on this? I will try setting it to OSS and report back.

UPDATE: setting the sound to OSS in winecfg works like a charm. I have a good frame rate and good sound in wow! Only issue left is the minimap...

Im using wine 1.1.9
 
Have you checked [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ?

---

### Post by DarkenSX on 2009-07-22
This Problem Is not Just A linux thing OpenGL does it to wow in windows too Except in windows instead of it being white it doesnt show up at all people have reported it being fixed by running the game in direct3D mode untill it is resolved with openGL by either Blizz or AMD/ATI I Dont Know How well The Game works in D3D yet to test it. might vary from Machine to Machine So I'll Report back on this once i test it or someone else can whatever happes happens if you do report please list the specs of your machine with the results.

---

### Post by bcboybuzz on 2009-08-09
C2D e8400 Radeon HD 4850 Ubuntu 9.04 WoW does run in D3D, but is laggy even with all settings at minimum... AA locked out [unable to go past 1x]...but at least i can see the frickin indoor minimap...

---

### Post by Mahinva on 2009-08-09
> BTW, does nVidia cards have this problem?

From my experience, no. I played WoW on a rather old nVidia card (GeForce 5500FX) and never had my minimap appear white while indoors, and I have never read of a white minimap occuring for other nVidia users.

The white minimap problem with ATI has existed for a while - a fix would be nice for ATI users but do not hold your breath. If you're using minimap for instances, definitely look into an instance map addon if you don't use one already.

---

