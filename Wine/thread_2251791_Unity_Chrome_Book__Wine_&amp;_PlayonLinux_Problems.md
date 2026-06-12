---
title: "Unity Chrome Book / Wine &amp; PlayonLinux Problems."
date: 2014-11-06
forum: Wine
---

### Post by Peepaw on 2014-11-06
I have been trying for almost a week to install any version of Wine on my Chromebook running Ubuntu Unity 12.04.

I've looked up many guides, I can't install wine VIA Software-center (more info button appears but install does not), I can install winetricks and I can install Q4Wine, basically, when it comes down to it I get one of two errors.


Exectued Command: ```
sudo apt-get install wine*
```

Error:
```
The following packages have unmet dependencies:
windbind4: Conflicts: winbind but 2:3.6.3-2ubuntu2.11 is to be installed
wine1.4-common : Depends: wine1.4 (= 1.4.1-0ubuntu1~precise1~ppa4) but it is not installable
 winff-doc : Depends: winff but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Executed Command: ```
sudo apt-get install wine1.7
```

Error:
```
E: Unable to locate package wine1.7
E: Couldn't find any package by regex 'wine1.7'
```

No Matter what I type in to install it One of those 2 errors happens with anything I type in. I've tried to install ppa directories and such and those were fine but installing wine itself will not work.

---

### Post by Peepaw on 2014-11-06
bump

---

### Post by Bucky Ball on 2014-11-06
*Thread moved to **Wine**.*

24 hours is the suggested time for bumping. This is an international forum and the person that can help you may not have logged on yet. Thanks and good luck.

---

### Post by oldrocker99 on 2014-11-08
You probably need to have the Universe repositories enabled.
```
sudo gedit /etc/apt/sources.list
```

You'll see at the bottom:
```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.wikimedia.org/ubuntu/ utopic universe
deb-src http://ubuntu.wikimedia.org/ubuntu/ utopic universe
deb http://ubuntu.wikimedia.org/ubuntu/ utopic-updates universe
deb-src http://ubuntu.wikimedia.org/ubuntu/ utopic-updates universe
```

IF the last four lines have a # at the beginning, delete that so the Universe repositories are enabled. Any line beginning with # is ignored.

Then:
```
sudo apt-get update
```
and try installing again.

---

