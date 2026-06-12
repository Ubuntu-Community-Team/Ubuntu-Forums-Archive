---
title: "Sins of a Solar Empire"
date: 2007-11-24
forum: Wine
---

### Post by Sutur on 2007-11-24
Anyone know if this game might run in linux/wine?

Looking pretty badass, I'm still playing modified versions of Homeworld 2.

Screens: [http://www.sinsofasolarempire.com/downloads.aspx](http://www.sinsofasolarempire.com/downloads.aspx)

---

### Post by ARhere on 2007-11-26
Looks just like[ EVE-online]("https://secure.eve-online.com/ft/?aid=103322&bid=1&gclid=CNmAtOGI-48CFVB1OAodb1sFMw"), which will run using WINE.

EVE is a MMORPG BTW.

-ARhere

---

### Post by ticopelp on 2007-11-26
Seems doubtful. Most of Stardock's stuff, in my experience, won't run at all under wine. Which is a shame, because Galactic Civilizations I and II are two of the greatest space strategy games ever made IMHO. I miss them a lot.

---

### Post by weetabix on 2008-01-01
Well, I just tried the game in Beta 3 state with wine 0.9.46 under Ubuntu 7.10 (default environment so no added dlls, winecfg using XP, emulate virtual desktop 1280x1024). My native resolution is just that, so in fact it runs in fullscreen (beryl is in use).

The game starts ok, intros work, settings work (can change resolution etc).
New game can be started (singleplayer) and the controls seem to work.

With VERY quick test couldn't find anything that would't work. Of course this is just Beta3 and no Stardock and didn't test multiplayer, so nothing sure of course.

---

### Post by Sutur on 2008-01-18
> **weetabix said:**
> Well, I just tried the game in Beta 3 state with wine 0.9.46 under Ubuntu 7.10 (default environment so no added dlls, winecfg using XP, emulate virtual desktop 1280x1024). My native resolution is just that, so in fact it runs in fullscreen (beryl is in use).

The game starts ok, intros work, settings work (can change resolution etc).
New game can be started (singleplayer) and the controls seem to work.

With VERY quick test couldn't find anything that would't work. Of course this is just Beta3 and no Stardock and didn't test multiplayer, so nothing sure of course.

This is good news :-)

---

### Post by straxus on 2008-02-08
I tried the Retail release under 0.9.54.  It installed fine.  If you let it launch itself at the conclusion of the install, it runs fine for a bit before crashing.  I was never able to launch the game after that.  It only hangs.

There is a[ thread]("http://forums.sinsofasolarempire.com/index.aspx?aid=171844") over at the SoaSE forums about running under Wine.

It seems the version you can download with Stardock Central works quite well,  but you must run the download process under Wine 0.9.47.

---

### Post by MrSpiffdifilous on 2008-02-12
I have a workaround for the crashing. It's more of just a temp solution till someone patches the game for wine or something but hey it works.  While its still true that you cant just launch the game you can "Modify" or "Repair" the installation with the disc and it will start the game again and you will still have all your progress. I've done it a bunch of times! Im currently using wine 0.9.49 incase anyone is wondering. let me know if anyone else can do the same!

---

### Post by WedgeHG on 2008-02-20
Hey MrSpiffdifilous, just curious: are you running the patched version of Sins (1.02) or the version that came on the disc? And when you launch Sins by running setup.exe from the DVD and choosing "Modify Available Options" how often does it crash? Or not at all?

I've given it a shot with my 7.04 setup and Wine 0.9.55 on the patched version of Sins and it still crashed (though it did seem to take longer than usual, but more trials will be necessary to confirm that it wasn't just a fluke). Thanks for sharing your results.

---

### Post by squidfaceExtreme on 2008-02-27
Sins actually works pretty well on my machine. It's glitchy and the fonts are too big so sometimes they don't even show up on some labels but it's otherwise playable at a relatively smooth framerate.

---

### Post by Nameless_one on 2008-02-28
My biggest problem with it is the sound. I use ALSA, but for some reason sound in the game is extremely slow and stutterinmg. Have you changed anything realted to sound for the game to play? 

Also, about the fonts. I wonder if we are having the same effect. When I runj SoaSE,  most of the text ingame is distorted and unreadable, except for very few texts (for example, I can see the 'Options' button, and 'Sins of a Solar Empire' on the top of the menu). Is this what you're getting? This pretty much makes the game unplayable for me, I can't remember all that stuff :) I have to read tooltips!

---

### Post by WedgeHG on 2008-03-05
Could you post a screenshot or two of the font distortion so I can compare it to my own? For me they mostly display correctly (with the exception of being too large of course) and in cases where they don't display correctly it just disappears entirely, not get distorted. Hotkeys do display as a bunch of gibberish though: something like <<<<<$%<<

---

### Post by Nameless_one on 2008-03-06
I am away from my own computer right now, but I will post the screenshot in a few days.

---

### Post by Nameless_one on 2008-03-07
[Here you go.](http://students.ceid.upatras.gr/~altanis/garbled.png)

---

### Post by Nameless_one on 2008-03-08
I installed Wine 0.9.56 and the font problems are gone :) The sound problem remains, though.

---

### Post by grimdeath on 2008-03-10
ive updated to 0.9.57 on gutsy, any word how this runs on this setup? I had just started on this game about the time I started using ubuntu a week ago.

guess i can try it tonight and post back on how it runs :P

---

### Post by Melhisedek on 2008-03-10
Please do so :) I'm about to get back home and am dying to try it out as well :)

---

### Post by WedgeHG on 2008-03-11
I haven't tried it on .57 yet but it seemed quite stable on .56 so I would imagine that .57 ought to be good as well.

And Nameless_one, I never had anything like what you had in the screenshot. But as long as it's gone I guess we don't need to worry about it anymore :)

---

### Post by Nameless_one on 2008-03-12
Yup :) Also, I've given up on the sound, I think I'll just play it on Windows, that's why I dual-boot.

---

### Post by Mr. Picklesworth on 2009-01-26
Just thought I'd jump in to add that this game runs really well on my machine. It has Intrepid Ibex, Wine 1.1.13 from PPA and nvidia-glx 180.11 from official repositories. For some reason running under Crossover Games it just crashes instantly, but in Wine it works.

Fonts are larger than they should be, as mentioned in the [appdb page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12495"), but the 3D scene seems to perform more consistently smoothly than it did in my Windows partition, which is a real first. (In fairness, I haven't checked the video settings).

One oddity: As soon as it starts rendering a 2D user interface on top of the 3D scene, the game grinds to an absolute halt and flipping through that interface becomes a monotonous chore. Particularly oddly, the HUD has no such problem.

[Corrected. Oops :P]

---

### Post by Meow27 on 2009-01-26
> **Mr. Picklesworth said:**
> Just thought I'd jump in to add that this game runs really well on my machine. It has Intrepid Ibex, _Wine 1.2.13_ from PPA and nvidia-glx 180.11 from official repositories. For some reason running under Crossover Games it just crashes instantly, but in Wine it works.

Fonts are larger than they should be, as mentioned in the [appdb page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12495"), but the 3D scene seems to perform more consistently smoothly than it did in my Windows partition, which is a real first. (In fairness, I haven't checked the video settings).

One oddity: As soon as it starts rendering a 2D user interface on top of the 3D scene, the game grinds to an absolute halt and flipping through that interface becomes a monotonous chore. Particularly oddly, the HUD has no such problem.

please correct this, as it could get confusing in the future ;)

---

### Post by Mr. Picklesworth on 2009-01-27
Thanks for pointing that out, Meow. Here's some happier news (after that disappointing "hey, there isn't a Wine 1.2!!!" moment).

I just tried this again, and suddenly it was working better, without the 2D graphics slowdown. Recently I installed Wine Doors again and downloaded the "official" DirectX 9 runtime, so that may have fixed it.

It's possible that the slowdown I encountered was due to a memory leak and I had simply forgotten about research for the first few minutes, but that doesn't explain why it was only the 2D interfaces.

---

