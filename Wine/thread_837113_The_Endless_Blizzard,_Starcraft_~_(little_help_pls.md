---
title: "The Endless Blizzard, Starcraft ~ (little help pls)"
date: 2008-06-22
forum: Wine
---

### Post by myromance123 on 2008-06-22
Heya, I have just installed Starcraft,patched it,installed Broodwar,patched it, all through cedega. You see, I used an .iso image from my pc so it keeps giving me this error when I try to run:

    "Starcraft is unable to read a required file. Your Starcraft CD may not be in the CDROM drive. Please ensure that the Starcraft disc is in the CDROM drive and press OK."

 Is there a way around this besides putting the install.exe onto my pc, because I only have a 60gb harddrive. If anyone knows where a no-cd crack is I would be happy to know. Thnx~

---

### Post by Hairy_Palms on 2008-06-22
use wine, it runs starcraft far better than cedega, in fact imo cedega is a dead duck nowadays, it was only good for games, and vanilla wine is now better than it.

---

### Post by myromance123 on 2008-06-22
What is vanilla wine?? Anyhow, I have tried using wine, same thing comes up. I have read in many past forums, and it seems as if no one has a no-cd crack for this game. They all resort to copying the install.exe fail and pasting it in the starcraft directory. Hasnt anyone found another way than this?  :confused:

---

### Post by disturbedite on 2008-06-22
vanilla wine simply means wine.

as for whether or not a no-cd crack is needed, i can't remember. it may well be that sc doesn't run with no-cd cracks any more with wine/cedega. if that is the case, then you need to clear some space off your HDD or get a new one.

if no-cd cracks do work with sc, then dig around, they're out there...

---

### Post by myromance123 on 2008-06-23
Lol, thnx disturbedite. I have been fishing for some time and found some websites with such cracks. Im just worried they're fake or able to damage cedega because it wasn't very easy to setup XD

  Ill go get some of the sites I found and post em here so anyone with the expertise can tell me "safe" or "backout" :]

:)

---

### Post by dfreer on 2008-06-23
I've created a .bin/.cue image of my original starcraft CD, and it works absolutely fine (e.g. no "cd is missing" errors) using daemon tools in windows.

Try creating a .bin/.cue image, and then try mounting that using cdemu in ubuntu. I haven't tried it myself, but it may work.

---

### Post by Judo on 2008-06-23
The game works fine with the actual CD.  I just needed to add a CD-ROM drive in WINE's configuration program and it ran as perfectly as Windows.  I can't remember exactly how it was named, sadly.

---

### Post by dfreer on 2008-06-24
> **Judo said:**
> The game works fine with the actual CD.  I just needed to add a CD-ROM drive in WINE's configuration program and it ran as perfectly as Windows.  I can't remember exactly how it was named, sadly.

Open winecfg, click on the "Drives" tab, and either use autodetect (should pick up the CD drive), or enter the path to the drive (/media/cdrom I should think).

---

### Post by disturbedite on 2008-06-24
i don't know why ppl are always saying they have to add drives to wine's configuration. mine were ALWAYS detected & added automatically whenever i installed wine.

---

### Post by tkmn on 2008-06-25
Hey, I found a no-cd patch :lolflag:

It's called the latest patch from Blizzard...

```
--------------------------------------------------------------------------------

- patch 1.15.2

--------------------------------------------------------------------------------



  Feature Changes



- StarCraft and StarCraft: BroodWar no longer require the CD while playing the

  game.  To play without the CD, please follow the following instructions:



- Windows Users:

    - Make sure you have "Hide extensions for known types" unchecked under

      Explorer Folder Options.

    - If you own only StarCraft, copy "INSTALL.EXE" from the StarCraft CD to 

      your StarCraft folder and rename it to "StarCraft.mpq".

    - If you own StarCraft: Brood War, copy "INSTALL.EXE" from the StarCraft:

      Brood War CD to your StarCraft folder and rename it to "BroodWar.mpq".
```

---

### Post by myromance123 on 2008-06-25
Ok thanks dude ~ But in anycase that still uses up a tone of space for my pc. Oh well, I guess I have no choice ( couldnt post the sites, against regulations, sorry).

  Thanks for all the replies~ :D

---

### Post by dfreer on 2008-06-25
> **tkmn said:**
> Hey, I found a no-cd patch :lolflag:

It's called the latest patch from Blizzard...

```
--------------------------------------------------------------------------------

- patch 1.15.2

--------------------------------------------------------------------------------



  Feature Changes



- StarCraft and StarCraft: BroodWar no longer require the CD while playing the

  game.  To play without the CD, please follow the following instructions:



- Windows Users:

    - Make sure you have "Hide extensions for known types" unchecked under

      Explorer Folder Options.

    - If you own only StarCraft, copy "INSTALL.EXE" from the StarCraft CD to 

      your StarCraft folder and rename it to "StarCraft.mpq".

    - If you own StarCraft: Brood War, copy "INSTALL.EXE" from the StarCraft:

      Brood War CD to your StarCraft folder and rename it to "BroodWar.mpq".
```

Awesome to know! I thought I heard something about this, but wrote it off to some fantastic dream I was having... :D

---

### Post by deh1963 on 2008-06-25
It's the same with the latest patch for Diablo II (1.12).  No CD required.

---

### Post by disturbedite on 2008-07-12
> **deh1963 said:**
> It's the same with the latest patch for Diablo II (1.12).  No CD required.
true. thanks for the convenience blizzard.

now i wonder if diablo 3 will be this way?...

---

### Post by Kartel on 2008-07-13
I would also add that you can register an account with blizzard.com and include your cd-key in the profile information. It will let you download the game and what you get won't require a cd. Handy in case you lose you cd/iso.

---

### Post by NeoFax on 2008-07-13
Patch 1.15.2 has a built-in no-cd requirement.  Also, if you connect to the Battle.net servers they will automatically install this patch.  As for the cannot find the CD, there is multiple ways of fixing this:

1. Copy over the install.exe file from both your StarCraft and BroodWars CDs and rename to StarCraft.mpq and BroodWar.mpq

2. cd ~/.wine/$USER; ln -s /Some/place/you/mounted/iso d:

3. Use acetoneISO to mount the iso under /media/cdrom

I prefer the first method as it does not mess up my standard wine install(BTW do this after running the patch and canceling the install when it states it cannot find the CD).  Unless of course you use wineprefixes, then it is a moot point.

---

### Post by chono on 2008-07-13
This is my first post, one, how do u make a new thread? and on starcraft, it works great in wine 800X600 except ipx and udp lan, both cannont initialize network provider. i have no idea how to fix this, any help?  -thanks

---

### Post by disturbedite on 2008-07-15
@ chono
click new thread near the top of the page. it would be appropriate to post in the WINE section of the forum.

---

