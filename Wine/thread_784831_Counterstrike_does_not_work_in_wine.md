---
title: "Counterstrike does not work in wine"
date: 2008-05-06
forum: Wine
---

### Post by nikoPSK on 2008-05-06
I purchased counterstrike source and garry's mod in steam under the latest wine (I added the Hardy repos) and when I launch Counterstrike, I get a black screen and when I launch GMOD I get a white screen. Any way to fix this? Fresh install of Hardy, and I haven't installed anything else on wine.

---

### Post by schtufbox on 2008-05-06
Silly questions maybe, have you installed drivers for your graphics card? is it an ATI or Nvidia? Which version of Wine?

---

### Post by nikoPSK on 2008-05-06
Latest version as I said, and yes I have installed the nvidia-glx-new package.

---

### Post by schtufbox on 2008-05-06
Just checking :P Figured you would have as judging by the post cvount at least, you've been here a while.
I can't think of a reason offhand, I run Hardy, I also have an nVidia card (drivers installed via envy) and the latest wine (though I am actually using crossover games now, but it ran fine in plain wine 0.9.60 and 0.9.61 too)
One thought I have is, as this happened with me too at one point, when the game ran fullscreen it switched my monitor off with an 'out of range' text displayed on the screen (I had a modelien wrong somewhere ata  guess) so i ended up running CS source in a window (well with wine having a virtual desktop of 1280x800 and setting cs source to use 1280x800)
Got so used to it, that I still run it that way, even though i don't need to

Probably no help at all, but that's all I can come up with, sorry :(

---

### Post by nikoPSK on 2008-05-06
Running in a virtual desktop doesn't seem to work for me. :( Although steam works fine and when I run CSS it shows the loading screen for a second or two.

---

### Post by schtufbox on 2008-05-06
in winecfg is the sound in wine set to use OSS or Alsa?  I have mine using Alsa. Not sure if OSS would make it not work, but it's worth a try.

---

### Post by nikoPSK on 2008-05-06
I have ALSA enabled, I get this when I goto the sound tab. Should I leave ALSA on when I enable OSS or turn it off?

EDIT: Also, the driver emulation box is not ticked, should it be?
EDIT EDIT: I actually read the dialog this time and clicked apply on the ALSA driver, if the ALSA driver does not work, I'll try OSS.
EDIT EDIT EDIT: Well, still the black screen, I'll try OSS.
EDIT EDIT EDIT EDIT: Mah, still doesn't go. :cry:

---

### Post by Rocket2DMn on 2008-05-06
Try adding some launch options to cs.  Right click Counter-Strike in the steam games window and hit Properties.  Then click the Set Launch Options button and try adding
```
-gl
```
or even other options like
```
-gl -width 1024 -height 768
```
You can find more options at [https://support.steampowered.com/kb_article.php?ref=1040-JWMT-2947](https://support.steampowered.com/kb_article.php?ref=1040-JWMT-2947)
It's possible that the default configuration for cs just doesn't like your video setup, so these can help you nail them down and later change the options from within the game.

---

### Post by nikoPSK on 2008-05-06
> **Rocket2DMn said:**
> Try adding some launch options to cs.  Right click Counter-Strike in the steam games window and hit Properties.  Then click the Set Launch Options button and try adding
```
-gl
```or even other options like
```
-gl -width 1024 -height 768
```You can find more options at [https://support.steampowered.com/kb_article.php?ref=1040-JWMT-2947](https://support.steampowered.com/kb_article.php?ref=1040-JWMT-2947)
It's possible that the default configuration for cs just doesn't like your video setup, so these can help you nail them down and later change the options from within the game.Tried both with the ALSA driver on. The first was no different and the second, my view didn't go skewed and I was able to see the loading screen for about 5 seconds, but black after again.

EDIT: I've even disabled Steam community in-game...

---

### Post by piratesmack on 2008-05-07
I just checked the Wine AppDB and from the comments said, it looks like the game is no longer working for some people after Wine 0.9.60/

Have you tried an earlier version?

---

### Post by nikoPSK on 2008-05-07
Nope, where can I grab one?

---

### Post by schtufbox on 2008-05-07
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by nikoPSK on 2008-05-07
It says I need libldap2, but apt can't find it.

---

### Post by schtufbox on 2008-05-07
which version of wine were you trying when is asked for that?

---

### Post by schtufbox on 2008-05-07
here's a copy of wine 0.9.58 from when Hardy was in beta (still had it, had to use it when wine 0.9.59 came out and didn't play nice) 
[http://www.mediafire.com/?nzl1wmy2tdu](http://www.mediafire.com/?nzl1wmy2tdu)

---

### Post by thomasyen on 2008-05-08
Hello. I had the same problem while running Wine 0.9.61, but it works great under Wine 0.9.58. Thanks!

---

### Post by TTrussell on 2008-06-03
I've been having the same problems as y'all. As we speak I just upgraded from 0.9.59 to 1.0 rc-3 (I had 59 because it was in the App>Add/Remove). However, if that doesn't work, am I to assume that using 0.9.58 will be OK if you DL the version for Ubuntu 7.10?

EDIT: 1.0 didn't work. Got further than ever before and crashed harder than ever before. Trying your copy of 58 now...)

EDIT: Works!!! YAY! Unfortunately it lags like **** and has no sound. Changing back to ALSA and putting it in a window... maybe that will work

EDIT: Crashes when using Vertex Shading.

---

### Post by lesergi on 2008-06-03
Hi!

Try writing -dxlevel 80 at launch options.

Regards!

---

### Post by TTrussell on 2008-06-03
> **lesergi said:**
> Hi!

Try writing -dxlevel 80 at launch options.

Regards!

I'm actually about to give up on Ubuntu. This distribution is very bad--freezes and crashes all the freaking time. I usually LOVE Ubuntu, had it on my laptop for a VERY long time, but then decided to go back to Vista so I could use DirectX 10. I was putting Ubuntu on my Desktop this time, and can only use 8.04 because I can't figure out how to get 7.10 to work with my Netgear MA111 adapter. 7.10 was always so solid, 8.04 is crap. May move to a different distribution, though I don't know what.

---

