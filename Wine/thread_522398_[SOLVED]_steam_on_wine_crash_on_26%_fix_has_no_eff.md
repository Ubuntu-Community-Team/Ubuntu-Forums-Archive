---
title: "[SOLVED] steam on wine crash on 26% fix has no effect."
date: 2007-08-10
forum: Wine
---

### Post by nickajeglin on 2007-08-10
I've installed the latest version of wine and steam, and also the mozilla activex thingee from transgaming. I've tried the SteamTemp.exe fix a million times and still get the exact same problem, error message and all. The message is "steam is already running. you may only run one copy of steam at a time." If anyone could help me it would be greatly appreciated.

---

### Post by cogadh on 2007-08-10
Someone alse may have a better idea, but the only way I could get past this is to copy a Steam installation from a Windows machine over my Wine installation of Steam, then delete the ClientRegistry.blob file and launch Steam. It recreates the blob file and runs normally at that point.

---

### Post by nickajeglin on 2007-08-10
that's a great idea, because the one on my windows machine is already updated. :) I'll try it. and thank you for being so amazingly fast.

---

### Post by nickajeglin on 2007-08-10
Hmm. no dice. Exact same error as before. Nothing I do seems to touch this one.

---

### Post by DoktorSeven on 2007-08-10
Seems like I remember running it using **nice** from some instructions on how to get it past that point:

**nice -n 19 wine Steam.exe**

---

### Post by nickajeglin on 2007-08-10
that got it past the 26% thing and I signed in. Thanks a bunch.:) Now it just crashes with this error: "steam.exe (main exception): win32 structuredException at a7b1c381: attempt to read from virtual address 2813444993 without appropriate access rights." after login. I seem to remember seeing something about this somewhere else. I'll take a look around

---

### Post by nickajeglin on 2007-08-10
I got it!!!! I got it!!!! 
Ok. Here's what I did to make it work.

1. Completely uninstall wine and delete .wine

2.Reinstall wine, reinstall steam with the newest version from their site.

3. Try it, it'll stick at 26%

4. Did recommended fix: that thing with steamtemp.exe this made my Steam.exe disappear. 

5. do wine start SteamInstall.msi again and select repair when it asks.

then it worked.

---

