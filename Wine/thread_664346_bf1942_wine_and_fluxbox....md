---
title: "bf1942 wine and fluxbox..."
date: 2008-01-11
forum: Wine
---

### Post by wana10 on 2008-01-11
so i have an interesting problem with bf1942. it installed perfectly through wine, and runs great, so long as i click on the wine application menu link created during installation. any other method of starting the game doesn't work, which as you can probably see poses problems for a fluxbox user.

the app menu link is set as an application, name of "Battlefield 1942" and a command of ```
env WINEPREFIX="/home/wesley/.wine" wine "C:\Program Files\EA GAMES\Battlefield 1942\bf1942.exe" 
```

so for fluxbox i made a line in my menu and it goes like this (my steam entry in flux looks the exact same and work perfectly by the way)
```
[exec] (Battlefield1942) {env WINEPREFIX="/home/wesley/.wine" wine "C:\Program Files\EA GAMES\Battlefield 1942\bf1942.exe" }
```
but for some reason that doesn't work. so me being the curious person that i am i loaded a terminal and entered ```
$ wine "C:\Program Files\EA GAMES\Battlefield 1942\bf1942.exe"
Warning: could not find DOS drive for current working directory '/home/wana10', starting in the Windows directory.
```
so that makes sense. i don't have a dos drive in my home directory so next
```
$ cd ./.wine/
~/.wine$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
```
there we go, dosdevices. so now lets
```
~/.wine$ wine "C:\Program Files\EA Games\Battlefield 1942\bf1942.exe"
```
and after this the system thinks for a second and then returns me to the prompt.

so i have no idea why the link in the app menu works but nothing else does. any help would be greatly appreciated as i don't want to have to switch over to gnome to play bf1942.

(and just for the record
```
~/.wine$ wine ./drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942/bf1942.exe
``` doesn't work either.)

edit* fixed my problem. i can launch bf1942 from the terminal by using
```
cd ./.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942/ && wine bf1942.exe
```
if that doesn't work for fluxbox i'll just make a little bash script and tuck it away somewhere.

---

### Post by TwinStinger on 2009-08-16
THANK YOU wana10!!!!!!!!!

You saved me from getting taken to a hospital for mental rehab.

---

