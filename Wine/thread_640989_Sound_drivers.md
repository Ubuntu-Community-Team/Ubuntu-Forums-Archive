---
title: "Sound drivers"
date: 2007-12-14
forum: Wine
---

### Post by Cap'n Murph on 2007-12-14
When I go into Winecfg and try to set up my audio drivers, no matter which drivers I choose the audio test fails and there's no sound in any of the games I play (I've only tried Steam, but I've tried CS 1.6 and TF2 and neither worked, its all I have installed right now).

---

### Post by yabbadabbadont on 2007-12-14
Just to ask an obvious question, does sound work outside of wine?

---

### Post by Cap'n Murph on 2007-12-15
After I reboot, yes, but after trying to run a game and going back to my music player, it doesn't work anymore. And actually I just booted TF2 and the sound worked for a minute (The steam logo and the menu music) before cutting out, but then if froze when I actually tried to get into a game

---

### Post by hikaricore on 2007-12-15
Even though the sound stops, the game and or WINE is still controlling your sound output 
system.
With the default configuration of the Linux sound system you won't be able to use sound elsewhere until this/these process(es) have been ended.

You need to make sure no other process is using sound while testing if you're not doing so already.

It is possible that the game/software is locking up your audio hardware in another more hardware based way, but I highly doubt it.

---

