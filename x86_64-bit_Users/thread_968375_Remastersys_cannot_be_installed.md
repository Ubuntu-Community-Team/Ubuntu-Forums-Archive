---
title: "Remastersys cannot be installed"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by psypher on 2008-11-02
Hey all.

I'm not sure if this is only 64bit related but I haven't got a 32bit install so here goes.

Setup apt sources to install remastersys but when I try install i get the following error:

```
 sudo apt-get install remastersys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  remastersys: Depends: discover1 but it is not installable
E: Broken packages

```

Looked all over the net but couldn't find anything related to this.

This is for Interpid, here is my sources.list:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://za.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://za.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://za.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://za.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://za.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://za.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://za.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://za.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

#AWN
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main

#Dropbox
deb http://linux.getdropbox.com/ubuntu intrepid main
deb-src http://linux.getdropbox.com/ubuntu intrepid main

# Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/

```

Thanks

---

### Post by cariboo on 2008-11-02
I don't know why the repository isn't working, but if you click the link:

[http://www.remastersys.klikit-linux.com/repository/remastersys/](http://www.remastersys.klikit-linux.com/repository/remastersys/)

you can just clcik on the file and download it. Once it's downloaded just double click on the package and gdebi will install it.

I just reread your post and I see you have a broken package, go to System-->Administration--Synaptic Package Manager-->Edit-->Fix Broken Packages

Jim

---

### Post by Yellow Pasque on 2008-11-03
The repo version seems to have an outdated control file which requests an old version of discover. The package from cariboo's link looks to be properly updated, as its control file requires "discover | discover1"  (i.e. it can use the newer version included in intrepid)

---

### Post by psypher on 2008-11-04
thanks, i fixed the packages and installed from synaptic, working now.

---

### Post by Fragadelic on 2008-11-05
I changed the control file to use either discover1 or discover so it will work with 8.10 and older versions but probably not so well on the 6.x versions which are very outdated now anyway.

I knew about this but didn't want to make any changes until they released 8.10 final to ensure that no other changes for it were needed.

---

