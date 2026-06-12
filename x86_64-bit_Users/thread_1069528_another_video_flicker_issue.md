---
title: "another video flicker issue"
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by andy350 on 2009-02-14
i am fairly new to ubuntu. i am running a gigabyte ga-ma78gpm-ds2h board with the integrated hd3200 ati graphics and i cannot get stable playback with any video program. it works fine with an 8800gts card, but i want to save a little on the temp and power consumption. i'm running intrepid 64bit with more than enoulgh cpu and memory...i have already tried disabling the driver and 6 different media programs(vlc, xine, mplayer, movie player, gxine...). nothing plays without a terrible flicker. the audio is clear and unbroken. any help would be appreciated. everything else is great, can't stand to look at a windows pc now.  thanks in advance

---

### Post by tenmoi on 2009-02-14
You have 2 options:
1. preferences->appearance->Visual Effects->None
2. Install the 9.1 ati driver and no flickering. 
  do it like this:
   sudo chmod +x driver.run
   alt+f2 -> gksu nautilus and browse to the .run file
   double click the .run file -> run in terminal
   next and ok and there you go!

hope this'll help.

---

### Post by andy350 on 2009-02-15
turning off all of the visual effects worked- i installed the 9.1 driver from ati as well. thanks

---

