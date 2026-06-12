---
title: "Install games using backupCD in Steam"
date: 2008-02-08
forum: Wine
---

### Post by SoberWarlock on 2008-02-08
I installed wine flawlessly without any problems so far. IT's amazing how people make tuts easy these days :) but I can't seem to find any tut on how to install a game using a Backup CD. I can't figure out how to make the autorun screen pop up. Any ideas :confused:

---

### Post by blackdragon1157 on 2008-02-14
I'm not sure what you mean by backup CD.  I assume if you're waiting for autorun, thats theres a setup.exe somewhere.   Navigate to you CDROM drive and try to run it (if your drive path is different, replace this one with it):

```

cd "/media/cdrom0"
wine setup.exe

```

If it is a multidisk installer, you may have to open up a new terminal and type ```
wine eject
``` to get it to eject the CD.

---

