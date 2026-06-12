---
title: "2 odd glitches when trying to play any game in wine"
date: 2011-07-17
forum: Wine
---

### Post by NT2015 on 2011-07-17
OK I'm having 2 odd problems that I've never noticed until i bought myself a new video card (Radeon HD6850). When ever I go to play a game in wine, any game, two things happen that really annoy the crap out of me. 

1. My second monitor is disabled every time I launch a game, and when I quit the game I have to go back into Catalyst to re-enable it every single time. (This bugs me, because I actually like using my second monitor during games)

2. The "Identify Display" numbers pop up as soon as the game is launched. If you dont know what I'm talking about, they are the red squares with numbers in them that pop-up in the top left corner of each of your monitors when you click the "Identify Displays" button in the AMD CCC. The issue is that these numbers pop-up when I launch my games, however CCC is not running when this happens.

I have not been able to make any progress toward the first issue. However I have made small progress towards the 2nd. I have found that if I open AMD CCC prior to launching the game, and then I alt + tab out of the game and close the CCC the red numbered squares will go away. Unfortunately this fix is not desirable because 9 times out of 10 alt + tabing out of a game running in wine will cause the game to crash, and starting the whole cycle again...

Almost forgot, I'm running Kubuntu 11.04 with Wine 1.3.23

---

### Post by NT2015 on 2011-07-25
Bump.....

---

### Post by NT2015 on 2011-07-29
Is there anyone who can at-least point me in the right direction?

---

### Post by brian70809 on 2011-07-30
is wine running in windowed mode?  Try doing that and if you can, get the game to run in windowed mode within it's own config.  This seems to solve a lot of the monitor issues.

I have not had an ATI card in a long time, is it possible to have the driver loaded without Catalyst or are they one in the same now?

---

### Post by NT2015 on 2011-08-03
Sorry for taking so long to get back, I assumed the thread was dead. But yes running games in "Windowed (Fullscreen)" works perfectly, they even integrate into my kwin alt+tab effects. 

However, is there a way to force this Windowed full screen mode? Very few of the games I play support this feature. As a matter of fact the only games I have that do are Half-Life 2 series, Portal series, and WOW. Is there a way to force all games to play in that windowed fullscreen mode?

---

### Post by schtufbox on 2011-08-10
In wine options  you can set it to run in a window but the windows app believes it's running fullscreen and thus works.
I'm at work right now and can't remember the exact names of the option, but it's under the graphics tab of wineconfig.

---

