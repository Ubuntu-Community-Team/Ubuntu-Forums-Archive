---
title: "Apt-get problem ... ?"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbee on 2006-01-14
I'm having a problem with apt-get. I'm trying to install samba but it won't work for some reason. First it asks me to put in the AMD breezy badger, then it says that theres a md5sum error and asks me to run an update. I've tried everything but nothing works unfortunately. 
```

Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/pool/main/s/samba/samba_3.0.14a-6ubuntu1_amd64.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
... the disk I'm using was the one I used to install the system so it should work ?
why do I need to put in my disk just to install samba ?

---

### Post by jensyt on 2006-01-14
I'd suggest going into synaptic and changing your repositories to the online ones.

I don't have access to my Ubuntu box right now as I'm on vacation, but there's an option somewhere in synaptic for setting different repositories; it's in some menu, if I can remember correctly.

Or, if you're more of a command line person, you could edit the file `/etc/apt/sources.list'

Just comment out the CDROM and uncomment the other repositories listed.

---

### Post by dbee on 2006-01-14
Oh ya, I forgot about that ... thanks :)

---

### Post by dbee on 2006-01-14
...oops ... I still have a problem, this is my sources.list
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb-src http://kr.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://kr.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://kr.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://kr.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
deb-src http://kr.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://kr.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://kr.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted

```
... everything seems to be in order if I'm not mistaken

---

### Post by dbee on 2006-01-14
Oh ... wait a second, I forgot about the to edit out the cdrom repository b... d'oh

---

