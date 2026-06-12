---
title: "Steam not accepting command line"
date: 2008-01-31
forum: Wine
---

### Post by orgrimdoom on 2008-01-31
Ive got steam installed and working fine, but because i want to run my games fullscreen and get it running faster i tried to use the terminal commands, but they dont actually do anything. Ive tried various ones modified to my path

```
WINEDEBUG=fixme-all wine /home/jareth/.wine/drive_c/Program\ Files/Steam/Steam.exe \
    -width 1280 -height 800 -applaunch 321 \
    -heapsize 512000 +map_background none -opengl
```

none of these actually start steam even though that is the location of steam

the only way i can get it to work is through the default icon it creates with a launch option of
 ```
env WINEPREFIX="/home/jareth/.wine" wine "C:\Program Files\Steam\Steam.exe"
```

also possibly fixable with some of the command line options, but some explosions cause the game to die

ty for any help ^^

---

