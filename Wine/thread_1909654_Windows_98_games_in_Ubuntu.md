---
title: "Windows 98 games in Ubuntu?"
date: 2012-01-15
forum: Wine
---

### Post by BlueSunshine on 2012-01-15
Is it possible to set Wine so I can play games that are made for Windows 95/98/00?

---

### Post by SkySonata on 2012-01-15
I don't know the technical answer but if you can run Half Life 1, please let me know!

---

### Post by BlueSunshine on 2012-01-15
I will get a copy of it and let you know!

---

### Post by there.is.only.xul on 2012-01-16
Absolutely. If you look on getdeb.net you can find a utility called Wibom (Wine Bottle Management) that will allow you to keep separate bottles for different games and installations, should they be necessary.

If you go under winecfg (Or the menu entry for Wine's Configuration Editor) you can very easily change the OS Wine will spoof, but most Windows 98 games shouldn't need too much modification to these settings. The only problems you may encounter is stuff with DLL files. Figuring out which should be native (Wine's version) and which should be builtin (Provided by Windows or some Windows application) can be a tedious chore.

---

### Post by Toz on 2012-01-16
Also have a look at PlayOnLinux (its in the the repositories). Its an easy-to-use front-end to wine that manages wine bottles and wine versions and has pre-made installation scripts for many games.

[http://appdb.winehq.org/]("http://appdb.winehq.org/") is a good resource for installing games/apps in wine. Search for the game you are looking to install and you'll get ratings and solutions to common problems.

---

