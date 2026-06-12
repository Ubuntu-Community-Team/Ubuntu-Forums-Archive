---
title: "Missing DLL file"
date: 2015-09-04
forum: Wine
---

### Post by Aidan_Owen on 2015-09-04
Hi, I tried to install The Sims 4 and vcrun2010, 2012, and 2013 through PlayOnLinux, but when I try to launch the game, I get this error (from debug):

```
[09/04/15 17:52:57] - Running wine- TS4.exe (Working directory : /home/aidan/.PlayOnLinux/wineprefix/Sims/drive_c/The Sims 4/Game/Bin)
err:module:import_dll Library MSVCP120.dll (which is needed by L"C:\\The Sims 4\\Game\\Bin\\TS4.exe") not found
err:module:import_dll Library MSVCR120.dll (which is needed by L"C:\\The Sims 4\\Game\\Bin\\TS4.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\The Sims 4\\Game\\Bin\\TS4.exe" failed, status c0000135

```

How can I fix that? I'm not sure why the DLL file isn't found. I searched for it in the virtual drive and it's there.

---

### Post by miniKOX on 2015-09-05
Have you tried to paste these files directly into path? I mean into the **Bin** catalog
```

The Sims 4\\Game\\Bin\\

```

And such a question: why the path to file has double \\ instead of single one \?

---

