---
title: "Wine won't run, &quot;Permission Denied&quot;"
date: 2017-10-05
forum: Wine
---

### Post by cpont63 on 2017-10-05
When I try to run wine by going to the wine file and using ```
./wine
``` I get the error Permission denied. Nothing has worked so far, including sudo and chmod. running wine through the ```
wine
``` command and by clicking on applications doesnt work either. Please help

---

### Post by sonnyke on 2017-10-11
Please follow the below steps and your install should be successful:
1. sudo dpkg --add-architecture i386
2. sudo add-apt-repository ppa:wine/wine-builds
3. sudo apt-get update
4. sudo apt-get install wine

---

### Post by yoshii on 2017-10-15
don't trigger wine directly.  
on first run, instead, run this:

```

winecfg

```
this is the Wine Configuration / preferences menus.  
It will help you to set up Wine better for other programs and is really a necessary step before running stuff.  
It also gets wine running so after that wine programs boot up faster.  

good luck

if you install wine-staging, or wine-development, it will probably be nested inside of the /opt/ folder.  
For example, wine-staging's winecfg is in /opt/wine-staging/bin/wine-staging, as is wine 

It gets kind of confusing, but it's stuff we need to know.

---

