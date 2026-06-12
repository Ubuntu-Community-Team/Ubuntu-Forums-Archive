---
title: "Breezy to Dapper"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by calcioguy9 on 2006-02-14
I'm working on getting my AE working, and I've read the best way to go is to upgrade to dapper.  It's fine if it's not working perfectly, I just want to get wireless going.  

So my question.  I download the latest Dapper .iso file.  Do I have to burn it to a CD, then reinstall and get rid of breezy, or is there a way to just upgrade it?  And what would be the best application to burn the .iso file onto a CD?

Thanks
-Kevin

---

### Post by alfonz on 2006-02-14
First you should take a look at [this post.]("http://www.ubuntuforums.org/showthread.php?t=93157")

your better off to do a dist-upgrade with apt.

```
sudo gedit /etc/apt/sources.list
```

change the name Breezy with Dapper, comment out the backports

```
sudo apt-get update
sudo apt-get dist-upgrade
```


if your brave enough take a crack at [this.]("http://ubuntuforums.org/showthread.php?t=119637")

---

### Post by anirban.sam on 2006-02-14
Just replace breezy with dapper in yr repository's list anf run dist-upgrade

---

### Post by Zach1188 on 2006-02-14
Here is my sources.list file:

> 
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu) breezy main

## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu) breezy main
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu) breezy main
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu) breezy main

Where would I add that (I can't find what your talking about)?

---

### Post by calcioguy9 on 2006-02-14
[QUOTE=alfonz]First you should take a look at [this post.]("http://www.ubuntuforums.org/showthread.php?t=93157")

your better off to do a dist-upgrade with apt.

```
sudo gedit /etc/apt/sources.list
```

change the name Breezy with Dapper, comment out the backports

```
sudo apt-get update
sudo apt-get dist-upgrade
```[/QUOTE]

Thanks.  I'm still using OS X as my primary OS, right now I'm dual booting and trying to learn and figure out this linux thing.

---

### Post by ssam on 2006-02-15
i recomend you try a [daily live cd]("http://cdimage.ubuntu.com/daily-live/") before you upgrade. its a good way to check what will work for you.

and back everything important up.

you may be best to wait for flight 4 which should be released in about a week. (the flight cds are meant to be free from showstoppers, little islands of stability)

---

