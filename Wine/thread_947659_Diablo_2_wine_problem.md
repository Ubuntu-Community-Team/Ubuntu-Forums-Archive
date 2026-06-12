---
title: "Diablo 2 wine problem"
date: 2008-10-14
forum: Wine
---

### Post by strycx on 2008-10-14
when i try to load it through wine it says

UNHANDLED EXCEPTION:
ACCESS_VIOLATION (c000005)

I still had the cds from a long time ago, so i didnt download it, but i suppose i could try to find the gecko engine to see if that helps. any further information would be greatly appreciated.

---

### Post by nonewmsgs on 2009-04-12
bump

---

### Post by asdfoo on 2009-04-13
> **nonewmsgs said:**
> bump

use a nocd?

---

### Post by TheBuzzSaw on 2009-04-13
The latest Diablo II patch lets you play the game without the CD. Install the latest patch, and set WINE to run in a virtual desktop. That should at least get it working.

---

### Post by nonewmsgs on 2009-04-13
i did install the latest patch installed successfully.
i also tried to follow this after i had the problem
([http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+wine](http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+wine))

but something really stood out to me after doing that.  check this out
[http://img164.imageshack.us/img164/6910/diablo2error.jpg](http://img164.imageshack.us/img164/6910/diablo2error.jpg)
no video modes???

i'm using wine 1.0.1 and ubuntu 8.10 with nvidia driver (geforce 6600)

---

### Post by TheBuzzSaw on 2009-04-13
> **nonewmsgs said:**
> i did install the latest patch installed successfully.
i also tried to follow this after i had the problem
([http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+wine](http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+wine))

but something really stood out to me after doing that.  check this out
[http://img164.imageshack.us/img164/6910/diablo2error.jpg](http://img164.imageshack.us/img164/6910/diablo2error.jpg)
no video modes???

i'm using wine 1.0.1 and ubuntu 8.10 with nvidia driver (geforce 6600)
I never bother with the video mode tests. Not being in a true Windows environment causes them to be confused anyway.

Try using a more up-to-date version of WINE. The "stable" version is missing a ton of patches/upgrades that are in the "development" version.

Are you running in a virtual desktop? If not, are you running dual monitors per chance?

---

### Post by nonewmsgs on 2009-04-13
i have tried virtual desktop to give it a 800x600 mode and no not dual moniters.  

i'm updating my wine and i'll let you know soon.

cheers

---

### Post by nonewmsgs on 2009-04-13
ok still no love :(
i tried enabling and disabling virtual desktop and nothing.

---

### Post by asdfoo on 2009-04-13
> **nonewmsgs said:**
> ok still no love :(
i tried enabling and disabling virtual desktop and nothing.

what do you mean nothing? you run it and nothings happens, no output?

---

### Post by TheBuzzSaw on 2009-04-14
I wish I could be of more help. Try studying WINE's Diablo II information page:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=74](http://appdb.winehq.org/objectManager.php?sClass=application&iId=74)

---

### Post by nonewmsgs on 2009-04-14
i get this

when i try to load it through wine it says

UNHANDLED EXCEPTION:
ACCESS_VIOLATION (c000005)

---

### Post by scrawl on 2009-04-14
c000005, thats a DIABLO error, not WINE. I also had this under Windows. Try reinstalling the game, that should fix it :)

---

