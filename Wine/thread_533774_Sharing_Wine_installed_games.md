---
title: "Sharing Wine installed games?"
date: 2007-08-24
forum: Wine
---

### Post by MemoryDump on 2007-08-24
is it possible for a multi-user workstation?

currently I have all my games installed under my Wine install ~/.wine

I don't really want to have to re-install all these games under each user who uses my Workstation.

For example my daughter has her games she likes to play, sometimes my brother comes over, logs in and wants to play something I already have installed.

thanks
-MD

---

### Post by MemoryDump on 2007-08-25
perhaps I posted this in the wrong spot.. cause I'm sure Wine Apps/Games can be shared with multiple users.. I just can't find a post about it at the moment :(

---

### Post by cogadh on 2007-08-25
In theory, you could use wineprefixcreate to generate a .wine directory in a shared location:
```
wineprefixcreate --prefix /path/to/.wine
```Then all users would have access to it. When running apps in that directory, you would need to run them with an evironment variable. Something like this:
```
env WINEPREFIX="/path/to/.wine" wine "C:\Program Files\Game\Game.exe"
```

---

