---
title: "WOW won't load"
date: 2011-11-28
forum: Wine
---

### Post by Mazate on 2011-11-28
Ok, I installed WOW last week with wine and it worked fine... mostly.  The WOW launcher button never worked so I had to go into the file structure and actually double click the wow.exe file to play.  Now that isn't working.  I double click it and my hard drive works for a few seconds and then goes quiet but the game never loads.  Does anyone know how to resolve this?

---

### Post by cwwilson721 on 2011-11-28
Launch Wow.exe through the terminal and post the output.
Ex: (Change "[COLOR="Blue"]<USER>[/COLOR]" with your username)
```
env WINEPREFIX="/home/<USER>/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```
The above assumes that WoW is installed in the 'normal' place

Also, we'll need:
[LIST]
[*]Hardware Specs (Mostly video card/chipset)
[*]Do you have proprietary drivers installed if a ATi/AMD or Nvidia? If Intel, good luck.
[*]What wine version?
[*]What Ubuntu version?
[/LIST]

Alot of this post is FROM THE STICKY, and is totally unnecessary.

Read it.

Then search the forum.

I'll bet it's already asked and answered.

---

### Post by Crossbow on 2012-12-30
Mazate - Was this resolved? It could be related to my problem. In my case the launcher works but the game will not load. I've been searching the forums for two days without finding a resolution. I posted in the "how to" sticky but no one has answered.

---

### Post by Mazate on 2012-12-30
No I never did get it to work right.  I've since gone back to Windows actually.  I prefer Ubuntu in every other sense but I can't play my games and that was a deal-breaker for me.

---

### Post by Crossbow on 2012-12-30
I wish that were an option for me, but I never had Windows in the first place. I can play the game on my roommate's Windows machine but it's blurry and slow and clunky. Plus, she either lost or never had her Windows installation discs so I can't use those, or reinstall hers.

---

### Post by overdrank on 2012-12-30
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

