---
title: "Fireworks MX used to work, doesn't anymore - using PlayOnLinux"
date: 2011-11-20
forum: Wine
---

### Post by compiz addict on 2011-11-20
Fireworks MX used to work perfectly fine until I formatted and installed Ubuntu 11.10. Right now I'm using Ubuntu 10.04, and it still doesn't work! This is really annoying because Fireworks is my preferred program for website graphics.

Using PlayOnLinux (the most recent version), Fireworks installs successfully, but crashes when running. PlayOnLinux gives me this when on debug mode:

**File :**Fireworks MX
**Date :** 11/20/11 09:55:58
**PlayOnLinux Version :** 4.0.14
**File content :**
```

#!/bin/bash
[ "$PLAYONLINUX" = "" ] \&\& exit 0
source "$PLAYONLINUX/lib/sources"
export WINEPREFIX="/home/eric/.PlayOnLinux//wineprefix/FireworksMX"
export WINEDEBUG=""
cd "/home/eric/.PlayOnLinux//wineprefix/FireworksMX/drive_c/Program Files/Macromedia/Fireworks MX 2004/"
POL_Wine "Fireworks.exe"  $@

```
**Output :**
11/20/11 09:55:58 - [main] Message: Debugger is starting
```

Fireworks MX: line 6: cd: /home/eric/.PlayOnLinux//wineprefix/FireworksMX/drive_c/Program Files/Macromedia/Fireworks MX 2004/: No such file or directory
[POL_Wine] Message: Running wine- Fireworks.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
wine: cannot find L"C:\\windows\\system32\\Fireworks.exe"
[POL_Wine] Message: Wine return: 2
 
```
**Other :**
11/20/11 09:56:52 - [POL_Open] Message: Opening : [http://pastebin.com/PbZAiB82](http://pastebin.com/PbZAiB82)

EDIT: The actual installer for Fireworks never starts, which would explain why Fireworks doesn't exist.

---

### Post by compiz addict on 2011-11-20
The problem was 2 of them:
the EXE that PlayOnLinux told me to download didn't work
the EXE that I already had the worked couldn't be installed by PlayOnLinux

I installed my working EXE <i>without</i> using PlayOnLinux.

It worked.

I don't like PlayOnLinux anymore.

---

