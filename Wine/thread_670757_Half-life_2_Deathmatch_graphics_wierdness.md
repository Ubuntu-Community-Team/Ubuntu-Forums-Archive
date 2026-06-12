---
title: "Half-life 2: Deathmatch graphics wierdness"
date: 2008-01-17
forum: Wine
---

### Post by Envergure on 2008-01-17
I've been using Ubuntu 7.10 for just over two months now.  Possibly the only thing I miss about Windows XP is Half-life 2: Deathmatch.

After a bit of trial and error I got it to run in Wine :biggrin:.  The sound, which seems to be the most common problem, actually worked fine.  The problem for me is the graphics:
[View attached screenshot.  It's the map with all the toilets]

Oh, and there isn't any text in the menus, which makes starting games very difficult.

I haven't got a clue what's causing this.  Any ideas?

---

### Post by The Noble on 2008-01-18
> **Envergure said:**
> I've been using Ubuntu 7.10 for just over two months now.  Possibly the only thing I miss about Windows XP is Half-life 2: Deathmatch.

After a bit of trial and error I got it to run in Wine :biggrin:.  The sound, which seems to be the most common problem, actually worked fine.  The problem for me is the graphics:
[View attached screenshot.  It's the map with all the toilets]

Oh, and there isn't any text in the menus, which makes starting games very difficult.

I haven't got a clue what's causing this.  Any ideas?

Try turning off HDR or bloom. I played through half life 2 with version .9.52 a couple weeks ago, and .9.53 seemed to work with some minor graphical glitches. What version of wine are you using? Perchance that is the problem.

Also, do you have a ATI card? Make sure that you have fglrx drivers before even trying to game. I also had troubles a while back while trying to game using wine with ATI, but I never confirmed it to be a problem with ATI.

---

### Post by Envergure on 2008-01-18
I can't change the graphics options because there isn't any text in the menus.
I'm using Wine 0.9.53.
What are fglrx drivers?

---

### Post by Envergure on 2008-01-18
I tried some different DirectX levels.  8.1 gave the same results as before.  Nothing else worked at all, except 6.0 which resulted in [attatchment].  This is the best it's been so far, except it stutters a lot.

---

### Post by The Noble on 2008-01-19
What graphics card do you have? An ATI card uses the fglrx driver (no clue why it is named that) for 3d acceleration. I ask because the fglrx driver used to have some problems with graphical glitches, so It is possible that is the case now. So, first off, tell me your hardware specs. Secondly, tell my if you have the drivers installed. Also, directx 8.1 is the best version to run Half life 2 with, so have it set to that currently.

---

### Post by Envergure on 2008-01-19
I have a Radoen 9550 SE and the fglrx drivers enabled.

---

### Post by The Noble on 2008-01-19
What version of Ubuntu are you using? I'm assuming Gutsy, but if you are using an older release you will want to upgrade the drivers to a newer release. Also, make doubly sure that you are not using the "ati" driver. It has 3d acceleration, but it will not work in games. To check, open up /etc/X11/xorg,conf and scroll down to 

```

...
Section "Device"
...

```

and see if the driver is "ati" or "fglrx".

---

### Post by Envergure on 2008-01-19
It sais fglrx.
Should I try changing it?

---

### Post by The Noble on 2008-01-19
No, don't change it. That is what you want actually. Would you mind running "glxgears" in the terminal? Wait 15 seconds without doing anything (turn off compiz) and copy the results here.

---

### Post by Envergure on 2008-01-19
3877 frames in 5.0 seconds = 775.350 FPS
9433 frames in 5.0 seconds = 1886.600 FPS
9432 frames in 5.0 seconds = 1886.400 FPS

I don't have compiz installed.

---

### Post by The Noble on 2008-01-19
I really don't know why Half life 2 is having problems. Try another Source game and see if that yields any different results. I never played half life 2 deathmatch, but I beat the Single Player compaign. I'm almost out of guesses, but also reverting to .9.52 worked better for me. I have a Nvidia card though, so something is certainly wrong with your system: either old drivers (use envy to update) or bad options in wine.

---

