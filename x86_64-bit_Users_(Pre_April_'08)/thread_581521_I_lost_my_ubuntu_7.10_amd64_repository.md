---
title: "I lost my ubuntu 7.10 amd64 repository"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by kstan_79 on 2007-10-19
anybody can give me the repository list at /etc/apt/source.list? I'm lost existing. Now I hard to install many softwares.

---

### Post by John.Michael.Kane on 2007-10-19
> **kstan_79 said:**
> anybody can give me the repository list at /etc/apt/source.list? I'm lost existing. Now I hard to install many softwares.

```
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy multiverse
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-security main restricted
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-security universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-proposed restricted main multiverse universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ gutsy-security multiverse
```

---

### Post by kstan_79 on 2007-10-19
it's work! thank you.

---

### Post by John.Michael.Kane on 2007-10-19
> **kstan_79 said:**
> it's work! thank you.

No problem. Should you have any other issues please post.

---

