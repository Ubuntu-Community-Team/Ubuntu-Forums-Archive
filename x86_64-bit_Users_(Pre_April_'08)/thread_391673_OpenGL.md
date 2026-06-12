---
title: "OpenGL?"
date: 2007-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by SavageNick on 2007-03-23
Hi - installed my 64bit edgy a little over a week ago and really enjoying it. There is 1 rather large problem however. I've literally only just realised why I have such rubbish fps in 3D apps - because they are all 32 bit apps. I just downloaded the UT2004 64 bit demo and it runs perfectly on my system (Ati x1950 pro) - so all the stuff about direct rendering etc was true after all!

This leaves me with a rather large problem - all my hardware works on 64 bit ubuntu - but I want to play 32 bit games etc properly, should i reinstall the 32 bit version instead?

The only way 32 bit apps even accepted I had rendering switched on was after I installed the ia32-libs package - I have a feeling that for some reason the 32 bit opengl drivers that are in that package use software (or just plain don't work properly) - any way I could fix it?

I REALLY REALLY dont wanna uninstall 64bit - but if thats the only way I can get 3D programs working properly, I'll have to I spose...

Any ideas guys?

---

### Post by xopher on 2007-03-24
Well the ia32-libs do, in a way, make your system 32bit - for that particular app/game that uses them at least.

So that shouldn't be the reason for games behaving like that.

How have you installed your gfx-card drivers? You are using fglrx right? What games have you tried?

---

### Post by SavageNick on 2007-03-24
Yeah I've installed the fglrx drivers - and everything is "working" i.e. direct rendering is enabled and glxinfo reports using the ati drivers. I'm using the latest ones from the ati website.

The problem I have is that all x64 3d apps work perfectly (using my 3d card) but 32 bit apps have appalling framerates. Is it possible that the ati drivers didnt install the 32 bit drivers properly? How could I check?

---

