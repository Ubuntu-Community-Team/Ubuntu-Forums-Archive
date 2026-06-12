---
title: "Xubuntu 13.10 + Wine + Amd APU A8 + Painkiller performance"
date: 2014-09-11
forum: Wine
---

### Post by ilpiero on 2014-09-11
Hi all,

I downloaded the painkiller pack from the humble store, for some reason they claimed linux compatiblity but out of 5 games/expansions only one was for linux.
I decided to give wine a try, and i dowloaded painkiller black editon (basically the 2004 game).
With AMD A8 6600K + 8 Gbytes of ram, proprietary drivers Xubuntu 13.10, I have average 25/35 FPS with Hi/Lo peaks like 17/45...(details set to high no antialiasing)
Is this the performance expected? Has someone similar Hardware I can compare with? Am I missing some trivial tweaking?


Thanks guys ;)

---

### Post by mastablasta on 2014-09-12
have you looked here: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=8883](https://appdb.winehq.org/objectManager.php?sClass=version&iId=8883)

it says (this is for latest patch) which stuff needs to be installed and setup for it to work well.

---

### Post by ilpiero on 2014-09-12
Thanks mastablasta, i'm not much of a gamer anymore,the program seems to work... i just wanted to know if there is a comparable benchmark.
Actually i got a glmark2 Score of 59 so mybe is not Wine the problem...

Thanks again!

---

### Post by mastablasta on 2014-09-12
no check the wine settings and any additional libraries you need installed. also check in other versions.

I never played this game but you chip should be quite capable of playing older titles. I mean I had a much older and not so strong GPU (HD 3650/512MB) and CPU (only a single core 2,4 Ghz AMD) and usually I can play games (FPS/RPG - Oblivion, Stalker...) from 2005, 2006 on med-high settings just fine. if you get good results in Linux then it is a wine "issue". in Linux there are a couple of engines that can be used for benchmarks. and then you have phoronix test suite to make the tests (never used it myself).

---

### Post by slickymaster on 2014-09-12
*Moved to the ***Wine*** sub-forum*

---

### Post by ilpiero on 2014-09-12
I found out the cause, it was the "without tearing" (my own tranlsation, this program for some reson is in italian) in the Catalyst control center.
Now that is disabled i get twice the FPS.

---

