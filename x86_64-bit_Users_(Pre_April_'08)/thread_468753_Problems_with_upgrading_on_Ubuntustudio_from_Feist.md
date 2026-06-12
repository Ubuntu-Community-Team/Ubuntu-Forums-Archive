---
title: "Problems with upgrading on Ubuntustudio from Feisty fawn"
date: 2007-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kagi on 2007-06-09
Hi, I wanted to upgrade on Ubuntustudio. I followed this these instructions: [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty) and because I will need only to edit music I wanted to make the installation with: sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins. But there is an constatnt error appearing just at the begginnig of the installation... it says, that the packages (ubuntustudio-desktop, ubuntustudio-audio, ubuntustudio-audio-plugins) were not found. 
This is my sources.list:

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
##[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

##deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

##deb [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) dapper free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) dapper free non-free

deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

deb [http://dpkg.u32.net/ubuntu](http://dpkg.u32.net/ubuntu) edgy vserver
deb-src [http://dpkg.u32.net/ubuntu](http://dpkg.u32.net/ubuntu) edgy vserver

# deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper misc
# deb-src [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper misc

# deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

# deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

And this is what I get when I do apt-get update:
Downloading failed  [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Any ideas what can be wrong?
Thanks in advance.

---

### Post by cmost on 2007-06-09
Ubuntu Studio is only for i386; there isn't an amd64 (i.e., x86-64) port yet.  If you're already running Feisty x86-32 i386, then you posted this in the wrong forum.  Sorry.

---

### Post by Kagi on 2007-06-09
You're right. I noticed it too late... sorry.

---

