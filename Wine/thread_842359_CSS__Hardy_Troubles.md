---
title: "CS:S  Hardy Troubles"
date: 2008-06-27
forum: Wine
---

### Post by lastelement0 on 2008-06-27
Hey all,

I've been trying to get CS:S to work under WINE for a while.  I am currently on Ubuntu 8.04.  I've managed to get Steam installed, and downloaded CS:S and installed it under Steam.  This is where my troubles begin. I try to play a game and Steam just closes.  It's not like my window closes, the whole process is killed.  I've played with various settings, including turning of the Community in game as I heard that was a problem.  

I was on WINE 1  but downgraded to 0.9.47 and was able to get it to load up, however the game just quit and messed up my resolution (zoomed everything in to about 680x400 or something similar).

Any assistance would be much appreciated.

---

### Post by Fred_E _krugar on 2008-06-27
I know this is gonna suck but set up wine to display steam and hl2.exe to use a virtual desktop, you can set it to 800x600. Once CSS is started you can change the resolution in  game and it will automaticaly resize the virtual window. 


I use a 22inch monitor but during the game I have it set up as a regular 19inch monitor fps are great at this setting.

---

### Post by lastelement0 on 2008-06-28
i tried this but didnt work. after some installs and uninstalls of wine i finally am able to get into a game. however its completely unplayable. it lags so much that i cant do anything. any ideas as to speed things up?

---

### Post by Fred_E _krugar on 2008-06-29
I use the icon on the desktop to start the game. What you have to do is right-click on the Icon and click on properties then click the Application tab.


Once there go to the command line and at the end of the command there add -dxlevel 80. Then change the vidio stuff in the game to medium.  Hope this helps.

---

### Post by lastelement0 on 2008-07-01
that didn't help my situation. im sure its some minor configuration tweak that is needed to get me capable of playing since i can get into CS:S. the matter is just how unbearably slow it is.  

my specs are

Dell Inspiron E1505
Core Duo 
2 GB Ram
ati x1400 mobility 128MB
Ubuntu 8.04

---

### Post by Fred_E _krugar on 2008-07-01
Ok thy this instead of -dxlevel 80 , use -dxlevel 70. My grandson has to use that on his 6800gt.

Also did you change in regedit the amount of ram your card has??

---

### Post by xcesarfrancox on 2008-07-01
> **Fred_E _krugar said:**
> Also did you change in regedit the amount of ram your card has??

How do I do that?? I went on wine wiki but I can't understand how to do that

---

