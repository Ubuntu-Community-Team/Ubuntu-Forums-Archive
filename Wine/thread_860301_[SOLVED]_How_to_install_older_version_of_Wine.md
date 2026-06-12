---
title: "[SOLVED] How to install older version of Wine ?"
date: 2008-07-15
forum: Wine
---

### Post by neur0 on 2008-07-15
I've tried installing all available .deb packages of Wine for Hardy and none resolves my invisible chat problem in Warcraft 3 on bNet. Someone suggested that version 0.9.45 is working ok. So atm I'm downloading the source code since the only available .deb of that version is for Feisty (7.04) and doesn't install with dpkg -i.
Is there any other way of installing the older version?
What do I do with the existing version of Wine, just remove it?

---

### Post by CatKiller on 2008-07-15
If you still have the earlier version in APT's cache, you can open Synaptic and use Package -> Force version... to select the earlier version. You could then use Package -> Lock Version to prevent it being automatically updated.

If the version you want is not still in the cache, I'd imagine that you would need to uninstall the version you have before you could install the older version. You would probably also want to lock the version after you have installed the older version.

Did dpkg complain about dependencies, or was it simply that you already had a newer version that caused it to fail? You might also want to tell the Wine devs about the regression against that bug so that it can be fixed in future versions of Wine.

---

### Post by CatKiller on 2008-07-15
double post

---

### Post by markharding557 on 2008-07-15
error

---

### Post by neur0 on 2008-07-16
Ok, I have managed to install the older version of wine.
It had a dependency issue, but I read somewhere that its not that important, so I installed via dpkg. The bug I had is now gone \\:D/ although the wine now creates zombie processes (probably just an old wine bug), but I'll try to somehow work around it.

New problem is that I now have a broken package error (probably because I ignored the dependency) and there is an "Error: BrokenCount > 0" icon in the tray. How do I tell the system to ignore it or somehow fix it without destroying my current Wine install?

---

### Post by CatKiller on 2008-07-16
You could fix the broken dependency by also installing/forcing whichever package it is that that version of Wine depends on. The packages are archived at [packages.ubuntu.com]("http://packages.ubuntu.com/").

---

### Post by neur0 on 2008-07-16
Thanks, found it in the archives, installed it, locked wine, everything is ok now (except the bad performance of the very old version of wine that is)

Marking as Solved

---

