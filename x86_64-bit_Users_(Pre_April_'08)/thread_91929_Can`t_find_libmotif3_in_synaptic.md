---
title: "Can`t find libmotif3 in synaptic"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by martinL on 2005-11-18
Hi,

I need OpenMotif in order to run MSC PATRAN on breezy AMD 64. But I can`t find libmotif in synaptic...

Thats my sources.list file:

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Any ideas?

Thanks

Martin

---

### Post by adwait on 2005-11-18
Try 
```
sudo apt-get install libmotif3
```

Works fine on my end.........if it doens't work, try changing the repos to archive.ubuntu.com

---

### Post by martinL on 2005-11-22
I installed libmotif3 but it seems that patran needs the 32bit version of libmotif...

Is it possible to install it on breezy amd64?

Thanks

martin

---

### Post by Kubuntu_Newbie on 2006-03-15
re: error "Couldn't find packge libmotif3"

libmotif3 is only available in the Apt multiverse

Add the following to /etc/apt/sources.list for Breezy.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by cnich23 on 2006-04-09
I am also having this problem in 64bit version i need open motif for citrix

---

