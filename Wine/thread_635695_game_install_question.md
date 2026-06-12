---
title: "game install question"
date: 2007-12-09
forum: Wine
---

### Post by luke9511 on 2007-12-09
hello all, i have a dual boot system setup where ubuntu is on a 8.4 gig hard drive and windows is on another hard drive and i was wondering how do i setup cedega, wine etc to run my game off the windows hard drive without having to install them on the ubuntu drive? thanks in advance for all the help/advice

---

### Post by cogadh on 2007-12-09
From the Wine FAQ on WineHQ.org:
> **Can I run applications directly off of a Windows installation without reinstalling them?**

Generally, no. Unless you know otherwise, you should leave your Windows installation alone and install things "fresh" into Wine. Most applications store their configuration data outside of their own folders, such as in the Windows registry.

This isn't unique to Wine: you'll run into a similar problem under Windows itself if you try and run applications from another Windows installation. Wine (or the other Windows installation) has no way of seeing this data unless it was written into Wine's registry by the program installer.

Some applications, however, are designed to be "portable" and don't use the registry at all, instead storing all of their settings in a file alongside the executable.

Basically, if you know for certain that your appication doesn't use the registry at all, then you can do it by simply adding your Windows drive as a drive in winecfg. I really don't recommend it though.

---

### Post by luke9511 on 2007-12-09
so im guessing cedega would be the same way correct

---

### Post by cogadh on 2007-12-09
Yup, Cedega is essentially the same thing as Wine. You can sometimes make a Wine install and Windows install share the same save game files though. You just need to create a symlink to the Windows save files in the Wine directories. That way, at least you won't have to play two separate games.

---

