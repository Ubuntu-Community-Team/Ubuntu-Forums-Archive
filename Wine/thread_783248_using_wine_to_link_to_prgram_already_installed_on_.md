---
title: "using wine to link to prgram already installed on windows drive"
date: 2008-05-05
forum: Wine
---

### Post by anfractuosities on 2008-05-05
Can I use Wine to run a program that is installed on my windows partition?  DO I need to reinstall it on my ubuntu partition?

---

### Post by anfractuosities on 2008-05-06
bump

---

### Post by ENigma885 on 2008-05-06
I believe there r some Windows applications that can be run this way , but others need some registry keys and stuff to work properly ...thus i prefer to install the program again in Wine

Also u can give it a try to launch the installed Windows application :
1.Go to ur Windows installation partition then Program Files and locate the .exe or wat ever u need to launch the program
2.Open Terminal 
```
wine <the .exe>
``` u can drag the .exe file directly to the terminal window much easier

---

### Post by cogadh on 2008-05-06
Using Wine to run applications from an existing Windows installation has been known to completely screw up Windows. It is strongly recommended that you do not try to do it. From the [Wine FAQ](http://wiki.winehq.org/FAQ)

> **[SIZE="4"]Can I run applications directly off of a Windows installation without reinstalling them?[/SIZE]**

Generally, no. Unless you know otherwise, you should leave your Windows installation alone and install things "fresh" into Wine. **Wine is not designed to interact with an existing Windows installation.**

Moreover, Wine has no way of accessing the registry of a Windows installation. Since many applications store configuration data in the registry, they cannot be "shared" and need to be installed under Wine in order to be used with Wine. This isn't unique to Wine: you'll run into a similar problem under Windows itself if you try and run applications from another Windows installation. Wine (or the other Windows installation) has no way of seeing this data unless it was written into Wine's registry by the program installer.

Some applications are not so tightly coupled with the registry and are instead self-contained within a folder. It may be possible to share these "portable" applications between Windows and Wine. However, this almost always complicates the support process. Please run the installation software which came with the application under a clean Wine configuration before seeking help.

/!\ WARNING: Do not change the symlink ~/.wine/dosdevices/c: (or any other WINEPREFIX) to point to an actual Windows installation. Do not use winecfg to do this either. Doing so can render your Windows installation unusable if write access is enabled/permitted. Note that the default symlinks created by Wine are safe and most users don't find a reason to change them.
Two examples of Wine screwing up a Windows installation (just from one thread in this forum):
[http://ubuntuforums.org/showpost.php?p=4704407&postcount=32](http://ubuntuforums.org/showpost.php?p=4704407&postcount=32)
[http://ubuntuforums.org/showpost.php?p=4809183&postcount=41](http://ubuntuforums.org/showpost.php?p=4809183&postcount=41)

---

