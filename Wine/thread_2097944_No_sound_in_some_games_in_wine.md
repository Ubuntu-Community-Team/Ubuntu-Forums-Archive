---
title: "No sound in some games in wine"
date: 2012-12-25
forum: Wine
---

### Post by Sazex on 2012-12-25
Hi, I've been having problems with getting sound to work with two out of three of my games that I have installed with steam on wine. 
I've installed Borderlands 2, Dead Island, and Portal 2. Borderlands 2 works flawlessly and sound is great.

However, Dead Island and Portal 2, do not have sound. Although the graphics, and the game play is fine*, there is no sound. 

I'm running Ubuntu 12.10 64-bit with Wine version 1.5.19.

Under audio tab in winecfg, the selected driver is winepulse.drv, and the output device is set to system default. When I click test sound, there is a 2 or 3 second delay before I hear a sound. 

Also when I disable mmdevapi, or set it to native (windows), Borderlands 2 sound no longer works.

The other options for mmdevapi, however, still give me sound in Borderlands 2, but none of them give me sound in Dead Island, or Portal 2.


EDIT: So I tried to see if it was just my headset reacting badly with Portal 2 and Dead Island(its a wireless Plantronics Headset)

I plugged in a wired headset, and for some reason sound on Portal 2 worked! I then immediately removed it and tried it again with my wireless, and it now works on that too!
But alas,neither headset works for Dead Island...

*My keyboard doesn't work in Portal 2...(It's also a wireless keyboard, although this is unrelated, and probably doesn't have anything to do with my audio problem)

Has anyone encountered any problems close to mine?



2nd EDIT: Okay, so I installed Portal 2, and Dead Island through Playonlinux, with good results for Dead Island(it works 100% now)...as for Portal 2 it detects my keyboard and I hear sound, but it doesn't make it to the main menu without crashing... This made my steam not work on regular wine, so I had to re install Borderlands 2 with playonlinux, and that's working now too. 

So now all my audio problems have been fixed...but I have this new Portal 2 problem...will try to re install later...

Anyways, since my audio problems have been fixed, I'll mark this thread as solved.

---

