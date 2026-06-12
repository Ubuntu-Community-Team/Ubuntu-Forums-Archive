---
title: "ubuntu 7.10 server amd64 repository ?"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by alaya on 2007-10-26
I have installed ubuntu 7.10 _server _edition amd64 on the server of my school(Sun V20Z).
I want to install gnome and some other soft.
the problem is that my etc/apt/source.list contain only the cdrom source.
I try to add some other repository( like this ones in this adress:[http://ubuntuforums.org/showthread.php?t=581521]("http://ubuntuforums.org/showthread.php?t=581521") )but it does n t much (index error when I launch apt-get update).
can some body give me the right repository for my gutsy server ?
and what is the commands I have to type to install gnome ?
thank you very much for your help.

---

### Post by dcstar on 2007-10-27
> **alaya said:**
> I have installed ubuntu 7.10 _server _edition amd64 on the server of my school(Sun V20Z).
I want to install gnome and some other soft.
the problem is that my etc/apt/source.list contain only the cdrom source.
I try to add some other repository( like this ones in this adress:[http://ubuntuforums.org/showthread.php?t=581521]("http://ubuntuforums.org/showthread.php?t=581521") )but it does n t much (index error when I launch apt-get update).
can some body give me the right repository for my gutsy server ?
and what is the commands I have to type to install gnome ?
thank you very much for your help.

I can give you the contents of my /etc/apt/sources.list:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://au.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-security universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://getswiftfox.com/builds/debian unstable non-free
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64

```

Please note that I use the "au." repositories, edit these for your own region.

To install Gnome, install the **ubuntu-desktop** meta-package.

---

### Post by alaya on 2007-10-27
thank you 'dcstar',
I have changed 'au' by 'fr', by the way I found this page to generate the sources list: 
[http://www.sourceslist.org/]("http://www.sourceslist.org/")
I installed gnome with command:
apt-get install gnome-core gnome gnome-desktop-environment
it works but when I restart the computer I have this error: 'No X server' !!!
I m now trying your command to install ubuntu-desktop but I think I don't think it will work.
what can I do ?

---

### Post by alaya on 2007-10-27
it works,
the meta package ubuntu-desktop include the X server too :)
thank's

---

### Post by alaya on 2007-10-27
it works,
the meta package ubuntu-desktop include the  X server too :)
thank's

---

