---
title: "Fallout 1&amp;2 / WINE"
date: 2007-07-01
forum: Wine
---

### Post by Kowalski_GT-R on 2007-07-01
Hi all, I just went through an unproblematic insallation of Feisty Fawn, and have to say I'm quite chuffed with it.
After a whole day getting the grip on it, I experimented everything without problems, be it office productivity or multimedia.

Then I tried to make Fallout 1 and 2 work with WINE....

did a search, but found old threads,

I am running version 0.9.40, but Fallout just briefly loads the setup screen (in which you choose the size of installation), then freezes,forces me to quit, and lives me with a resized desktop (640x480).

Mouse pointer never worked.
I set WINE to run Win98 and a resolution of 1280x1024.
Tried other resolutions and other win versions and no joy.

What am I missing?

Thanks in advance,
Andre

---

### Post by Kowalski_GT-R on 2007-07-01
specs should be in my signature...

thanks

---

### Post by dfreer on 2007-07-01
According to wine's appdb, Fallout 1 should work fine as long as you specify it to use the small installation. Does it crash before you have a chance to select?

---

### Post by Kowalski_GT-R on 2007-07-01
yep,

installation screen,

dead pointer arrow, and black screen shortly after...

---

### Post by drummingpariah on 2007-07-01
I was running into the same problem, and for whatever reason, installing Fallout 2 solved it.  Start with fallout2, then install fallout1, and you MIGHT have better luck.  I've tried this on two machines so far, let me know how it works out for you.

Oh, and fallout2 appears to be running fine, and fallout1 worked fine with the humungous installation.  I'm going to have to check and see what might be the problem with it, and maybe I just haven't hit it yet.

---

### Post by Xzallion on 2007-07-01
I just tried installing Fallout 2 with wine version 0.9.33 on Fiesty, and everything in the menu's works, and the game *is* technically playable, but anything in game is incredibly slow, and its hard to do anything.  I'm gonna try installing Fallout 1 and see if that works or if I still have the same problems with it.

Okay, I just installed Fallout 2 (humungous installation), then installed Fallout 1 (humungous install also), patched both, and both are wonderful on menu's and movies, but when you get control of your character they are incredibly slow.  Is there anyway to fix this?

---

### Post by drummingpariah on 2007-07-02
Honestly, I hadn't gone that far :)  I installed them, saw that they booted, and moved on to my next project.  You may want to check the wine games hq database to see if there are any specific instructions for fallout & fallout 2.

---

### Post by dfreer on 2007-07-02
> **Xzallion said:**
> I just tried installing Fallout 2 with wine version 0.9.33 on Fiesty, and everything in the menu's works, and the game *is* technically playable, but anything in game is incredibly slow, and its hard to do anything.  I'm gonna try installing Fallout 1 and see if that works or if I still have the same problems with it.

Okay, I just installed Fallout 2 (humungous installation), then installed Fallout 1 (humungous install also), patched both, and both are wonderful on menu's and movies, but when you get control of your character they are incredibly slow.  Is there anyway to fix this?

sounds like your video card driver's aren't installed correctly to me (namely, direct rendering/3D acceleration is not enabled), although since I don't have fallout I can't say for certain. If you don't know whether it is or not, check this command in terminal:
```
glxinfo | grep rendering
```

---

### Post by Kowalski_GT-R on 2007-07-02
> **dfreer said:**
> sounds like your video card driver's aren't installed correctly to me (namely, direct rendering/3D acceleration is not enabled), although since I don't have fallout I can't say for certain. If you don't know whether it is or not, check this command in terminal:
```
glxinfo | grep rendering
```

thanks for the info.....

I was wondering if DOS Box wuold be a better option(at least for Fallout 1)

---

### Post by dfreer on 2007-07-02
or you could install your video drivers if that is the case ;)
DOSBox is a straight out emulator, which means it is going to be slower than wine pretty much everytime. I generally use it only for games that won't run in wine, basically any true DOS game. I'm not even sure if it runs in DOSBox to begin with...

EDIT: Have you seen this link?
[http://www.towerofcreation.com/page.php?15](http://www.towerofcreation.com/page.php?15)

---

### Post by Kowalski_GT-R on 2007-07-02
> **dfreer said:**
> 

EDIT: Have you seen this link?
[http://www.towerofcreation.com/page.php?15](http://www.towerofcreation.com/page.php?15)

much appreciated.....

this community is something special.....lots of things to learn ):P

I'm at work right now, I'll try all the things that came out so far and give the outcome as soon as I find some time....

---

### Post by edemark on 2007-07-02
Hi I have fallout 1 installed in dosbox. Yes it is an emulator but on the other side fallout is a game with some 10 years of age so it is running on my p4 750Mb ram ati igp 345 perfectly. For fallout2 you have to use wine/cedega (crossover office).
good luck

---

### Post by charlieg on 2007-07-02
I don't see any reference to [FIFE]("http://www.fifengine.de/") in this thread, which could be a useful starting point although I'm not sure how completely playable Fallout is with FIFE.

---

### Post by Xzallion on 2007-07-02
dfreer, that command returns```
direct rendering: Yes

```
I got the official Nvidia drivers installed and working already, it just seems to do odd things to wine games.

Edit: Just used that guide, and it sped everything up a little bit but still unplayable. :(
Oh well, I'm not to worried about it, I'll just boot into windows to play for a bit.

---

### Post by Kure on 2007-07-16
> **Kowalski_GT-R said:**
> much appreciated.....

this community is something special.....lots of things to learn ):P

I'm at work right now, I'll try all the things that came out so far and give the outcome as soon as I find some time....

This page ([www.towerofcreation.com](www.towerofcreation.com) +  Fallout & Linux)  shouldn't be necessary, I wrote the guide months ago and Wine made a huge leap forward - but some of those dirty tricks may help a bit.

> **charlieg said:**
> I don't see any reference to [FIFE]("http://www.fifengine.de/") in this thread, which could be a useful starting point although I'm not sure how completely playable Fallout is with FIFE.

FIFE is just and engine, they haven't yet implemented scripting language at all - you can't play Fallout in it, you can barely see the maps (no character interaction etc).

---

### Post by kesman on 2008-01-07
thread LIFTUP!

So, I get fallout 2 running with wine almost perfectly. The only thing is that it eats up 99% of my processor, which is weird. I have ati radeon x700 with fglrx, working perfectly, and a 1,6ghz processor so that's not it. Wine gives me no error messages, it just eats all available processor speed.

Any clues? I have the newest wine from the repository by the way.

---

### Post by Yeeha on 2008-01-07
Fallout 2 is slow on normal priority for some reason, try running wineserver and game with priority -10 that fixed slowness for me. If u get tired of manually setting priority then theres script named winefix somewhere out here.

---

### Post by kesman on 2008-01-08
Thanks, I'll give this a try. There's just this problem that fallout isn't running slow, quite normally I think. Dunno why it takes so much processor though...

---

### Post by ShinobiTeno on 2008-08-22
> **Kowalski_GT-R said:**
> Hi all, I just went through an unproblematic insallation of Feisty Fawn, and have to say I'm quite chuffed with it.
After a whole day getting the grip on it, I experimented everything without problems, be it office productivity or multimedia.

Then I tried to make Fallout 1 and 2 work with WINE....

did a search, but found old threads,

I am running version 0.9.40, but Fallout just briefly loads the setup screen (in which you choose the size of installation), then freezes,forces me to quit, and lives me with a resized desktop (640x480).

Mouse pointer never worked.
I set WINE to run Win98 and a resolution of 1280x1024.
Tried other resolutions and other win versions and no joy.

What am I missing?

Thanks in advance,
Andre


I know its too late for reply))
But I had exactly the same problem, ie game freezes instantly on animation sequences.

The solution is fixing the sound settings within WINE. Check if correct output is selected, check if ALSA or OSS work in other programs. Also Pulseaudio and Alsa dont work well. So get PulseAudio plugin or select Esound for emulation of ESD.

---

