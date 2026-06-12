---
title: "I want to install my game with wine, how would I put this in terminal?"
date: 2020-06-09
forum: Wine
---

### Post by daniel-norton on 2020-06-09
It is in the Downloads folder. My username on my laptop is daniel

Please can someone help? :(

P.S I am running 20.04

---

### Post by howefield on 2020-06-09
Thread moved to the "*Wine*" forum.

---

### Post by Perfect Storm on 2020-06-09
Hello,

If you havn't done it you may want to run winecfg first to set wine up;
```
wincfg
```

Then;
```
wine /home/daniel/Downloads/FILENAME.EXE
```

---

### Post by TheFu on 2020-06-09
Most Windows programs, if they work acceptably, require special settings in WINE to work best. "game" isn't sufficient for anyone to point you to a guide specific to that "game."  It is different.

winehq often has setup instructions. [https://www.winehq.org/](https://www.winehq.org/)
PlayOnLinux often makes installs and running easier. [http://wiki.playonlinux.com/index.php/Main_Page](http://wiki.playonlinux.com/index.php/Main_Page)
There are other tools to make things easier like Lutris. [https://lutris.net/](https://lutris.net/)

Most games that "just work" with WINE are really old.  Also, there are many, many, many, that nobody has figured out how to get working yet.  Sometimes WINE doesn't have required capabilities for some programs to work.  Years ago, I needed a Windows program to work under WINE. That program used ocx libraries, but the ocx support hadn't been created in WINE at the time, so it didn't and wouldn't work.

It is a "nice surprise" when a program works well under WINE, IME.

---

