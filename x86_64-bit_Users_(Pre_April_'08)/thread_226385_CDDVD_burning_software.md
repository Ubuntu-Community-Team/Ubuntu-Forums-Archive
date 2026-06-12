---
title: "CD/DVD burning software"
date: 2006-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by satimis on 2006-07-31
Hi folks,

Ubuntu-6.06-amd64

I have been running KDE desktop on LinuxOS for most times even though
GNOME Desktop installed but seldomly run.  On CD/DVD burunig I either
ran command lines or ran ran k3b

I just finished installing Ubuntu-6.06-amd64 and found k3b not
installed.  I suppose it is for KDE desktop.  I found
nautilus-cd-burner but it is not the GUI CD/DVD burning package I
expect.  Please advise which package shall I installed and run on GNOME
desktop having similar features as k3b.

TIA

B.R.
satimis

---

### Post by jamesford on 2006-07-31
you CAN instgall k3b in gnome, personally i find gnomebaker perfect for my needs

---

### Post by satimis on 2006-07-31
Hi jamesford,

Tks for your advice.

> personally i find gnomebaker perfect for my needs
$ sudo apt-cache search gnomebaker
No printout

$ sudo apt-cache showpkg gnomebaker
W: Unable to locate package gnomebaker


Please advise which repo provide this package.  TIA

B.R.
satimis

---

### Post by jamesford on 2006-07-31
have a look here [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

after u add those do sudo apt-get update
then sudo apt-get install gnomebaker

---

### Post by Clochard on 2006-08-01
I find Bonfire to be much more to my liking than Gnomebaker.  Think K3b for Gnome.  There's even the latest version (0.4.1) in the AMD64 repo - add this to your /etc/apt/sources.list

deb [http://janvitus.interfree.it/](http://janvitus.interfree.it/) ./

Then apt-get install bonfire

It is still very early but I really do think it will become something special.

---

### Post by satimis on 2006-08-01
Hi jamesford,

Tks for your advice and URL.

After having added extra repositories according to;
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Now I have gnomebaker running on Ubuntu box.

B.R.
satimis

---

### Post by satimis on 2006-08-01
Hi Clochard,

Tks for your advice.

~$ cat /etc/apt/sources.list```

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multive rse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe mul tiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe  multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe m ultiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted univer se multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own  risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe m ultiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted univer se multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk. )
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non free 
 
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Where shall I add following line on "source.lst```

deb http://janvitus.interfree.it/ ./
```

TIA

B.R.
satimis

---

### Post by jamesford on 2006-08-01
just add it at the bottom, doesent matter as long as its on a line of its own

---

### Post by satimis on 2006-08-02
> **jamesford said:**
> just add it at the bottom, doesent matter as long as its on a line of its ownHi,

Noted with tks.

satimis

---

