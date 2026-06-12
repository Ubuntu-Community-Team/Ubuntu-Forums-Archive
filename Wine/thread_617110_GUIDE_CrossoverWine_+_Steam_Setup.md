---
title: "GUIDE: Crossover/Wine + Steam Setup"
date: 2007-11-19
forum: Wine
---

### Post by sirgogo on 2007-11-19
Hello all:

I'm sure this has been addressed many, MANY times all over the web, but I just thought I'd create a post on how to get Steam working after a Crossover/Wine installation. There have been many issues concerning the launching of games (graphically).

So here goes:

1. Get your emulation program (Crossover/Wine)
2. Follow instructions to install Steam.
3. Once this is done you basically do w/e.
4. Open the My Games list.

*This is the place where many people encounter errors (including me).

5. Try and launch your game.
6. If this does not work, or you have errors, I'm in business.
7. Right click on your game, and select Properties.
8. Click "Launch Options"
9. Add Commands!
- To force opengl: ```
-novid -gl
``` (this is actually two commands, but you should put them together).
- To force a specific Direct X level: ```
dxlevel #0 (where # is replaced by Direct X version 6, 7, 8, 9.. etc)
```
- To have a quick load: ```
-console
```
-To force a window size (includes fullscreen):```
-width #### -height ####
```
- To set memory to be used  (by default it is 64mb): ```
-heapsize ####### (imput digits first, and add 0's at the end. For example: 1 GB would be 1024000")
```

A sample would be:
```
-console -novid -gl -width 1400 -height 1050 -heapsize 1024000
```

10. Click okay, and launch your game!

*** This is a note:
11. I'm not sure why this happens, but I only needed to use these commands once. After the first time, the game wouldn't run if those commands were enabled. I *know* that this should not be the case, but it happens. So please keep this in mind.


Have fun! :guitar:

---

### Post by karth on 2007-11-19
Haven't you ever experienced crashes when **you** get "dominated" in TF2?

---

