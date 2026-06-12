---
title: "[SOLVED] File Z:\install\xtras\ not found on the installation disk?!"
date: 2008-09-24
forum: Wine
---

### Post by LastWho on 2008-09-24
Hi
i ve this software to study medicine, and i couldn't install it with wine,..

its an ".IMG" file, so i mounted it with **AcetoneIso** on this directory:
~/virtual-drivers/1

then i opened the .exe file with wine .. and when the installation starts i receive this message:
File Z:\install\xtras\ not found on the installation disk. Do you want to continue.. 
when i click on yes (thats means xtras will not be installed) the same message appear with all the other folders.. 
at the end i get nothing installed

[IMG]http://i16.servimg.com/u/f16/11/66/67/80/ecg10.png[/IMG]

Actually all the folders wine couldn't find are at: ~/virtual-drivers/1 :
for example: 
**Z:\install\xtras** is at **~/virtual-drivers/1/install/xtras **

```
-r--r--r--  1 root root  332 1998-11-10 19:58 **cdcheckecg.txt**
-r--r--r--  1 root root  332 1998-11-10 19:58 **cdcheckecg.txt**
dr-xr-xr-x  1 root root 2.0K 1999-12-16 11:13 **QT402WIN/**
-r--r--r--  1 root root 598K 2000-08-22 17:11** SETUP.exe**
dr-xr-xr-x  1 root root 2.0K 2000-09-07 11:45** tracings/**
dr-xr-xr-x  1 root root 2.0K 2000-09-11 16:25 ./
dr-xr-xr-x  1 root root 2.0K 2000-09-12 14:21 **install/**

```

if i just could make wine understand that, i ll get my software installed lol :p



(ps: 
For wine i found that there is theses folders:
C:\ contains program Files and windows
Z:\ is the same as " / " 

i opend winecfg and tried to modify the wintoz version for setup.exe .. also i chose Emulate virtual desktop .. but with no results)

Help me please
thanks

---

### Post by pedro_orange on 2008-09-24
Sorry if I'm reading this wrong, but you're saying:

Z: is / (which is root folder)
and you've put the files in ~ (Which is your home folder)

---

### Post by LastWho on 2008-09-24
yes Z:\ for wine is the same as "/"
i opened the winecfg then i click on add application so i found theses folders:

Desktop: 
[INDENT]/ ; My computer ; My documents[/INDENT]

My computers:
[INDENT] (C:) ; (Z:) ; (D:) 
C: program files ; windows
Z: opens "/" with all subfolders (etc, home,..); can we say that its "/"??
D: opens my DVD folder[/INDENT]

My documents: opens  "~"

---

### Post by david_kt on 2008-09-24
> **LastWho said:**
> 
Actually all the folders wine couldn't find are at: ~/virtual-drivers/1 :
for example: 
**Z:\install\xtras** is at **~/virtual-drivers/1/install/xtras **



Try to run winecfg, click on drives tab, click z: drive, and change the link by browsing to 
 ~/virtual-drivers/1 directory.

After that try to run it again and see if that help.

DK

---

### Post by LastWho on 2008-09-24
it works perfectly lol 
thank you so much david :) :)

i love you ubunto!!

---

