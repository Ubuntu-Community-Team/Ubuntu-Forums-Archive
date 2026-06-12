---
title: "REsize window size."
date: 2008-06-16
forum: Wine
---

### Post by Cringle on 2008-06-16
Having a problem with wine.
I want to change the virtual desktop window size. but when I go onto the Wine config.

The 'ok' button is out of view (see screenshot)

Anyway do get around this?

Cheers,
Chris

---

### Post by cogadh on 2008-06-16
Open the /home/<username>/.wine/user.reg file in a text editor (**not** OpenOffice) and scroll down to the bottom of the file. Near the end, there will be an entry that looks something like this:
```
[Software\\Wine\\Explorer\\Desktops] 1213629256
"Default"="640X480"
```
Change the "640X480" (or whatever yours says) to at least 800X600, then save the file and re-run winecfg. You should now be able to access all of winecfg's buttons normally.

---

