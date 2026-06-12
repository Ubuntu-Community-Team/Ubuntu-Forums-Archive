---
title: "ATI Driver"
date: 2007-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Blue Toes on 2007-07-03
Imtrying to install the linux drivers for the ATI Radon 9200, an this error message comes up when i run it in the terminal

-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

anyone have and solution to this problem?

---

### Post by frostie on 2007-07-03
[http://ubuntuforums.org/archive/index.php/t-243342.html](http://ubuntuforums.org/archive/index.php/t-243342.html)

hth

---

### Post by Blue Toes on 2007-07-03
thanx for the help, but my copm is out to get me, and now its saying stuff like 

: ./ati-installer.sh: /bin/sh: bad interpreter: No such file or directory
Removing temporary directory: fglrx-install

after

ln: creating symbolic link `/etc/alternatives/sh' to `/bin/bash': Permission denied

and

Writing extended state information... Done
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true
A package failed to install.  Trying to recover:

---

### Post by je1117 on 2007-07-03
Blue Toes... I will tell you up front, I have never gotten ATI's drivers to work for my Radeon 9200. Ever. I think I was close once, and then it completely screwed up my fresh Ubuntu install. I am sure I have gotten the same errors as you have  just mentioned, but I cannot recall at what point or what I did about it.

Just use the open source and save yourself a world of pain.

But if you power through and get those working, let me know what kind of performance you can get!

---

### Post by Blue Toes on 2007-07-03
I almost got it to work with a series of commands, but i have one more problem.

whenever I type the command  $  X_VERSION=x710_64a ati-driver-installer-8.28.8.run
 
an actuall message pops up saying i need to run the installer as a super user.   I figure it means sudo ________, but can anyone tell me what that might be?

---

### Post by Praill on 2007-07-03
Why would you want to use fglrx if you have a card that the opensource driver supports? I would almost give my right leg for one of those older cards.
The fglrx drivers sucks, currently. It doesnt even support composite extensions so you are forced to choose between direct rendering and composite extensions (hardware exceleration or beryl).

---

