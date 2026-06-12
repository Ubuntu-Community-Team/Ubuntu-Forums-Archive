---
title: "repositories errors"
date: 2008-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by hvacr on 2008-03-25
I am getting an error when I reload the synaptic package manager. I also cannot find the ubuntu-restricted-package. One shows up in add/remove, but says it will not work with amd 64

I am not sure what these errors mean.




Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)

here is my sources list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted web multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse web universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe web #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted web multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe web #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://download.tuxfamily.org/upure64/](http://download.tuxfamily.org/upure64/) gutsy-upure64 main
deb [http://download.tuxfamily.org/upure64/](http://download.tuxfamily.org/upure64/) gutsy-upure64 experimental
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) gutsy main universe
deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) gutsy main universe #Added by software-properties
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by warp99 on 2008-03-25
Remove all occurrences of "web" in the repository lists, then sudo apt-get update. That's why you're getting these errors:

> [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry web/binary-amd64/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dis...dates/Release:](http://archive.ubuntu.com/ubuntu/dis...dates/Release:) Unable to find expected entry web/binary-amd64/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dis...urity/Release:](http://archive.ubuntu.com/ubuntu/dis...urity/Release:) Unable to find expected entry web/binary-amd64/Packages in Meta-index file (malformed Release file?)


---

### Post by hvacr on 2008-03-26
Thanks very much.

---

