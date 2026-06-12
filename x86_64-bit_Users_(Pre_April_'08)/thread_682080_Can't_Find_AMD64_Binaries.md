---
title: "Can't Find AMD64 Binaries"
date: 2008-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by SpiritMacardi on 2008-01-29
Whenever I run the update manager, I get a message saying:
"http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz: 404 Not Found"
It doesn't seem to effect anything, but I'd like to know why it's happening and if there's a fix to it.

---

### Post by damvcoool on 2008-01-29
try removing the space on gutsy

---

### Post by SpiritMacardi on 2008-01-30
> **damvcoool said:**
> try removing the space on gutsy

Oh, actually that space is an error on my part. It isn't there in the error message.

---

### Post by Yellow Pasque on 2008-01-30
Yeah, I used to get that a lot too. I guess that repo isn't available anymore or perhaps it switched. You can comment out the appropriate line in /etc/apt/sources.list if that error message annoys you. Here's my sources.list for reference:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070809)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy commercial
# deb-src http://archive.canonical.com/ubuntu gutsy commercial

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://packages.dfreer.org gutsy main
```

---

### Post by utUtu on 2008-01-30
> **SpiritMacardi said:**
> Whenever I run the update manager, I get a message saying:
"http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz: 404 Not Found"
It doesn't seem to effect anything, but I'd like to know why it's happening and if there's a fix to it.

This repo is remnants of your feisty installation. It used to be 'feisty-commercial', and when you did a search/replace 'fesity/gutsy' it became 'gutsy-commercial'.  However, it doesn't exist anymore in gutsy.  Just comment or delete it from your sources.list and you should be fine.
:popcorn:

---

