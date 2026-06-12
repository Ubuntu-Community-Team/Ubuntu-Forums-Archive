---
title: "nvidia and steam games"
date: 2008-01-04
forum: Wine
---

### Post by darksidedude on 2008-01-04
hello, I am using ubuntu 7,10 for right now, I was wondering how outdated the restricted manager drivers are, because the games I have on steam (Mainly team fortress 2 and Team fortress classic) always lag, that doesnt happen in windows.

I have a nvidia 6200, 1.5gbs of ram amd athlon 2000+ 
this runs flawlessly in windows, I know TF2 works, i looked at all the youtube videos, hopefully I can have the same luck, thanks for your help

---

### Post by sauronsmatrix on 2008-01-18
hey,i had your problem too. i think wine isn't that good with directx 9 and above.

for steam games, add this to the options -dxlevel 81

so ex: wine "/folder/folder2/folder3/game.exe" -options -options -dxlevel81

specifically, i have to run Portal like:
wine "/portal/portal/game.exe" -steam -game portal -dxlevel 81

you should notice a far superior FPS

also, do you have the proper drivers installed for nvidia?
did you enable them via sudo nvidia-glx-config enable?

after doing that, did you restart

---

### Post by darksidedude on 2008-01-19
well, problem is solved, fedora 8 has a RPM in their repos, no messing around with a binnary, just install a RPM, but thanks for the help

---

