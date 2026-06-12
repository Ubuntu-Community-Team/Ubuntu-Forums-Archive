---
title: "Build debian package from cvs"
date: 2005-09-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by xodeus on 2005-09-12
Hi I've tried to build a debian package of gplflash2, but I can't as it is cvs.
As I don't have a source file i did this:
```
mariusz@101c:~/projects/gplflash2-cvs$ dh_make -e xodeus@gmail.com
The directory name must be <package>-<version> for dh_make to work!
I cannot understand the directory name or you have an invalid directory name!

Your current directory is /home/mariusz/projects/gplflash2-cvs, perhaps you could try going to
directory where the sources are?
``` 
I think that I'm in the dir where the sources are. or?
Really don't understand. I'll try to install this first to check it out.

---

### Post by mlomker on 2005-09-12
Trying to package the latest 0.4.13 version?  The .12 is [already available.](http://www.steiner-web.info/rafael/flash/)

---

### Post by Corbelius on 2005-09-13
[QUOTE=xodeus]Hi I've tried to build a debian package of gplflash2, but I can't as it is cvs.
As I don't have a source file i did this:
```
mariusz@101c:~/projects/gplflash2-cvs$ dh_make -e xodeus@gmail.com
The directory name must be <package>-<version> for dh_make to work!
I cannot understand the directory name or you have an invalid directory name!

Your current directory is /home/mariusz/projects/gplflash2-cvs, perhaps you could try going to
directory where the sources are?
``` 
I think that I'm in the dir where the sources are. or?
Really don't understand. I'll try to install this first to check it out.[/QUOTE]

dh_make would the .tar.gz source, create a .tar.gz package with the cvs directory ;)

---

