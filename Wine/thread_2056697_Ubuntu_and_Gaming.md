---
title: "Ubuntu and Gaming"
date: 2012-09-12
forum: Wine
---

### Post by nato85 on 2012-09-12
Hey Guys

I have always been a big fan of Ubuntu. I used to use it on my desktop computer here at work until I needed a Windows environment for the software that I now have to use.

I wish to install Ubuntu at home but there is a small problem, one that I know you experts would be able to help me out with.

The problem is that I am an avid gamer. And I wish to be able to play games on Ubuntu as well as general web tasks and such.

Recently I tried out Zorin, I tried it out because it gave it a sort of Windows feel to Linux however I was hoping it would be able to install Windows games on Linux, unfortunately it didnt help me anymore then the last time I tried a linux installation. 

I dont really care about it looking like Windows, I would like to know how to install a windows game properly on Linux.

The problem that I seem to face is, there are many packages that I can use to install a game like Modern Warfare 3, but I always come unstuck when it asks for the second CD.

When I put in the second CD, it never recognises that there is a CD in the drive as I would half expect that the CD ROM icon would come back on the desktop again but it doesn't

Can someone help me out by either directing me to a website that will explain clearly how to install Multi-Disc games in Linux, or what I can do to the Linux installation so when I install multi-disc games i wont need to mount or unmount something causing errors like it has in the past?

I know this sounds like a really noobish question but if I could even get a few games installed. I would ditch windows completely

---

### Post by mastablasta on 2012-09-12
you need to use Wine or play on linux to install Windows games. onyl some games work fully in linux. for MW3 for example the steam version SP seem to not be working: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=24738](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24738)
 
in any case don't expect linux to run most of your windows games. you will be lucky to get any to run. 
 
for multiple disks install look 
here: [http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f](http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f)
and here: [http://wiki.winehq.org/eject](http://wiki.winehq.org/eject)

---

### Post by oldos2er on 2012-09-12
Moved to Wine.

---

### Post by nato85 on 2012-09-12
I know most games dont like running under Linux, but you think with having Wine or some kind of windows emulation going on it be easier then this.

Its really the only thing stopping me from using Ubu full time

---

### Post by thatguruguy on 2012-09-12
> **mastablasta said:**
> you need to use Wine or play on linux to install Windows games. onyl some games work fully in linux. for MW3 for example the steam version SP seem to not be working: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=24738](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24738)
 
in any case don't expect linux to run most of your windows games. you will be lucky to get any to run. 
 
for multiple disks install look 
here: [http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f](http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f)
and here: [http://wiki.winehq.org/eject](http://wiki.winehq.org/eject)

A person running Gentoo had problems, but a person running Ubuntu 12.04 gave it a "Gold" rating.  

I don't run a lot of Windows games, but I do have Portal, Portal 2 and Halo CE, and my son plays Mount&Blade Warband pretty regularly. To state that he would be "lucky to get any to run" is a bit of an overstatement.

---

### Post by nato85 on 2012-09-12
i see a few games and stuff run under ubuntu but i dont want it to be a struggle just to get it on there

---

### Post by alphaamanitin on 2012-09-14
I use DosBox to run my old games (Spear of Destiny, Wolf3d, Commander Keen, etc). 

AlphaA

---

### Post by nato85 on 2012-09-14
Can you run things like Virtual box on Ubuntu to just load into that to play games?

---

### Post by PaulInBHC on 2012-09-14
I have an install disc for Windows XP. I thought I would try Virtual Box just for games. When you set up VB, it limits you to 128mb of video ram. Not good enough for most games.

---

### Post by MikeCyber on 2012-09-15
Most games run well in WINE but not in an emulator alike Virtualbox etc.

---

### Post by raptorak on 2012-09-15
> **MikeCyber said:**
> Most games run well in WINE but not in an emulator alike Virtualbox etc.

This greatly depends on the type of game, I think. I'm mostly into MMO's and the ones that do work run very slow under WINE, and the ones that run alright are often broken after patches.

For the most part though, none of the games I play will run under it.

---

### Post by MikeCyber on 2012-09-15
I run Wolfenstein, Rage etc. with the same FPS etc. as on Windows. Only FSX is remarkably slower, but I've some problems with that. All on 1.4 and I won't bother to update, only until I see a 
fix for FSX.

---

### Post by MrSpike16 on 2012-09-15
In order to install games and programs in Wine that have multiple discs you need to use this command in Terminal to remove disc from drive:

```

wine eject

```

If you have several discs you can use the up arrow key (in Terminal) to bring up this command again.  Saves a bit of time.

---

