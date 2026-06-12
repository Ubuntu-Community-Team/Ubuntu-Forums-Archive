---
title: "Help getting wine 1.4 on Ubuntu 18.10 64-bit"
date: 2019-04-12
forum: Wine
---

### Post by echaskaris on 2019-04-12
I want to play this ([https://appdb.winehq.org/objectManager.php?sClass=version&iId=21910](https://appdb.winehq.org/objectManager.php?sClass=version&iId=21910))*[I][I][I][COLOR=brown][COLOR=mediumblue] [/COLOR][/COLOR]*[/I][/I][/I]game, but no version of proton will run it and the best version of wine seems to be 1.4. However, I either can't get it to compile when downloaded from winehq or install the binary from launchpad. Playonlinux won't work either, the game isn't available in the list and it's on steam. Please help me install wine 1.4. Thanks.

---

### Post by slickymaster on 2019-04-12
Thread moved to **Wine** for a better fit

---

### Post by mastablasta on 2019-04-15
> **echaskaris said:**
> I want to play this ([https://appdb.winehq.org/objectManager.php?sClass=version&iId=21910](https://appdb.winehq.org/objectManager.php?sClass=version&iId=21910))game, but no version of proton will run it and the best version of wine seems to be 1.4. However, I either can't get it to compile when downloaded from winehq or install the binary from launchpad. Playonlinux won't work either, the game isn't available in the list and it's on steam. Please help me install wine 1.4. Thanks.


Don't believe the ratings. and despite the silver rating it looks like some of recent wine versions might work better. 
for 1.4 it says: [COLOR=#000000][FONT=&quot]Run in 1024x768
[/FONT][/COLOR]for new test it says it all works but there is stuttering. so maybe reducing resolution the result would be the same as in old version?!

are you saying you can't install old wine version using Play on linux & manual install option?

---

### Post by thenailedone on 2019-04-17
Just a few hours ago I made a similar post... see if [https://lutris.net/games/call-of-duty-black-ops/]("https://lutris.net/games/call-of-duty-black-ops/") has a working script (behind a firewall and can't access gaming sites). Even if not it has similar methods of being able to use different versions of Wine to try and run applications (I am not 100% up to speed how to install specific versions but once already on the system can be choses).

I am fairly doubtful you will be able to get 1.4 installed and working properly to be honest..

---

### Post by monkeybrain20122 on 2019-04-20
> **mastablasta said:**
> 
are you saying you can't install old wine version using Play on linux & manual install option?

POL is broken in 18.04, does it work in 18.10?

---

### Post by echaskaris on 2019-04-21
Tried with lutris and the script you showed thenailedone, the game is not starting.

---

### Post by thenailedone on 2019-04-22
> **echaskaris said:**
> Tried with lutris and the script you showed thenailedone, the game is not starting.

Yeah I see even [https://www.protondb.com/app/42700]("https://www.protondb.com/app/42700") reporting it as borked :/

[WineHQ]("https://dl.winehq.org/wine-builds/ubuntu/pool/main/") only has official debs going back to 2.4 (and even then there will be doubt in the required dependencies.

---

### Post by mastablasta on 2019-04-23
> **monkeybrain20122 said:**
> POL is broken in 18.04, does it work in 18.10?

i'm on 18.04 - yes it is broken. though i think it should be possible to do it on manual install (via their install wizzard). i could be wrong. many things in POL do not work (particularly scripts), but some things still do.

> **thenailedone said:**
> Yeah I see even [https://www.protondb.com/app/42700](https://www.protondb.com/app/42700) reporting it as borked :/

[WineHQ]("https://dl.winehq.org/wine-builds/ubuntu/pool/main/") only has official debs going back to 2.4 (and even then there will be doubt in the required dependencies.

based on this the only options seem to be to wait or get windows running. :(

---

### Post by thenailedone on 2019-04-24
> **mastablasta said:**
> based on this the only options seem to be to wait or get windows running. :(

I fear that is the price we pay in having the ability to play the latest and greatest, we lose the ability to play the oldies but goodies :/

---

