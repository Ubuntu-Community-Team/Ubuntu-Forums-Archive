---
title: "Tomb Raider Underworld crashes"
date: 2011-10-09
forum: Wine
---

### Post by WallOfShame on 2011-10-09
Hello!
I've been playing Tomb Raider Legend on Wine 1.2.2 on Maverick since many days smoothly without any errors! Recently I installed Tomb Raider Underworld and started the game. The intro played and menu opened. Everything was fast and smooth. I clicked on Start New Game, selected Tomb Raider (I've tried selecting all 3 difficulty levels) and a bomb blast video played which panned out (clear graphics, fire appears, smooth, without any delay, sound is fine!), then a screen with rotating wheel appears (i suppose it indicates "loading"). It rotates for around 60 degrees and stops. The game comes to standstill and a message appears: "TRU.exe has encountered a serious error and needs to close! This error might be due to insufficiency in Wine. Visit winehq.org for tips or report the bug!" Why is this happening, can you help me out?

For further info check this vid: [http://www.youtube.com/watch?v=zGs-54s_HI0](http://www.youtube.com/watch?v=zGs-54s_HI0)
my game crashes at 0:59 exact!

My sys specs:
Maverick | Dual Core 2GHz Intel T4200 GMA| Lenovo G550
RAM 2GB | 250GB HDD | 5GB empty space on file system(maverick)

---

### Post by ergo-proxy on 2011-10-09
Can be anything... did you check [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14559](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14559) ?

Try to use a different wine version (1.3.7) is marked as gold.

---

### Post by WallOfShame on 2011-10-09
> **ergo-proxy said:**
> Can be anything... did you check [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14559](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14559) ?

Try to use a different wine version (1.3.7) is marked as gold.
thanks dude! Can i upgrade wine 1.2.2 to 1.3.7?

---

### Post by ergo-proxy on 2011-10-09
Not really, you have to compile it by your own:

1) make sure you have official wine ppa enabled
2) download required packaged: [I]sudo apt-get build-dep wine1.3
3) download 1.3.7 wine versions [http://www.ibiblio.org/pub/linux/system/emulators/wine/](http://www.ibiblio.org/pub/linux/system/emulators/wine/)
4) unzip it etc
5) open the terminal, navigate to the wine 1.3 directory
6) type: configure
7) type: make
8) when it's done inside the directory there should be a script which you have to run ie.: ./wine /pathto/you/game/game.exe  
[/I]

---

