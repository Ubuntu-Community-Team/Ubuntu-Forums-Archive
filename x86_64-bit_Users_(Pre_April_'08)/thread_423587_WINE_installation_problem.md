---
title: "WINE installation problem"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by PleaseEnjoyThis on 2007-04-26
To make WINE compatible for my 64bit I had to install these libraries, but I got this. More detail on what I was doing...[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)


fer:~$ sudo apt-get install ia32-libs lib32asound2
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs

help would be lovley

---

### Post by Kilz on 2007-04-26
> **PleaseEnjoyThis said:**
> To make WINE compatible for my 64bit I had to install these libraries, but I got this. More detail on what I was doing...[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)


fer:~$ sudo apt-get install ia32-libs lib32asound2
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs

help would be lovley

Ubuntu has a website that makes all packages available. [You may want to just go there to get this package. ]("http://packages.ubuntu.com/feisty/libs/ia32-libs") Then double click on it and let gdebi install it.

---

### Post by reidamd on 2007-04-27
I was having same problem and tried the fix above and get this :

ia32 shared libraries for use on amd64 and ia64 systems
This package contains runtime libraries for the ia32/i386 architecture, configured for use on an amd64 or ia64 Debian system running a 64-bit kernel.

---

### Post by YokoZar on 2007-04-27
I updated the wiki page for you.  You need to enable the Universe repositories to get ia32-libs

---

