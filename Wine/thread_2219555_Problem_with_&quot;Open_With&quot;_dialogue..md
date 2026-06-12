---
title: "Problem with &quot;Open With&quot; dialogue."
date: 2014-04-24
forum: Wine
---

### Post by cbanakis on 2014-04-24
So I managed to get Adobe Illustrator CS6 running in wine.

A great accomplishment if I do say so myself.

The only problem I am having, is with the right-click open with option.

I created a .desktop file under Home/.local/share/applications/

And it almost works.

If Illustrator is already running, and I right-click a file, and open with Adobe Illustrator, it works perfectly.

However, if Illustrator is not already open, I get the following error...
```
There is no windows program configured to open this type of file.
```

I'm hoping that I just missed a mundane detail, and someone will tell me "you need a comma there" lol

Here is my .desktop file
```
[Desktop Entry]
Type=Application
Name=Adobe Illustrator CS6
MimeType=application/illustrator;
Exec=env WINEPREFIX="/home/chris/.wine" wine start /ProgIDOpen Adobe.Illustrator.16 %f
NoDisplay=true
StartupNotify=true
Icon=FADF_Illustrator.0
```

This file is pretty much as far as google would take me.

Thanks for your help

---

