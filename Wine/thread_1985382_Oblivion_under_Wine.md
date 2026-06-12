---
title: "Oblivion under Wine"
date: 2012-05-23
forum: Wine
---

### Post by vaim369 on 2012-05-23
Alright, so I've installed Oblivion, with the patch and shivering isles, yada yada yada, it's all done. I configured wine according to the tutorial you first get when you google "how to run oblivion under wine" (well at least I think I did properly, im pretty new to using linux). I start it up, and the bethesda logo stutters, for a bit, but then it runs smooth after a few seconds, and then it does it from there on each logo even when i reach the menus, after a few seconds on each one they all run smooth. I then start the game, and blam, my character's texture has gone horribly wrong and the whole game world as well, and the framerate is pretty bad too. 

I'm using kubuntu 10.10, I don't exactly know what my graphics card is (don't how to check but my laptop is the way it was when I bought it a year ago), but when i ran oblivion when i had windows (same laptop) it ran just fine, even at a tad bit higher settings, so I'm guessing it should at least work on the lowest setting, some help plz, im thinking i just have to re install maybe, but i'm concerned that's gonna be a waste. 

Again, I'm pretty new to linux (using since the end of march) but I'm getting the hang of how it works pretty well, so keep that in mind

For the love of all that is holy please help, I'm so close to playing this game it's pissing me off that I can't figure out what is wrong, also I'm pretty sure I'm running the latest version of wine updated yesterday (I think, Again im a newbie at this) in case anyone is wondering

Edit:
New problem, when i start playing (after skipping the intro scene_, all goes black (well I can see the edit character menu stuff, but graphics wise, cant see anything, no background character, nada, btw sound is all fine), tried re installing everything, failed, still all black

---

### Post by thatguruguy on 2012-05-23
> **vaim369 said:**
> Alright, so I've installed Oblivion, with the patch and shivering isles, yada yada yada, it's all done. I configured wine according to the tutorial you first get when you google "how to run oblivion under wine" (well at least I think I did properly, im pretty new to using linux). I start it up, and the bethesda logo stutters, for a bit, but then it runs smooth after a few seconds, and then it does it from there on each logo even when i reach the menus, after a few seconds on each one they all run smooth. I then start the game, and blam, my character's texture has gone horribly wrong and the whole game world as well, and the framerate is pretty bad too. 

I'm using kubuntu 10.10, I don't exactly know what my graphics card is (don't how to check but my laptop is the way it was when I bought it a year ago), but when i ran oblivion when i had windows (same laptop) it ran just fine, even at a tad bit higher settings, so I'm guessing it should at least work on the lowest setting, some help plz, im thinking i just have to re install maybe, but i'm concerned that's gonna be a waste. 

Again, I'm pretty new to linux (using since the end of march) but I'm getting the hang of how it works pretty well, so keep that in mind

For the love of all that is holy please help, I'm so close to playing this game it's pissing me off that I can't figure out what is wrong, also I'm pretty sure I'm running the latest version of wine updated yesterday (I think, Again im a newbie at this) in case anyone is wondering

Open a terminal and type the following:
```
lspci | grep VGA
```
... and post the results here. That will tell you your video card. I'm guessing that it's an intel.

Just out of curiosity, why are you still running 10.10?

---

### Post by vaim369 on 2012-05-23
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]

those are the results I get, I tried to update wine yesterday,  did it, checked, it's wine version 1.3, don't know if that helps

as for using kubuntu 10.10, is it bad or something? I was trying to install the latest ubuntu at first by creating a pendrive, long story short, that failed, so i tried kubuntu, it worked for reason, and it's what I have now, but that's a whole other story. Personally, this os is starting to grow on me, but if know you any more user-friendly (as in more GUI friendly, and I know there is, just don't know if I want to change and put all the work I put on working with this thing to waste) distribution of linux, I'd like to know

Okay last night I reinstalled everything, it ran a bit smoother, but still generally the same problems, and then it got worse. when i started playing, all i say was black, the sound was working, but i could not see anything, all black, i saw some things about HDR turned on causing that or something on another thread, but it's off, experimented, still the same

---

### Post by thatguruguy on 2012-05-23
I would suggest upgrading your Kubuntu to 12.04.  10.10 is no longer supported, as of this past April.  12.04, as a long-term release, will be supported until April of 2017.

For instance, Wine is now on 1.5, but you can't get that for Kubuntu 10.10.

You should also make sure you are using the proprietary drivers (if available) for your graphics hardware.

---

### Post by vaim369 on 2012-05-23
Thanks, I wasn't aware that it was no longer supported, I'll update, see what happens

---

### Post by vaim369 on 2012-05-23
next question, how If I'm using the right proprietary drivers?

---

### Post by rai4shu2 on 2012-05-24
> ./winetricks d3dx9

see: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506)

---

