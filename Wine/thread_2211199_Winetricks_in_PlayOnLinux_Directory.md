---
title: "Winetricks in PlayOnLinux Directory"
date: 2014-03-14
forum: Wine
---

### Post by RiotsHere on 2014-03-14
How would I open winetricks in a play on linux folder that I made for a game? I wanted to try and use a different sound driver or disable it if the different sound driver doesnt work because in entropia universe it seems that the sound is not working like it should. Its really fuzzy and when I start it if I'm playing music in the back ground that music will also sound the same.

---

### Post by alexftw. on 2014-03-16
Try this:
```

WINEPREFIX=/your/folder/ winetricks

```

You'll have to use the folder which has e.g. "dosdevices" and "system.reg" in it.

---

