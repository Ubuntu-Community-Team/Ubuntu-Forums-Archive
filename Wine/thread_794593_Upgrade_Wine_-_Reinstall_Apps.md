---
title: "Upgrade Wine - Reinstall Apps?"
date: 2008-05-14
forum: Wine
---

### Post by SteveF on 2008-05-14
I have WineHQ as a repository and I get occasional update notices anout Wine.  When I get these I have them installed.  My question is, do I need to reinstall my apps?  I didn;t think so and kept runnig them.  Then out of curiosity, I renamed my .wine folder so it would not be found and I ran winecfg.  This created a new .wine folder.  I looked at and noticed that the folders were different from the one I had (it had been a while since I first installed my apps).  I also noticed that some of the DLLs were different in size.

So when I upgrade, am I really getting the latest version?

Thanks,

Steve

---

### Post by cogadh on 2008-05-14
Okay, a little explanation aboout how Wine works. Basically, the .wine directory is a "fake windows" directory that is supposed to have all the necessary files that Windows software needs to see in order to be installed and run (its also where you installed Windows applications reside). However, the default DLLs, EXEs and such that you see in the .wine directory are not the actual binary files, but simply pointers to the real binary files that are installed in /usr/lib/wine (I think that's the right directory, not on my Linux box right now). When you upgrade Wine, those binary files are upgraded so that the existing pointers in the .wine directory are always using the upgraded files. However, when you do install an upgraded Wine, you are supposed to run "wineprefixcreate" to re-update your .wine directory with any necessary pointer and registry changes made to the new version. If you haven't been doing that, then some of the items in your .wine directory might be out of date, but Wine itself is not.

---

### Post by SteveF on 2008-05-14
Thanks cogadh.

So you are saying that if I run wineprefixcreate any missing/new DLLs/links would be added and existing ones would point to the correct Wine binaries?  If I haven't been doing that, I was still running the newest binaries, but I may have been missing some DLL/links?

Steve

---

### Post by cogadh on 2008-05-14
Missing items are unlikely, since there really haven't been any new DLLs added to Wine in a very long time and placeholders already exist for the ones that are still not complete. The DLL pointers will always point to the current binaries, since they are basically dumb and only really care that a binary exists in the correct directory. The big thing you really need to run wineprefixcreate for at this point is registry changes.

---

### Post by YokoZar on 2008-05-15
> **cogadh said:**
> However, when you do install an upgraded Wine, you are supposed to run "wineprefixcreate" to re-update your .wine directory with any necessary pointer and registry changes made to the new version. If you haven't been doing that, then some of the items in your .wine directory might be out of date, but Wine itself is not.
Not anymore.  See: [http://wiki.winehq.org/wineboot](http://wiki.winehq.org/wineboot)

---

### Post by Sleaka J on 2008-05-15
If I upgrade Wine from the Update Manager, does that run either wineboot or wineprefixcreate? Or do I still have to do that myself?

---

### Post by cogadh on 2008-05-15
> **YokoZar said:**
> Not anymore.  See: [http://wiki.winehq.org/wineboot](http://wiki.winehq.org/wineboot)
I assume this is effective with RC1, or is it something that went into effect before that?

---

