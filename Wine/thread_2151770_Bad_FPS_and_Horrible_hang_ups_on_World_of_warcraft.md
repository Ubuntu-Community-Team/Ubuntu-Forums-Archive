---
title: "Bad FPS and Horrible hang ups on World of warcraft!"
date: 2013-06-05
forum: Wine
---

### Post by mcsweeney on 2013-06-05
So i've heard wine and World of Warcraft are suppose to run wonderfully together but i've had nothing but troubles! When in combat or sometimes just running around i get horrible freeze up or lag spikes and my MS will jump from 300ms to red 1000ms but with no noticeable lag expect for a few seconds! I also notice HORRIBLE Fps (20-30 never more then 40) while in most places (its wine i understand it wont run perfectly)

Specs:
CPU: Intel core i-7 920
Gfx card: Nvidia GTX 260 (313 Proprietary Drivers)
Mem: 6gb of DDR3
WIfi USB adapter: Cisco (Linksys AE1000)

Wine Setup:
Has it own PoL Wine prefix to its self.
Wine Version 1.5.31

---

### Post by deri on 2013-06-05
Don't have the game, haven't played it under linux. Are you sure that your ping is ok? Don't know how to help in this case.

---

### Post by mcsweeney on 2013-06-05
> **deri said:**
> Don't have the game, haven't played it under linux. Are you sure that your ping is ok? Don't know how to help in this case.

Sorry should have clarified that i actually have a Windows laptop right be hide me playing the game perfectly with maxed out settings and perfect ping, never had a single hang up on it. Both on the same network.

Also Opengl mode does not help.

---

### Post by Tweak42 on 2013-06-05
Can you try using wired ethernet instead of the USB wireless?  I googled around and there have been problems with getting linux drivers working for the Linksys AE1000 in the past, although the silence of recent post seem they may have work themselves out (or people stopped using them).

Also try rolling back to an older set of nvidia drivers, perhaps 304.x or 310.x series.

You didn't state what version of Ubuntu you are using, because the stock Unity3D desktop environment uses compiz which can interfere with 3D performance.  There several work arounds for that depending on how far you're willing to go.

---

### Post by deri on 2013-06-05
What's your linux and kernel?

---

### Post by Cvxcvgg on 2013-06-05
This may seem a bit simple, but have you tried turning down some of the settings? Some games, MMOs especially (in my experience), have a lot of post-processing or bloom effects, which can really eat up your FPS in combat. I would also lower any physics debris limits or anti-aliasing/anistropic filtering settings. If you've tried that, I would suggest playing on your awesome windows computer, seeing as it's right next to you. ;) Also, while you may have 6 GB of DDR3 RAM, what matters more is the RAM on your graphics card, unless you're using some of that DDR3 as virtual memory. I looked up your card, and its specifications say it is only loaded with about 900 MB. Other than that, I don't see too many other possible causes.

---

### Post by mcsweeney on 2013-06-05
Sadly no because of the location of the computer and i did try the installing of the drivers but it seemed to be more of a fix for 10.10 and 11. Im gonna try the drivers roll back and im using the latest 13.05 with stock kernel.

Also Cvxcvgg the laptop is a friends. The GTX 260 is still overkill for WoW, i mean i know im not gonna be getting max performance because its going threw wine, my bigger issue is the Random lag/Freeze ups where i cant control anything and generally wipe a Random group of people.

---

