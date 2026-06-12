---
title: "Ubuntu 7.10 64 bit Could not download all repository indexes"
date: 2008-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingleer on 2008-01-14
When I  try to do an update I get the following error - 

> 
Could not download all repository indexes 

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-amd64/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-amd64/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-amd64/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-amd64/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz:) 404 Not Found
 

I already tried Synaptic package manager to solve this problem and restarting. I checked to make sure all the right boxes are ticked under Software Sources. 

When I type 

> 
cat /etc/apt/sources.list
 

in the terminal, I get the following output

> 
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free 


Can anyone tell me what I'm doing wrong? Thanks in advance...

---

### Post by kingleer on 2008-01-14
Just tried entering sudo apt-get update in the terminal. 

I got the following error  

> 
 Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by Yellow Pasque on 2008-01-14
You're not doing anything wrong unless you entered some URL's incorrectly. Double-check on medibuntu's existence/location and comment out if necessary (or use System -> Administration -> Software Sources if you prefer a GUI).

Mine looks like this:
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

### Post by zzHanks on 2008-01-28
I get this error too.

Doos anyone know how to fix this? (I've never changed the URLs)

---

