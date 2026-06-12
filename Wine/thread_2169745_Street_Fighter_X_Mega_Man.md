---
title: "Street Fighter X Mega Man"
date: 2013-08-23
forum: Wine
---

### Post by fKsAGFX on 2013-08-23
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=14783](http://appdb.winehq.org/objectManager.php?sClass=application&iId=14783)

I want to run Capcom's Street Fighter X Mega Man game on Wine in Ubuntu 13.04. It has a gold rating on the Wine website. The only instruction is to "Install directmusic with winetricks for sound support".

I open winetricks in a terminal with winetricks --gui (add apps) but there is no directX or directmusic in the app list. How do I add these two things to Wine so I can get sound in SFXMM?

---

### Post by Toz on 2013-08-23
*Moving to the **Wine** subforum.*

When you open winetricks, first select "Select the default wineprefix" then look under "Install a Windows DLL or component". Directx9 is called d3dx9 and directmusic is there as well.

Or, from a terminal window:
```
winetricks d3dx9 directmusic
```

---

