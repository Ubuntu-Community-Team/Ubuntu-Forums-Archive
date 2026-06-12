---
title: "cps3 / WINE help on Ubuntu 7.10"
date: 2008-02-08
forum: Wine
---

### Post by dvoyage on 2008-02-08
Im trying to play SFIII on my ubuntu laptop so Im using WINE to run cps3.  However, I can not get the game to load. You normally specify your rom directory in the supplied .ini file, but I have tried everything to no avail.  Do i need to make a new config file??  .ini  not readable through WINE??  Ive been scratching my head over this for a couple of nights. thanks all:confused:

---

### Post by DoktorSeven on 2008-02-08
You can play SFIII using sdlmame (native emulator).  

SDLmame package: [http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)
kxmame-SVN package (compatible with SDLmame): [http://sdcofer.googlepages.com/home](http://sdcofer.googlepages.com/home)

You still need to set the INI file (/etc/sdlmame/mame.ini) to point to your ROM directory, but since you're not going through the Wine converted paths, it should be easier to point to it.

---

### Post by dvoyage on 2008-02-08
yeah, ive thought of giving sdlmame a shot, but hadnt gottenaround to it. no better time than now, yeah?  just for the s & gs, can anyone explain what the issue with cps3/WINE is?  Thanks for all the help!!

---

### Post by dvoyage on 2008-02-09
got sdlmame working!  thanks for the tip.

Id really rather not download all the .chd files since they are so large. I was checking the WINE app db, and cps3 worked on a pclinuxos distro--

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9005](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9005)

any WINE pros here who can give any advice??:confused:

---

