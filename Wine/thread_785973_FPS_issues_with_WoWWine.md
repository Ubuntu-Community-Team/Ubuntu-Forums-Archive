---
title: "FPS issues with WoW/Wine"
date: 2008-05-07
forum: Wine
---

### Post by cjules86 on 2008-05-07
I have WoW running (following the ubuntu howto) using ubuntu 8.04 amd64 and wine version 0.9.59.  I don't notice any graphical problems.  But, when playing in windows xp, in a busy pvp area I will get around 35-50fps.  In ubuntu, I'm getting 10-20fps which for me, is unplayable.  I was wondering if anyone else is having this issue.  I'm fine dual booting windows xp for WoW but would really like to get it running perfect in Ubuntu as it is the only reason I have to dual boot atm.

I've tried almost all the tweaks and tricks I have found out there (been trying to fix this issue for months since I had the same problem in 7.10 as well), none of them seemed to help.  Any help you guys could offer would be appreciated.  Let me know what specs on my setup you guys need, if any.

---

### Post by gaspard.leon on 2008-05-07
yep this is the main problem with WOW / Wine...

Slower then Windows...

My friend was using Ubuntu with WOW but it was too slow in the end (he's a big WOW player) so he had to switch back to windows XP

no fault of Wine folks, at least it works, which is pretty impressive!!

you might try low graphics settings, but likely you'll find it's the still a little too slow for regular use.

---

### Post by Trance56k on 2008-05-07
What kind of video card do you have? I have a 8600GT and WoW runs great. I average about 60-100fps with almost everything turned up.

---

### Post by cjules86 on 2008-05-07
8600gt 512mb vid card.  I usually average around 80-100fps idling around main cities (not shatt) on my XP partition.  I do get 80fps once in a blue moon when running past a very dead and low graphic area with wine but usually it averages around 40-50 in the same areas that I'll get the 80-100fps with XP.

EDIT: This is with pretty much all settings to the max (same settings in wine as in xp)

---

### Post by jbysmith on 2008-05-07
> **Trance56k said:**
> I have a 8600GT and WoW runs great. I average about 60-100fps with almost everything turned up.

Ditto that, on a 7800 GS-OC.  (Wellllll not quite that fast, but fairly close) Wasn't much tweakery on my end.  Just made sure to use the proprietary drivers. set WoW to run in OpenGL mode, and applied the one OpenGL registry change that's on the AppDB.  Even in busy areas getting a very good framerate, typically at or better than XP speed, with all settings at maximum and Compiz running.  If I disable Compiz, it goes through the roof. (This is on Ubuntu 7.10 with a self-compiled 0.9.61 Wine, 8.04 isn't playing nice for me yet)

---

### Post by thisismalhotra on 2008-05-08
> **gaspard.leon said:**
> yep this is the main problem with WOW / Wine...

Slower then Windows...

My friend was using Ubuntu with WOW but it was too slow in the end (he's a big WOW player) so he had to switch back to windows XP

no fault of Wine folks, at least it works, which is pretty impressive!!

you might try low graphics settings, but likely you'll find it's the still a little too slow for regular use.

I dont know about your issues but FPS is not a problem with wine, I play with an 8800 GT and my server latency, FPS and everything else is always and consistently better than windows xp/vista ... must be something in your settings ...

---

### Post by thisismalhotra on 2008-05-08
> **cjules86 said:**
> 8600gt 512mb vid card.  I usually average around 80-100fps idling around main cities (not shatt) on my XP partition.  I do get 80fps once in a blue moon when running past a very dead and low graphic area with wine but usually it averages around 40-50 in the same areas that I'll get the 80-100fps with XP.

EDIT: This is with pretty much all settings to the max (same settings in wine as in xp)

I assume you have done ll the config.wtf changes and regedit for wine. All you need to try now is to get dll's and see if they help out..

look at this page...

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by cjules86 on 2008-05-08
Hmm I haven't tried the dll's I'll try that today and hopefully see some results :)

---

### Post by cjules86 on 2008-05-08
I don't want to jinx it but it seems the dll's fixed it.  The fps still isn't what it should be but the game is playable.  It drops down to the 20's once in a while but it seems ok.

---

### Post by Fire_Missionary on 2008-05-09
I have found that sometimes running in D3D (directx) instead of OpenGL in WoW yields higher framerates.

Although I'm fine with it looking crappy as long as I get 60+ FPS.
Usually I run it at minimal graphics settings and in D3D, I get constant 40+ in high activity areas. Mind you, Shattrath and EOTS still have framerate drops for me, but WSG, AB, and AV are good.

Just suggesting D3D instead of OGL because it works for me for increasing framerates.

AMD Phenom X4 Agena 9500 @2.2Ghz Quad-Cor
4GB (4x1GB) DDR2 800mhz 
nVidia 7900GTX 512mb

---

### Post by Fairmantium on 2008-05-09
> **cjules86 said:**
> I have WoW running (following the ubuntu howto) using ubuntu 8.04 amd64 and wine version 0.9.59.  I don't notice any graphical problems.  But, when playing in windows xp, in a busy pvp area I will get around 35-50fps.  In ubuntu, I'm getting 10-20fps which for me, is unplayable.  I was wondering if anyone else is having this issue.  I'm fine dual booting windows xp for WoW but would really like to get it running perfect in Ubuntu as it is the only reason I have to dual boot atm.

I've tried almost all the tweaks and tricks I have found out there (been trying to fix this issue for months since I had the same problem in 7.10 as well), none of them seemed to help.  Any help you guys could offer would be appreciated.  Let me know what specs on my setup you guys need, if any.

I am having the same issue as you.  When i was running XP, i was getting 60+ FPS even in the most crowded areas of shattrath with all the details at maximum.  However, while running WoW with wine 0.9.61 in Ubuntu 8.04 under OpenGL, I have noticed that in the same areas of Shattrath I am now getting around 20-25 FPS.  During raids I used to get 60+ FPS also, and now i have to stare at the ground to heal people as my FPS drops down into the teens during AoE groups, etc.  I've tried the registry edit and adding the DLLs in the above post and it didn't improved the framerate any.  I'm running a Geforce 7900 GS with the most recent drivers.  Any other suggestions would be appreciated.

---

