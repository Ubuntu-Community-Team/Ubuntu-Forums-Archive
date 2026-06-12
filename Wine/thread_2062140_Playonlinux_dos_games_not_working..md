---
title: "Playonlinux dos games not working."
date: 2012-09-24
forum: Wine
---

### Post by Sarys on 2012-09-24
I try to play Blood from gog but I keep getting this to my debugger  "- Running wine-1.4-dos_support_0.5 BLOOD.EXE (Working directory : /home/sarys/.PlayOnLinux/wineprefix/OneUnitWholeBlood_gog/drive_c/Program Files/GOG.com/One Unit Whole Blood)
Dosbox front-end for PlayOnLinux
[PlayOnLinux] Working in /home/sarys/.PlayOnLinux//wineprefix/OneUnitWholeBlood_gog
[PlayOnLinux] Detecting program directory to run: C:\Program Files\GOG.com\One Unit Whole Blood
[POL_LoadVar_ScreenResolution] [1;34mMessage:[0m Screen width: 1366
[POL_LoadVar_ScreenResolution] [1;34mMessage:[0m Screen height: 768
DOSBox: error while loading shared libraries: libvorbis.so.0: cannot open shared object file: No such file or directory"

what's the problem? I get similar error when trying to play gog Master of orion 1 and 2.

---

### Post by thatguruguy on 2012-09-24
Give us more details about your system. 
1. Which version of Ubuntu are you running? 
2. Are you running 64-bit or 32-bit?
3. Have you made any changes to your system?
4. What happens when you open a terminal and type the following:
```
ls /usr/lib/x86_64-linux-gnu/libvorbis.so.*
```

---

### Post by Sarys on 2012-09-24
> **thatguruguy said:**
> Give us more details about your system. 
1. Which version of Ubuntu are you running? 
2. Are you running 64-bit or 32-bit?
3. Have you made any changes to your system?
4. What happens when you open a terminal and type the following:
```
ls /usr/lib/x86_64-linux-gnu/libvorbis.so.*
```

1. 12.04
2. 64-bit
3. I have no idea what you mean.
4. :~$ ls /usr/lib/x86_64-linux-gnu/libvorbis.so.*
/usr/lib/x86_64-linux-gnu/libvorbis.so.0
/usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5

---

### Post by thatguruguy on 2012-09-24
I think we're getting somewhere. What do you get when you type the following?
```
ls /usr/lib/i386-linux-gnu/libvorbis.so.*
```

---

### Post by Sarys on 2012-09-24
> **thatguruguy said:**
> I think we're getting somewhere. What do you get when you type the following?
```
ls /usr/lib/i386-linux-gnu/libvorbis.so.*
```

:~$ ls /usr/lib/i386-linux-gnu/libvorbis.so.*
/usr/lib/i386-linux-gnu/libvorbis.so.0
/usr/lib/i386-linux-gnu/libvorbis.so.0.4.5

---

### Post by thatguruguy on 2012-09-24
Strange. It looks like you have the correct 32-bit version of libvorbis installed. Just for grins, have you tried the following in a terminal?
```
sudo apt-get install ia32-libs
```

---

### Post by Sarys on 2012-09-24
> **thatguruguy said:**
> Strange. It looks like you have the correct 32-bit version of libvorbis installed. Just for grins, have you tried the following in a terminal?
```
sudo apt-get install ia32-libs
```

I gave it a try and it installed something "NEW" so I guess I didn't have something.

EDIT: odd it said that it failed to intall something but it fixed the problem

---

### Post by thatguruguy on 2012-09-24
The next step would be to try to run the game from dosbox directly, without using POL.

---

