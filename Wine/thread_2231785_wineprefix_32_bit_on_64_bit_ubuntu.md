---
title: "wineprefix 32 bit on 64 bit ubuntu?"
date: 2014-06-27
forum: Wine
---

### Post by Promethean on 2014-06-27
I check all over the internet on how to do this. I found the command and typed it in but the there is no directory and I can't find anywhere on the internet on how to create the directory. Help?

---

### Post by deadflowr on 2014-06-27
Moved to the Wine subforum

---

### Post by Toz on 2014-06-28
> **Promethean said:**
> I check all over the internet on how to do this. I found the command and typed it in but the there is no directory and I can't find anywhere on the internet on how to create the directory. Help?
Hello and welcome to the forums.

The directory will be automatically created for you when you run a wine command. I like first running winecfg to create the container and bring up the configuration dialog. To do this and specify a WINE32 architecture, you would run (in a terminal window):
```
WINEARCH=win32 winecfg
```
...and the wine directory will be called **.wine** in your home directory. Note that it is a hidden directory.

You can also specify to use another directory, non-hidden if you prefer, by specifying WINEPREFIX. Something like:
```
WINEARCH=win32 WINEPREFIX=~/MyWine winecfg
```
...will setup a 32-bit wine and use ~/MyWine (directory in your home directory) as the wine directory.

Note, that once you use the WINEARCH or WINEPREFIX variables, you have to re-use them everytime you run a command from the terminal. So for example, if you want to run a windows setup in that prefix for that architecture, you would need to run:
```
WINEARCH=win32 WINEPREFIX=~/MyWine /path/to/setup.exe
```

On more note, you should have a look at [PlayOnLinux]("http://www.playonlinux.com/en/"). It helps to automate and manage these kinds of things better and removes the complexity of having to do it manually. PlayOnLinux is in the official repositories.

---

