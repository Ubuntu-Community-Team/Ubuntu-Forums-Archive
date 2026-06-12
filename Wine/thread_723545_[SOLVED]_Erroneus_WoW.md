---
title: "[SOLVED] Erroneus WoW"
date: 2008-03-13
forum: Wine
---

### Post by petzworld999 on 2008-03-13
Up until today, WoW worked very well, except for the minimap. Today, I went to play WoW and it would not start. I went to the command line, and ran 
```

wine Wow.exe

```
from the WoW directory. Nothing happened, so I pressed control+c and got this:

```

critta@CRITTAC:~/Games/World of Warcraft$ wine Wow.exe
err:module:LdrInitializeThunk "winmm.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"H:\\Games\\World of Warcraft\\Wow.exe" failed, status c000013a

```

The same thing happens when I run winecfg, but not certain other problems. Anyone have any idea on how to fix this problem?






EDIT: I uninstalled some packages, and it works like it did before.

---

### Post by otakuj462 on 2008-06-20
Same problem here, except with RollerCoaster Tycoon; was working fine one moment, and now it is breaking on this dll. What did you uninstall to fix the problem?

Please let me know. Thanks,

Jake

---

