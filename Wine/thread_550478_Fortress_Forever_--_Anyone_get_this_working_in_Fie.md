---
title: "Fortress Forever -- Anyone get this working in Fiesty under WINE?"
date: 2007-09-13
forum: Wine
---

### Post by nchase on 2007-09-13
I've had no luck getting the new HL2 mod, Fortress Forever, working in WINE.

I'm able to run Day of Defeat: Source (which uses the same engine) just fine, albeit, without sound.

If you've had any degree of success, please post here.

---

### Post by PoHandle on 2007-09-14
The extent of my success was that I was able to get to the main FF screen.  Nothing but the wallpaper was displayed.  I had to guess where the quit button was to actually exit the program.  Now everytime I try to run it, the screen turns black for a moment and then just returns to my desktop.  All my other Source Engine games run fine... I have no clue why Fortress Forever refuses to run.  So now, I just put on my radiation suit and stepped back into my Windoze partition to play the mod.  It's fun, but needs more maps; old classics like 2fort, avanti, and flagrun.

I tried running several different commands (nonXgl wine "C:\...\Steam.exe" -applaunch 320 ... and varients thereof including various parameters) to launch the game, but to no avail.  I'll wait for the first update to try the game again in Ubuntu...

---

### Post by nchase on 2007-09-14
[QUOTE=PoHandle;3362456 I have no clue why Fortress Forever refuses to run.  So now, I just put on my radiation suit and stepped back into my Windoze partition to play the mod.[/QUOTE]

:)

Actually, I got to the exact same point you did with similar results -- I got the server select screen to show up, but only once. I tried to connect to a server, and then it went back to the desktop.

---

### Post by Kefoo on 2007-09-15
There was a steam update a few days ago that broke running games under wine. I was able to fix it by disabling all the Steam Community features.

I'm having the same missing menu problem in wine on Gentoo. There is also almost no text showing up in the configuration dialogs. I had this same problem with Half-Life 2 last year. I know a lot of people were missing the tahoma.ttf font. I don't remember whether that fixed it for me, and I have that font now, so that's not the problem here (at least for me), or there's more than one thing wrong.

---

### Post by hone on 2007-09-22
There's a forum post at Fortress-Forever.com detailing what people have gone through to get some of the fonts to work: [http://www.fortress-forever.com/forum/showthread.php?t=11453](http://www.fortress-forever.com/forum/showthread.php?t=11453)

In short if you remove HUDfont.ttf and HUDfont_caps.ttf, you should do a little better.  I removed Crosshairs.ttf and this will load the default haliflife 2 font.  You can then choose to use letters for a crosshair.  I find the +/x work the best.

---

### Post by jseiser on 2007-09-24
> **hone said:**
> There's a forum post at Fortress-Forever.com detailing what people have gone through to get some of the fonts to work: [http://www.fortress-forever.com/forum/showthread.php?t=11453](http://www.fortress-forever.com/forum/showthread.php?t=11453)

In short if you remove HUDfont.ttf and HUDfont_caps.ttf, you should do a little better.  I removed Crosshairs.ttf and this will load the default haliflife 2 font.  You can then choose to use letters for a crosshair.  I find the +/x work the best.

Once i delete that file, do i need to edit another file to get a xhair?  I got the game running but crosshairless, and it rocks :)

---

### Post by ChuK0i on 2009-05-03
I'm able to get in-game running under the latest release of wine after deletion of the said font files. Anyone know why you need to delete said files? What's causing ff to crash because of said files?  How to fix it?

Furthermore, while I'm able to get in-game I cannot get much further. Playing sniper is fine but if I change to any other class, ff will crash and fail horribly. I've heard this isn't an isolated incident either. Any suggestions?

---

