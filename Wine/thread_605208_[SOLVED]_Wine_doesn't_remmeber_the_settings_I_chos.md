---
title: "[SOLVED] Wine doesn't remmeber the settings I chose"
date: 2007-11-06
forum: Wine
---

### Post by the8thstar on 2007-11-06
Hello,

Wine doesn't save the settings I choose when I go to Applications > Wine > Configure Wine.

Is it a permission problem?

Help please!:)

---

### Post by Ferrat on 2007-11-06
> **the8thstar said:**
> Hello,

Wine doesn't save the settings I choose when I go to Applications > Wine > Configure Wine.

Is it a permission problem?

Help please!:)

Try using winecfg in the terminal instead, the Applications > Wine menu almost never works as it should for me

---

### Post by the8thstar on 2007-11-08
Thanks, now it's working.

I ran into another problem... for some reason wine can't seem to understand long names in Windows, like 'Program Files' for instance. It returns an error saying that 'Program' wasn't found.

Bummer.:confused:

---

### Post by cogadh on 2007-11-08
You need to add an escape character to the path, like so:
```
wine ~/.wine/drive_c/Program\ Files/<appdirectory>
```
But it is easier and better to change directories to the application's install directory first, then just run the executable with "wine application.exe"

---

### Post by the8thstar on 2008-02-03
Ok thanks!

---

