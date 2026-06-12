---
title: "[SOLVED] Xubuntu 7.10 and Wine 0.9.46 Problems"
date: 2007-10-26
forum: Wine
---

### Post by reset3x on 2007-10-26
I just installed Xubuntu 7.10. I was running 7.04 and Wine 0.9.33 with no problems. Now I have a new problem. When I run HL2 via Steam the Xfce panels remain on the screen. If I disable the window manager in Wine config my keyboard doesn't work.... 

Does anyone know how I can fix this?

EDIT: Is this common with Gnome and KDE too? if not I'd be glad to switch....

EDIT 2: Solved. When HL2 starts hit alt-space. Then send HL2 to another workspace....

EDIT 3: Unsolved.... Well it worked a couple of times but now it doesn't!!!!

---

### Post by karth on 2007-10-26
I had this problem with all Source apps, until now, I'm only able to run the game in a virtual desktop (winecfg > Graphics)

---

### Post by reset3x on 2007-10-31
Bump....

---

### Post by n3utrino on 2007-10-31
i am able to play tf2 if i set the windows version to start with of the hl2.exe  in wine to win98.
but im doing this in gnome.

maybe you could try this

it seems that the next wine version has some bugs fixed regarding to the steam issues.

---

### Post by reset3x on 2007-10-31
> **n3utrino said:**
> i am able to play tf2 if i set the windows version to start with of the hl2.exe  in wine to win98.
but im doing this in gnome.

maybe you could try this

it seems that the next wine version has some bugs fixed regarding to the steam issues.

Using .47 now... Steam does work much better but the dopey panels remain... Episode 2 won't run in 98.... Guess I'll try Gnome... UGGGGHHHH!!!!!

:-(

Edit: If I hit alt-F2 and killall xfce4-panel I get full screen. when I exit the game I do the same but xfce4-panel. Then when I go to log out It kill Xfce4 and all I have is my beautiful wallpaper... Time to write some scripts I guess...

---

### Post by reset3x on 2007-10-31
Bumpity Bump..... Gnome no worky either...

---

### Post by n3utrino on 2007-10-31
Was it the same behaviour?

---

### Post by n3utrino on 2007-10-31
I followed this guide

[http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/)

all i had to do was setting it to win98 and tadaaa tf2 works

nvidia g80 8800 gtx
wine 0.9.46-0ubuntu1

---

### Post by reset3x on 2007-10-31
> **n3utrino said:**
> Was it the same behaviour?

Yep... Tried the suggestion of opening and closing the game too.... I may have to (GULP) get a copy of XP... I miss FEAR and I want to run Orange Box with no BS.....

---

### Post by reset3x on 2007-10-31
Huh... I was messing around and hit alt-F11... Problem solved!!!! =D>

---

