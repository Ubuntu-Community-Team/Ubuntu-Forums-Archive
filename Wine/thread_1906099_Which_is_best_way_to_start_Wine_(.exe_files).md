---
title: "Which is best way to start Wine (.exe files) ?"
date: 2012-01-08
forum: Wine
---

### Post by grandsatrap on 2012-01-08
I am copying some application launchers from and old computer that had Wine on it, to my new Ubuntu desktop. Problem: There are at least 4 different ways of launching a Wine program. Can someone explain them to me and tell me which is the best way?

1. A whole ton of stuff
```
env WINEPREFIX="/home/griffin/.wine" wine C:\windows\command\start.exe /Unix /home/griffin/.wine/dosdevices/c:/windows/profiles/All\ Users/Start\ Menu/Programs/Notepad++/Notepad++.lnk
```

2. Call the program directly (and pass it parameters if need be)
```
/home/griffin/.wine/drive_c/apps/filesync/FileSync.exe c:/apps/filesync/writings.fsy
```

3. run Wine and pass the program to it
```
/usr/bin/wine /home/griffin/.wine/drive_c/apps/DU_meter/DUMeter.exe
```

4. set up a special launcher script
```
notepad
```

---

### Post by howefield on 2012-01-08
Thread moved to the "*Wine*" forum.

---

### Post by ergo-proxy on 2012-01-09
Any method which is more convenient to you :)
 
The 4th is ok but before running it make sure you export WINEPREFIX pointing to your installation so:
 
1) export wineprefix
2) run wine

---

