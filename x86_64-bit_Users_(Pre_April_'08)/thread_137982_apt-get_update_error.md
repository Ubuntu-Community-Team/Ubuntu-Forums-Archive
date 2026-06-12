---
title: "apt-get update error"
date: 2006-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by tkang on 2006-03-01
I have been scouring the forums for this but I can't find any soultion

When I try an apt-get update... I get

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Fetched 5B in 1s (5B/s)
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.


I have tried apt-get clean.  I have tried taking out all the packages.  I have tried the default sources.list.  I'm not sure at all how to fix this problem.  I've tried to restart several times and attempt it again, but nothing seems to be  working...

---

### Post by silky05 on 2006-03-01
Try this as root from command line:

apt-get install -f

then try to **update** again:

apt-get update

---

### Post by tkang on 2006-03-02
tkang@TBONE:/usr/bin$ sudo apt-get install -f
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
tkang@TBONE:/usr/bin$
tkang@TBONE:/usr/bin$
tkang@TBONE:/usr/bin$

---

### Post by tkang on 2006-03-02
bump!

---

### Post by silky05 on 2006-03-02
Try this link for resolving errors:  

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)

---

