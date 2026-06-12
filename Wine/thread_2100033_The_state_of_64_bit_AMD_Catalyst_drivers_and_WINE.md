---
title: "The state of 64 bit AMD Catalyst drivers and WINE"
date: 2012-12-31
forum: Wine
---

### Post by KBentley57 on 2012-12-31
I've been using Ubuntu for quite some time now, and also WINE.  I have looked high and low, and haven't really found a satisfactory answer to my questions regarding the AMD drivers for x64 Ubuntu and WINE interaction.  First, my system specs:

AMD Phenom II 1090T @ 3.6 GHz
16 GB DDR3 1600 MHz @ 8-8-8-24
790 FX Chipset
AMD 6970 2 GB GPU @ stock
750 W OCZ GameStream PSU
Ubuntu 12.10 x64
fglrx-updates and
fglrx-amdcccle-updates
WINE version - currently 1.5.10 and 1.5.20 with PoL.
22" 16:9 at 1080 res.

Of all the game's I've played under WINE, I don't suspect that any of them have really used the AMD binary fglrx driver.  For example, Running left 4 dead 2 under WINE gives me something about 30 fps, regardless of the settings used.  My system would rip this game apart on windows, on the order of hundreds of fps.  StarCraft II on ultra gives me 16-20 fps, and on all low settings gives me only 25-30 fps.  Other games gives similar performance.  From what I've been reading, this has something to do with wine being 32 bit, and my graphics drivers being 64 bit.  I understand that the fglrx blob from the repos supposedly installs both 32 and 64 bit modules, but I could be mistaken there.

So, am I not doing something completely obvious?  Or is the issue with my system different than I realize?  I don't expect an equivalent frame rate of a windows system, however I know that it shouldn't be this low.  Using aticonfig --od-getclocks shows that the gpu isn't really being utilized at all during game play, and I'm wondering if all I'm actually doing is software rendering.

Any advice?

---

### Post by KBentley57 on 2013-01-02
Bump

---

### Post by KBentley57 on 2013-01-07
I really do hate to double bump; last time.  Promise.

---

### Post by ZombieApocalypse on 2013-01-10
From what I've read and from my own experience, the problem is down to poor driver support from AMD. This is my set-up:

Kubuntu 12.10 64-bit (dual boot with Win 7)
 AMD Catalyst 12.11 beta (fglrx)

 AMD Phenom II X4 965 @3.4 GHz 
 XFX AMD/ATI HD5850 1GB
 8GB DDR3 (1333MHz)

I have tried Left 4 Dead through WINE and Killing Floor through the Steam linux beta client. In both games performance is poor and barely improves if I lower the graphics settings. Although my system is not as powerful as your, I can max these games out in Win 7 and get frames rates in excess of 100 fps (though I usually stick on v-sync and cap at 75fps). 

AMD have now set up a page on their forums regarding the Linux Steam client ([http://devgurus.amd.com/community/steam-linux](http://devgurus.amd.com/community/steam-linux)), so hopefully they will start to take their Linux support more seriously. However, I'm seriously considering a Nvidia card for my next upgrade as their driver support is reputedly vastly superior in Linux and people are reporting good performance in 3D games.

---

