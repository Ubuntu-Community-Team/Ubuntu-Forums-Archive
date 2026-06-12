---
title: "WINE can't see setup.LST file during installation of simple win me app"
date: 2011-08-02
forum: Wine
---

### Post by Rising Eagle on 2011-08-02
WINE can't see setup.LST file during installation of simple win me app

I'm installing eX-Sense Pro under wine in Natty. It's a simple win me/win xp application.

The setup.exe runs fine, but wine seems to not see setup.LST - another file in the same directory:

Setup cannot find C:\users\redwood\Temp\boom1000\setup.LST.
Setup is aborting...

During installation, the boom1000 directory is created and setup.exe is copied into it, but setup.LST is not copied. When I set up boom1000 and copy setup.LST into it, the install process creates boom1001 and repeats the same mistake. 

Any ideas? Thx.

Eagle

---

