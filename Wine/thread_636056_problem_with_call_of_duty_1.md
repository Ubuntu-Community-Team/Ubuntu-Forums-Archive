---
title: "problem with call of duty 1"
date: 2007-12-09
forum: Wine
---

### Post by taavi7 on 2007-12-09
hi, im new in wine and i need ur help. i installed call of duty in windows and i tryed to run it in linux ubuntu buy if i run CoDSP then it says: Couldnt load deafult.cfg. Make sure Call of Duty is run from correct folder. and when i click OK it gives me this: 

COD 1.0 build win-x86 Oct  5 2003
----- FS_Startup -----
Current language: english
Current search path:
H:\/main

File Handles:
----------------------
0 files in pk3 files
ERROR: No languages available because no localized assets were found
----- CL_Shutdown -----
-----------------------
Hunk_Clear: reset the hunk ok
Couldn't load default.cfg.  Make sure Call of Duty is run from the correct folder.

can someone help me please?

---

### Post by Sockerdrickan on 2007-12-09
cd thedir
winedebug=-all wine "codsp.exe"

---

### Post by cogadh on 2007-12-09
Tux0r, king of the short and to the point post! :)

Just to elaborate on that, what you need to do is change directories to the directory where CoD is installed, then run the executable.

---

### Post by taavi7 on 2007-12-09
okey..i dont get the point :D
please tell me step-by-step what i have to do, because im pretty newb in ubuntu :D

---

### Post by cogadh on 2007-12-09
Assuming that CoD is installed in its default location, open a terminal and run this (two separate commands):
```
cd ~/.wine/drive_c/Program\ Files/Call\ of\ Duty/
WINEDEBUG=-all wine CoDSP.exe
```

---

### Post by Sockerdrickan on 2007-12-09
I usually write a script and put it in my home dir

```

#!bin/sh/
cd
cd .wine/drive_c/Program\ Files/Call\ of\ Duty/
WINEDEBUG=-all wine CoDSP.exe

```
Save that as cod.sh and run it with "sh cod.sh"

---

### Post by taavi7 on 2007-12-09
ok i got in now but theres two more things :D,first, in win i can play the game,  but in linux it says that i need to insert the disk although i but no-cd in that folder (in win) because i cant to nothing with my second hard drive and win/linux system folders (i cant create a folder, paste etc.) that was my second problem.

i really hope, that somebody can help me :?

---

### Post by cogadh on 2007-12-09
Okay, please explain that a little more clearly, that barely made sense to me. Are you saying that you used a no CD crack in Windows, but can't in Wine for some reason?

---

### Post by taavi7 on 2007-12-09
yup, in windows i can play it fith the crack but in linux it says that insert the correct cd in rom

---

### Post by Sockerdrickan on 2007-12-09
Try another NoCD then! ;)

---

### Post by taavi7 on 2007-12-10
uuhh..i got it to work now..
and thank you for your help..

---

