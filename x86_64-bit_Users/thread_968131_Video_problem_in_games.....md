---
title: "Video problem in games...."
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by socomoddjob on 2008-11-02
Okay....ill start off by saying i am a novice with ubuntu so be easy on me. 

Im running intrepid 64 bit.

When i try to play a game like nexuiz, open arena or alien arena the game loads but the graphics are completely messed up. 

My video device is a Intel Graphics Media Accelerator 4500MHD

Help

---

### Post by cooldude on 2008-11-21
Me too. UT2004, Wolfenstien enemy territory, & Urban terror. All video is scrambled. sound works fine. Pretty sure drivers are working correctly as can use other 3D apps like googleearth for example.

---

### Post by huntzire on 2008-11-22
I have a few issues with x86-64 bit Ubuntu 8.10, What I have discovered, is certain chipsets (i only have experience with nvidia chipsets) is most applications have a hard time setting XServer resolution. so look for the configuration files for the games and make sure the resolutions are set to a normal resolution and low just for test purposes.


Also make sure you install the close sourced drivers, most opensource ones are still iffy with performance still.

 Also if you ever get a game that goes completely black screen and your monitor complains resolution out of sync, try putting the app in window mode till you set the resolution, by hitting alt spacebar.

---

### Post by cooldude on 2008-11-23
Well, I found out they work fine in window mode. I ended up putting an extra monitor for a dual monitor setup so I did a aticonfig --dual-head=right & after that could play games full screen.

---

