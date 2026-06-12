---
title: "Age of Empires II and WineHQ"
date: 2008-08-15
forum: Wine
---

### Post by NurChiN on 2008-08-15
There are a lot of threads with such topic. But in all of them there are problems with **[COLOR="Red"]installation[/COLOR]**.

I havent been able to find any thread which is related to improve AoE under ubuntu.

I installed wine, AoE II, and I'm playing it. But there are problems with performance, sound and graphics. I've searched a lot but still havent been able to improve.

Sound works choppy, and often goes off. When I produce many units game slows down. 

Please write here only those who installed and playing AoE II. Other who have problems with installation, videocard drivers search more suitable threads.

---

### Post by NurChiN on 2008-08-15
I'm using Ubuntu 8.04 hardy heron.

ALSA sound system

NVIDIA 8600 gs video card 256mb

WineHQ 1.1.2 version

---

### Post by NurChiN on 2008-08-15
I also want to add that. 

"Quit Current Game" does not work. It just halts. I have to close AoE totally and start from beginnig from terminal

I type in terminal "wine /directory of AoE/age.exe -- -opengl

---

### Post by NurChiN on 2008-08-16
No one plays AoE II

---

### Post by Jsewill on 2009-06-02
I have successfully installed AOE II and the Conquerors expansion on Ubuntu 9.04 Jaunty initially using the version of wine from the ubuntu repositories.

  It's nearly a year later and I have come across this post.  Maybe you've already found your answer, but either way I'll help however I can.

  AOE installs without any winecfg changes.  The game runs under a virtual desktop 800x600.  Otherwise there has been some regression that causes X to restart upon starting (before the game fully starts) or exiting the game.

  I just compiled wine from git with the latest DIB Engine patches from Bug 421 - [http://bugs.winehq.org/show_bug.cgi?id=421]("http://bugs.winehq.org/show_bug.cgi?id=421").  This has fixed so much!  The text in the menus looks almost perfect, and the building/unit queue slowdown is no longer an issue.  The only issue I see left is that the mouse cursor blinks when you move it, and there is a noticible slowdown with any cursor motion during gameplay.

  Let me know if you are still interested in running this game.  I'll help as much as I can.

---

