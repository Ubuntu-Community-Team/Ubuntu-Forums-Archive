---
title: "Getting Puzzle Quest to work"
date: 2008-04-02
forum: Wine
---

### Post by OttoDestruct on 2008-04-02
I'm having trouble getting puzzle quest to work. The last instructions from the wine app database might as well be latin to me.

> I got it running by copying a dpnet.dll from my windowspartition into ~/.wine/drive_c/windows/system32/ Then do WINEDLLOVERRIDES="dpnet=n" regsvr32.exe dpnet.dll Then WINEDLLOVERRIDES="dpnet=n" wine Puzzle\ Quest\ Demo.exe

Can anyone explain to me exactly what they did? Those commands both just give me errors.

---

### Post by nebu on 2008-04-02
> Download this dll to ~/.wine/drive_c/windows/system32/, start winecfg and add "dpnet" to the library override (native, builtin).
Then download this dll to your Puzzle Quest directory. The game should now work.

this is from the wine app datebase....

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10277](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10277)

this is pretty clear

---

### Post by OttoDestruct on 2008-04-02
I've done that and the game still fails to launch. It goes to a (full) black screen, then crashes.

---

