---
title: "Way to get 1.5.19 on ubuntu12.10"
date: 2012-12-29
forum: Wine
---

### Post by ELD on 2012-12-29
How would i go about getting back 1.5.19 on ubuntu? 1.5.20 broke eve online and the suggested override doesn't work for me?

I have tried getting packages from the archive but i always seem to have missing deps? :(

---

### Post by wiebeest on 2012-12-29
> **ELD said:**
> How would i go about getting back 1.5.19 on ubuntu? 1.5.20 broke eve online and the suggested override doesn't work for me?

I have tried getting packages from the archive but i always seem to have missing deps? :(

It's not only Eve online. Somethings very wrong with the latest 1.5.20 wine update. Check: [http://ubuntuforums.org/showthread.php?p=12428159#post12428159]("http://ubuntuforums.org/showthread.php?p=12428159#post12428159")

---

### Post by gnush on 2012-12-29
[http://sourceforge.net/projects/wine/files/Source/wine-1.5.19.tar.bz2/download](http://sourceforge.net/projects/wine/files/Source/wine-1.5.19.tar.bz2/download)

Just download and install. But be sure to remove the existing WINE version before installing the older version.

*_Edit:_*

Just read that you've already tried to download it. Oh, well, can you post some information on what dependencies you need?

---

### Post by wiebeest on 2012-12-29
> **gnush said:**
> 
Just read that you've already tried to download it. Oh, well, can you post some information on what dependencies you need?

The win32 libraries seem flawed. 
A lot of people also mention the error report referring to something related to sound. 
Since recently there hasn't been an update to the sound drivers for Ubuntu ALSA, I think it's fairly safe those sound errors are caused by the 32-bit dependencies.

---

### Post by wiebeest on 2012-12-30
> **ELD said:**
> How would i go about getting back 1.5.19 on ubuntu? 

This worked for me, perhaps you should check too? [http://ubuntuforums.org/showpost.php?p=12429342&postcount=6]("http://ubuntuforums.org/showpost.php?p=12429342&postcount=6")

---

### Post by ELD on 2012-12-30
I managed to use playonlinux to get it working, since it lets you use a different version of wine for everything you install it's not my wine of choice.

---

### Post by Lila7714 on 2012-12-30
could get playonlinux. Last time I checked it lets you install any version of wine in your home folder without messing with your packages.

---

### Post by Lila7714 on 2012-12-30
> **ELD said:**
> I managed to use playonlinux to get it working, since it lets you use a different version of wine for everything you install it's not my wine of choice.
Ah, beat me to it. but ya that'll work.

---

