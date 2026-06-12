---
title: "Desktop Size Problem"
date: 2008-06-05
forum: Wine
---

### Post by amtur_poet on 2008-06-05
I need to know how to reset my default settings in wine. I accidentally set the desktop size too big, and now the window is too large to go down far enough in the "configure wine" to reset this. How might I reset the settings in wine externally? I tried completely removing and re-installing Wine in synaptic, but that kept the settings.

---

### Post by cogadh on 2008-06-05
Either delete the .wine directory or manually edit Wine's registry files. 

The .wine directory is a hidden directory in you home directory, so you will need to unhide files in order to see it. NOTE - If you delete the .wine directory, you will need to reinstall any applications you already had installed in Wine.

To edit Wine's registry files, you will also need to unhide hidden folders, as the registry files are found within the .wine directory. Look in that directory for the user.reg file. Open it with a text editor (NOT OpenOffice) and scroll all the way down to the bottom for an entry that looks something like this:
```
[Software\\Wine\\X11 Driver] 1209401998
"Desktop"="800X600"
```
Yours will say something different on the "Desktop" line, change to at least "800X600" and then save the file. Restart winecfg and all buttons will be accessible.

---

