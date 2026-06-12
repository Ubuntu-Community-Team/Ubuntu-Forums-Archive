---
title: "Simcity 4 under Wine on Feisty"
date: 2007-10-23
forum: Wine
---

### Post by Phil Airtime on 2007-10-23
Hiya,

Back when I had a Mac, I had a copy of Simcity 4 for it. I'm looking at getting back into playing it, but I obviously can't play the Mac version on Ubuntu. If I get a cheap copy of the Windows version off Ebay, will it work under Wine on **Feisty** (not Gutsy)? My current Wine version is 0.9.33 from the repos. My computer is as in my signature and my graphics card is an Nvidia Geforce FX 5600GT with the proprietary driver installed.

If anyone has had success (or otherwise) with this, please let me know before I buy.

Cheers.

---

### Post by cogadh on 2007-10-23
Wine's AppDB can tell you nearly everything you need to know:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1565](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1565)

---

### Post by Phil Airtime on 2007-10-23
Cheers for the link. Mixed reviews, it seems, with one person saying "garbage" and another saying "bronze" with the same Wine and Ubuntu versions. What they were doing differently, I don't know. I'm not sure about this "no CD crack" stuff; it all sounds very technical and a bit dodgy. I want to buy a legal copy and not do anything iffy! I've only ever used Windows at work (always Macs and then Ubuntu at home) so I'm not sure if that is standard practice. 

I've also found this blog post, but that goes on about needing "a cracked SimCity 4.exe that skips the copy protection". Scary biscuits. [http://tombuntu.com/index.php/2007/04/06/simcity-4-on-ubuntu-with-wine/](http://tombuntu.com/index.php/2007/04/06/simcity-4-on-ubuntu-with-wine/)

---

### Post by cogadh on 2007-10-23
The discussion of cracks in public forums is strongly discouraged, however, it should be noted that Wine does have incomplete copy protection support and some people find that the only recourse they have to get around that is to use a cracked executable.

I believe Sim City 4 uses SafeDisk copy protection, which does not work at all in Wine.

---

### Post by Phil Airtime on 2007-10-28
Just for completeness in case anyone clicks onto this thread from a search:

SimCity 4 Deluxe Edition *does* work on Feisty with Wine 0.9.33 following the instructions in the tombuntu.com blog post linked to above. It's reasonably fast even with all graphics settings turned up. However, a "minor modification" must be made to your purchased copy, details of which I can't go into here. 

When you first load the game, colours may be set very low and it'll look awful. To fix, go into the graphics settings, select "32-bit" from the colour options and restart the game. On my machine, it does hang every so often, particularly when entering or exiting underground view or zooming in and out which is rather annoying; just make sure you save your city every ten minutes or so! That could be my aging computer, but it's something to watch out for. I lost an entire city the other day.

When a user-created building or modification asks to be installed into your C:\Documents and Settings\blah blah whatever folder, the Linux replacement is ~/SimCity 4/.

---

