---
title: "Blockland"
date: 2008-01-05
forum: Wine
---

### Post by Game_boy on 2008-01-05
Blockland is a game where you can build with not-LEGO bricks. It runs on the OpenGL-based Torque Game Engine, a Tribes 2 derivative which does have a Linux port but the creator of Blockland has not released a version like that.

A small (20MB) demo with all of the code but feaures disabled is available [[COLOR="Blue"]here[/COLOR]]("http://blockland.us/index.asp?p=Download") (top link). A weird thing when using wine is that you first must cd to the folder and use "wine blockland" otherwise the game will not load.

It completely crashes with a generic unhandled exception error in its own terminal (not Linux-inherited) either on loading a level or a random 5-30 sec. time period afterwards. There is nothing else useful in the console or the Wine one.

A Wine backtrace is over 1.8GB and I can't actually open it without the text editor crashing, so that's little help.

I am running Wine 0.9.52 on Ubuntu 7.10, and as far back as 0.9.35 at least has the error, however the game worked on Ubuntu 7.04 (uncertain whether the transition in particular was when the problem began).

Since the demo is small and the steps to reproduce is simply starting a one-player map and waiting, I would be grateful if anyone could come up with a useful backtrace or otherwise try out the bug. I have an installation of both XP and Vista which I can transfer native files from.

EDIT:

Intel Core 2 Duo E6400 @2.13GHz
ATI Radeon X1950PRO (R5xx, fglrx 8.42.3)
Ubuntu 7.10 Desktop x86 (Gutsy Gibbon)

Wine 0.9.52
Default settings in official .deb

---

### Post by Game_boy on 2008-01-06
Anyone?

---

### Post by io5cml4z on 2010-11-21
It runs fine for me. No bugs at all. Make sure that you have the latest Blockland (currently v19) and Wine (3.x). Also make sure you have any additional drivers enabled. :popcorn:

---

