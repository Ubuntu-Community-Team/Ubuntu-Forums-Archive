---
title: "Source list corrupt"
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by shooter902 on 2007-07-18
Hi all..Well I've just had Feisty 7.04 AMD 64 installed for a week and I've already broke it!! It's just really never  running QUITE right or good enough till ya break it and then you would give anything if you wouldn't have made that last tweak!! If I learned anything, It's don't screw with a smooth running system at 3 in the morning, and a couple of beers in ya! but hey, thats part of the learning curve, and I did have a little help from some bad ram that helped make things worst.

In any event, I'm just a week old with ANY Linux OS, and I must say that I am having a BLAST! I love this OS...It pains me now to hit the KVM switch back over to the dark side (XP Pro) But it is a fun ride and everyone is totally cool in these forums! no flaming like in the Windows forums..anyway..

I broke my sources.list file and I was wondering if someone with the ultimate sources.list file might post it so that I might just cut and paste it? is it that easy? Is that allowed? Total newbie for the most part. Here is my broken one if someone wouldn't mind poking fun of it and maybe help me fix it..Whichever is easier..I've been trying to soak up so much info in these forums, that easy would be welcome :)


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha amd64 (20070627)]/ gutsy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

# Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
 
Thanks for any help
Regards
Phil

---

### Post by ThrobbingBrain66 on 2007-07-18
Whoa...you really did quite a number to that thing...edgy, fesity and Gutsy repos there. :)

I comment all the deb-src lines cause I don't bother with source packages, but if you would ever need them, you can go to System>Administration>Software Sources and then check the box for source code.

Anyway, here it is:

## Main & Restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Universe & Multiverse                                                   
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe 

## Bug Fixes
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe

## Backports
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe 

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe 
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe 

## Proposed Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted multiverse universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted multiverse universe

---

### Post by shooter902 on 2007-07-19
> **ThrobbingBrain66 said:**
> Whoa...you really did quite a number to that thing...edgy, fesity and Gutsy repos there. :)

I comment all the deb-src lines cause I don't bother with source packages, but if you would ever need them, you can go to System>Administration>Software Sources and then check the box for source code.

Anyway, here it is:

## Main & Restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Universe & Multiverse                                                   
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse universe 

## Bug Fixes
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe

## Backports
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted multiverse universe 

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe 
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe 

## Proposed Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted multiverse universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted multiverse universe

Thanks throbbingbrain..I am still having issues with line errors (line 12 I think) I forget the error at the moment and I don't have the system in front of me right now. I have a second drive that I loaded with 7.10  to see how it ran....Errrr..I'm finding that none of the releases I have tried like my logitech MX laser mouse, I would love to solve that problem.

I will try and troubleshoot the source list problem and see what happens! Or maybe I will just reload..I wasn't that far into the configuration..but thanks for your help!! maybe all I need is more cowbell!! :) ( love that skit)

TTFN

---

### Post by ThrobbingBrain66 on 2007-07-19
did you ```
sudo apt-get update
``` after you copied over the sources?  I looked over the sources I typed and everything seems to be in order.

---

### Post by Corbelius on 2007-07-20
> **shooter902 said:**
> 
deb [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)



lol, see here: [http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

;)

---

