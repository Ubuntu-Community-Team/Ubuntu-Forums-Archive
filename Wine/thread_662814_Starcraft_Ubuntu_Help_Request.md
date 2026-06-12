---
title: "Starcraft Ubuntu Help Request:"
date: 2008-01-09
forum: Wine
---

### Post by Priest Apostate on 2008-01-09
I have been trying to get WINE to work with installing Starcraft to my system (Toshiba Satellite R15-822, Ubuntu Feisty 7.04), but I keep having an issue when attempting to install the game. I have installed the wine program, and have attempted to follow the instructions on this page: [http://ubuntuforums.org/showthread.php?t=168313](http://ubuntuforums.org/showthread.php?t=168313) 
I don't see the command to activate Wine for the install.exe file. How to activate it?
Also, anytime I try to install StarCraft, I get the error message: 

exp1:Error 0x00000003: Path not found

My C Drive is listed as root in Wine
My /media/cdrom0 is listed as Drive Type: CDROM
Any other information needed, just ask. I've checked out the manual online for wine, and I have only run into a brick wall. 

Please help a person struggling to escape the clutches of M$!

---

### Post by FriedChips on 2008-01-09
```
wine /media/cdrom0/install.exe
```
should get you what you want if what you are saying is that the cdrom is mounted as cdrom0 under media. That command should start the installer. If that doesn't work try:
```
cd /media/cdrom0/
wine install.exe
```
that may work better as it appears to be having a path problem.

---

### Post by Technoviking on 2008-01-09
Using the least Wine my help also.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Mike

---

