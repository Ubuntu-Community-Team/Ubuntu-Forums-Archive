---
title: "start wine"
date: 2007-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chymera on 2007-08-17
i installed wine via the repos at wineHQ .... but i cant get it to start, i dont find any wine entry under Applications, i tried installing wine again but the system said its already there.... tried **sudo wine** .... nothin ... tried **wine PROGRAM** ... it created a wine file in my home directory but said it couldnt find the windows :confused:

---

### Post by Amazona aestiva on 2007-08-17
In terminal type:
```
winecfg
```
If it won't start wine's configuration window, You should try another version.

---

### Post by Chymera on 2007-08-17
yep, i got the window but i still cant find where to start wine from :confused: there's no entry whatsoever of wine under applications

---

### Post by tszanon on 2007-08-17
You have to use wine in terminal, like this:
```
wine <program name.exe>
```

---

### Post by Chymera on 2007-08-17
oh joy, and why is that? can't i just have the wine application somewhere and browse my windows programs through it?

---

### Post by Amazona aestiva on 2007-08-17
To open .exe:
1.right click
2.open with
3.else
4.type wine

---

### Post by Chymera on 2007-08-17
10x, i got used to the winde window browser way of doing it :P

---

### Post by DamjanDimitrioski on 2007-08-17
To use wine, you have to press alt + F2, then write "\wine program_path\program_name.exe".
Or create Desktop launcher, with command "\wine program_path\program_name.exe".
Then double click the Desktop launcher and the program or game will start, probably.
I tested: Heroes iV, notepad, winrar, keygens.
I tested Half Life and Counter Strike, but it's not functioning, i use Cedega for them.

---

### Post by tgm4883 on 2007-08-17
Wine isn't really a program.  It's a translation layer.  So it's different than running other programs.

---

