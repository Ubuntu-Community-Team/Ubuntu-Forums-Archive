---
title: "Trying to get Thief 3: Deadly Shadows to work"
date: 2013-06-07
forum: Wine
---

### Post by sky5564 on 2013-06-07
It's one of my favorite games and i would love to see it running on Ubuntu 12.04 or Linux Mint 13.

I know it is possible because here is video proof it works on linux:

[https://www.youtube.com/watch?v=-c2uIwYC2NQ](https://www.youtube.com/watch?v=-c2uIwYC2NQ)

I purchased the game from gog.com and downloaded the installer.exe, I used playonlinux and the install process worked just fine without any problems.

But when i run this game i get this in the debug terminal:

```
fixme:d3d:state_wrap (WINED3DRS_WRAP0) Texture wrapping not yet supported.
```

Basically what happens for me is the menu fails to load correctly, Buttons and text are missing and when i finally do fiddle around with the menu (Clicking randomly) i finally hit the area where the button is supposed to be and the game starts, After the game starts it does not look correctly, Their is no lighting at all and the only thing you can see is the moonlight above garret and the black ground below, You can also hear his footsteps and the guards talking.

Here is a screenshot of the menu:

[http://i.imgur.com/0UU77Q0.png](http://i.imgur.com/0UU77Q0.png)

---

### Post by Mateusz Stachowski on 2013-06-09
You should try the [Sneaky Upgrade]("http://www.ttlg.com/forums/showthread.php?t=138607") - widescreen and tweaks patch for Thief 3. That's unofficial community patch for that game which adds many good things and solves problems with compatibility for new hardware (widescreen and multicore CPU).

Also a general tip for trying to get information about how to run a game on Wine is to search in Google for AppDB results. You have to type the name of the game in this case Thief and then just add appdb.

[Google Thief appdb]("https://www.google.com/search?q=Thief+appdb")

The test results in AppDB for this game are for very old Wine versions and therefore they may not be accurate for 1.5.31 and 1.6-rc1 releases.

---

### Post by Mark Phelps on 2013-06-09
The silver rating means you're essentially wasting your time trying to get this to work.  For a game to be useful in Wine, it needs at least a Gold rating.

---

### Post by sky5564 on 2013-06-09
Cool, Makes me want to install windows 7 on a seperate partition just to play it again.

---

### Post by Mateusz Stachowski on 2013-06-10
I've tried running the game on Wine 1.6-rc1 with SneakyUpgrade 1.1.2 and it works just like it did even when I was still using Windows XP. I've started the training mission and played it for about 3 to 5 minutes (no glitches with graphics and sound) and then my PC just shut off. I have the same problem with couple other games (for example Dead Space).

It seems that the game would deserved a Platinum rating. I had trouble only with screen resolution because the game starts with 640x480 and when you change it in-game to 1920x1080 it doesn't apply it immediately. You have to exit the game change you screen resolution from that 640x480 to whatever you normally have and then start Thief.

---

### Post by WienerWuerstel on 2013-06-11
And it's even supoorted by PlayOnLinux so it should just work fine with WINE. The WINE APPDB is fine and everything but sometimes the ratings are a little bit of. You shouldn't only trust the Ratings and read some Tests to see what works and what doesn't.

---

### Post by Cerberus90 on 2013-12-04
> **Mateusz Stachowski said:**
> I've tried running the game on Wine 1.6-rc1 with SneakyUpgrade 1.1.2 and it works just like it did even when I was still using Windows XP. I've started the training mission and played it for about 3 to 5 minutes (no glitches with graphics and sound) and then my PC just shut off. I have the same problem with couple other games (for example Dead Space).

It seems that the game would deserved a Platinum rating. I had trouble only with screen resolution because the game starts with 640x480 and when you change it in-game to 1920x1080 it doesn't apply it immediately. You have to exit the game change you screen resolution from that 640x480 to whatever you normally have and then start Thief.

On Win 7 this one work [http://www.moddb.com/games/thief-deadly-shadows/downloads/widescreen-patches-tds-tweaker](http://www.moddb.com/games/thief-deadly-shadows/downloads/widescreen-patches-tds-tweaker) in HD 16:9, but when you go to the end of level or area, or if you try to load saved games boom, it blow it and just freeze, so if it this is problem in Linux go for it it is a one of best games ever! ;) If anyone need support in supporting games for linux call, i will be there! :)   :p
Pay attention on comment [http://www.steamgamesonlinux.com/thief-deadly-shadows/](http://www.steamgamesonlinux.com/thief-deadly-shadows/)

---

### Post by e-San on 2014-07-19
Hi!

I have quite simmilar problem, but i'm closer to play (according to your screenshot sky).

Look here: [http://i.imgur.com/RFpa4Fu.png](http://i.imgur.com/RFpa4Fu.png)

I tried Sneaky Upgrade (dzi&#281;ki Mateusz), but no diffrence (screenshoot is after 'upgrade').

It's on POL but installed as 'other'.

Regards!

---

