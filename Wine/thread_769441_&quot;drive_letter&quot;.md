---
title: "&quot;drive letter&quot;"
date: 2008-04-26
forum: Wine
---

### Post by skrag on 2008-04-26
Sorry about the newbie question, I was wondering if there is a way to assign a "drive letter" to my cdrom so that when i run Warcraft 3 The Frozen throne thru wine it will pick up my CD in the tray? i tried the no-cd thing and it hasnt worked for me, any suggestions would help a bunch! :)

---

### Post by joshsmith on 2008-04-26
if you run the program winecfg, and go onto the drives tab you get what you want. but it should already trick windows programs into thinking the really exists a drive letter

in linux, the cd drive is known as /media/cdrom0 (or something similar)

however, if the cd has copy protection this is going to slightly harder (and your best bet is to try the no cd crack again, or get another) as copy protection usually uses some crap bodge windows specific way to verify its a real cd

check out the wine app db for help
:)

---

### Post by skrag on 2008-04-26
thanks for the great help, i booted over to windows and patched the game then re-copyed the directory over, apparently with the most recent patch it no longer requires the cd (thank you blizzard!!) now it works, but its weird it wont work with a link on the desktop it still asks you for the cd but if you open up a file browser and run it then it loads just fine it also loads fine from a launcher on the pannel bar, mabe its my link, who knows

the game works fine now (even b.net) accpet no sound, when you start it the game errors:  "unable to initalize base sound services, sound disabled"

no biggie but if you guys know how to shake the liunx wand at it and make the sound work let me know!

---

### Post by joshsmith on 2008-04-26
about sound:
check wine app db to see if this is a common problem

try another app too. to see if you can get sound from that.

but in case it isnt a common problem, or you cant get sound from anything, run winecfg, go onto the audio tab, and say what box is check (ie alsa or oss)
for me at least i need to change it to oss, then run the program like:
padsp wine {path to application}
from a terminal
(padsp is used make oss sound work with pulseaudio in ubuntu)

---

### Post by skrag on 2008-04-26
the wine app db pretty much said it works, i ran winecfg and basicly tried every driver in there (ALSA, OSS and JACK) and the "test sound" button fails on them all, i tried your command padsp to run it (padsp wine /home/user/Warcraft\ III/Frozen\ Throne.exe") with oss selected as the driver and it still errors, my sound outside of wine works fine (onboard sound), kinda sucks 


:-k

---

### Post by joshsmith on 2008-04-26
to get the test button really working, select oss, close the program, then run the program with padsp
ie 
padsp winecfg
then see if the test sound works. (i just tested it on my computer and it does)

---

### Post by skrag on 2008-04-26
so i ran padsp wincfg, clicked test, it worked so i hit apply then ran padsp wine /home/user/Warcraft\ III/Frozen\ Throne.exe (oh yeah and i re-started in there somewere) now it works! thanks a ton josh, now that i can play TFT i have no reason to use windows at all! 

=D>

---

### Post by joshsmith on 2008-04-26
glad i could help :D

---

### Post by Sef on 2008-04-26
Moved to Wine.

---

### Post by skrag on 2008-04-26
after spending a few hours with it i can say the single player works fine, custom maps work and all. it connects to battle net ok but i was experancing bad lag in ladder games, and in custom maps (dota 6.51), i am on a wireless connection thats about 100ish feet from me (and its peak hours atm), so some of this could be my fault,  ill test more on off-peak hours


oh yeah and it looks way better in -opengl the d3d isnt really bad either though

---

