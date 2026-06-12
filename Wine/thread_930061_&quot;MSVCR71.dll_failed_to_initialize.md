---
title: "&quot;MSVCR71.dll failed to initialize"
date: 2008-09-25
forum: Wine
---

### Post by KhaaL on 2008-09-25
Hey all

I have this problem when trying to run civilization 4 which used to work fine. I've used winetricks to install the packages msxml3 vcrun2003 dotnet11 corefonts directx9 and the file msvcr71.dll exist both in the local directory of the game aswell as my wine/system32 folder. I still get this error message when i try to run colonization. What's wrong here?

---

### Post by Ferrat on 2008-09-25
Have you changed setting in winecfg to use native msvcr71.dll ?? 

if not, type winecfg in a terminal, select Libraries then type in msvcr71 and press add

---

### Post by KhaaL on 2008-09-26
> **Ferrat said:**
> Have you changed setting in winecfg to use native msvcr71.dll ?? 

if not, type winecfg in a terminal, select Libraries then type in msvcr71 and press add

Even with that override, i get the same error:

```
err:module:attach_process_dlls "MSVCR71.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\The_Depot\\Coloniz\\Colonization.exe" failed, status c0000005

```

---

### Post by CHaoSlayeR on 2009-04-17
I'm having the same Problem with the "mpr.dll" that I copied from my windows XP partition.

I've read on some other place in the web that some libraries don't play nicely with wine and I expected to get some errors when functions are called but a "failed to initialize" is definetely not the error message I expected to get.

Does someone know how to get those native libraries to work?

Any hint appreciated.

C]-[aoZ

---

### Post by NightMKoder on 2009-04-17
Copying system DLL's is not always a good idea - microsoft usually offers package (like visual c 2005 runtime) that have the dll. use winetricks to install the packages and all should be well.

KhaaL: can we get the full console output (or just the part above the error at least)?

---

