---
title: "Ubuntu feisty amd64 repository list"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Coyote21 on 2007-09-27
Since Trevino's list of repositories has a few problems, working on amd64 versions of feisty, here's an version of sources.list that I've compiled, from various sources and that works (without any apt-get errors or warnings):

```

# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://pt.archive.ubuntu.com/ubuntu gutsy main restricted
deb http://pt.archive.ubuntu.com/ubuntu gutsyy-proposed main restricted
deb http://pt.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsyy-security main restricted

deb-src http://pt.archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu gutsy-proposed main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://pt.archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://pt.archive.ubuntu.com/ubuntu feisty-proposed universe multiverse
deb http://pt.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

deb-src http://pt.archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu feisty-proposed universe multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://pt.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb-src http://pt.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb http://kubuntu.org/packages/kde-latest feisty main

deb-src http://kubuntu.org/packages/kde-latest feisty main

# Upstream Wine
# GPG key: 387EE263
deb http://wine.budgetdedicated.com/apt feisty main 

deb-src http://wine.budgetdedicated.com/apt feisty main

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 

deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera, VmWare Server and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

# kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde4-3.90.1 feisty main
deb-src http://kubuntu.org/packages/kde4-3.90.1 feisty main

# The repository from Kubuntu Germany
# GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
deb http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview

# Achim&#8217;s Unofficial &#8216;feisty&#8217; Kubuntu packages
# GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc
deb http://www.mpe.mpg.de/~ach/kubuntu/feisty ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/feisty ./

# Ubuntu feisty University Klagenfurt packages
# GPG key-file: http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
# $ sudo apt-key add uniklu-debuild.pub
#   uniklu:         backports and new packages
#   uniklu-intern:  not freely redistributable (jvm), or modified packages
#   uniklu-testing: packages not ready for general use
deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu
deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-intern
deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-intern
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-testing

# Official Beryl Ubuntu Packages (GPG key: 1609B551)
# GPG key-file: http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

# Geole&#8217;s Ubuntu Repository
# GPG key-file: http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
deb http://ubuntu.geole.info/ feisty universe multiverse
deb-src http://ubuntu.geole.info/ feisty universe multiverse
deb http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted
deb-src http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb http://www.linux2go.dk/ubuntu feisty main
deb-src http://www.linux2go.dk/ubuntu feisty main

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ feisty main
deb-src http://snapshots.ekiga.net/ubuntu/ feisty main

# edevelop - e17 (Enlightenment DR 17)
# GPG key: http://lut1n.ifrance.com/repo_key.asc

deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

# syzygy42 repository: avant-window-navigator, exaile, closure&#8230; (GPG key: 8434D43A)
# GPG key-file: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
deb http://download.tuxfamily.org/syzygy42/ feisty all
deb-src http://download.tuxfamily.org/syzygy42/ feisty all

## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ feisty-upure64 main-amd64
deb-src http://download.tuxfamily.org/upure64/ feisty-upure64 main-amd64

## uPure64 Repository (Experimental)
deb http://download.tuxfamily.org/upure64/ feisty-upure64 experimental-amd64
deb-src http://download.tuxfamily.org/upure64/ feisty-upure64 experimental-amd64

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

 It has some of trevin's sources (the ones that worked for me), Corbelius repository see post
[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093), and others that I've found...
 Here's the keys needed, for the packages:

```

#Ubuntu supported packages -> This is the main ubuntu package repository (Probably you won't need it)
# GPG key: 437D05B5

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 437D05B5
sudo gpg --export --armor 437D05B5 | sudo apt-key add -

# Ubuntu community supported packages -> The ubuntu comunity packages
# GPG key: 437D05B5

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 437D05B5
sudo gpg --export --armor 437D05B5 | sudo apt-key add -

# Kubuntu.org bleeding edge KDE -> Kubuntu comunity packages from the latest KDE
# GPG key: DD4D5088

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys DD4D5088
sudo gpg --export --armor DD4D5088 | sudo apt-key add -

# Upstream Wine -> The latest wine packages WineHQ (I didn't tested this one, but it doesn't give any errors) 
# GPG key: 387EE263

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 387EE263
sudo gpg --export --armor 387EE263 | sudo apt-key add -

# Medibuntu multimedia packages 
# GPG key: 0C5A2783

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 0C5A2783
sudo gpg --export --armor 0C5A2783 | sudo apt-key add -

# CANONICAL COMMERCIAL REPOSITORY 
# GPG Key: 437D05B5

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 437D05B5
sudo gpg --export --armor 437D05B5 | sudo apt-key add -

# The repository from Kubuntu Germany
# GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg

sudo wget http://archive.czessi.net/ubuntu/kczessi.gpg
sudo apt-key add kczessi.gpg

# Achim&#8217;s Unofficial &#8216;feisty&#8217; Kubuntu packages
# GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc

sudo wget http://www.mpe.mpg.de/~ach/ach-gpg.asc
sudo apt-key add ach-gpg.asc

# Ubuntu feisty University Klagenfurt packages
# GPG key-file: http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub

sudo wget http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
sudo apt-key add uniklu-debuild.pub

# Official Beryl Ubuntu Packages 
# GPG key: 1609B551

sudo wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
sudo apt-key add root@lupine.me.uk.gpg

# Ubuntu repository for Screenlets 
# GPG key: F854AFD7

sudo wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
sudo apt-key add F854AFD7.gpg

# Geole&#8217;s Ubuntu Repository
# Import the package geole-keyring

sudo apt-get update
sudo apt-get install geole-keyring

# Linux2Go Ubuntu Packages 
# GPG key: E8BDA4E3

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys E8BDA4E3
sudo gpg --export --armor E8BDA4E3 | sudo apt-key add -

# gnomemeeting - ekiga 
# GPG key: 52ABFCB1

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 52ABFCB1
sudo gpg --export --armor 52ABFCB1 | sudo apt-key add -

# Automatix repository 
# GPG key: E23C5FC3

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys E23C5FC3
sudo gpg --export --armor E23C5FC3 | sudo apt-key add -

# edevelop - e17 (Enlightenment DR 17)
# GPG key: http://lut1n.ifrance.com/repo_key.asc

sudo wget http://lut1n.ifrance.com/repo_key.asc | sudo apt-key add -

# syzygy42 repository: avant-window-navigator, exaile, closure&#8230; 
# GPG key: 8434D43A

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 8434D43A
sudo gpg --export --armor 8434D43A | sudo apt-key add -

# Fresh, from the new uPure64 site...

gpg --keyserver hkp://keyserver.ubuntu.com:11371/ --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -



```

Hope it suits you, as it suited me (Since, now I've upgraded my sources.list to gutsy repositories)

--EDITED: The uPure64 repository is on again! :popcorn:

---

### Post by cwrann on 2007-09-27
In the last couple of days the upure64 repository has not been reloading, it might just be me i'm not sure.

---

### Post by cwrann on 2007-09-27
This is the upure 64 repository that is not working for me:

## uPure64 Repository
deb [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64
deb-src [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64

---

### Post by mhenriday on 2007-10-01
This last week or so, _none_ of the **upure64** repositories for **Feisty** have been loading for me : > [http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz:](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz:) 302 Found
[http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/source/Sources.gz:](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/source/Sources.gz:) 302 Found
[http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/binary-amd64/Packages.gz:](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/binary-amd64/Packages.gz:) 302 Found
[http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/source/Sources.gz:](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/source/Sources.gz:) 302 Found
I've also been having trouble with **automatix2** :
> [http://www.getautomatix.com/apt/dists/feisty/Release.gpg](http://www.getautomatix.com/apt/dists/feisty/Release.gpg)
[http://www.getautomatix.com/apt/dists/feisty/main/i18n/Translation-sv_SE.bz2](http://www.getautomatix.com/apt/dists/feisty/main/i18n/Translation-sv_SE.bz2)
and more surprisingly (at least to me) with a newly imported key file and repository from **Google** :
> [http://dl.google.com/linux/deb/dists/stable/Release:](http://dl.google.com/linux/deb/dists/stable/Release:) Unable to find expected entry  non-free/binary-amd64/Packages in Meta-index file (malformed Release file?)
Moreover, when I try to do ```
apt-get update
``` in a terminal, I get the following pleasant surprise :
> E: Kunde inte öppna låsfilen [lock file could not be opened] /var/lib/apt/lists/lock - open (13 Åtkomst nekas [Permission denied])
E: Kunde inte låsa listkatalogen [Could not read list catalogue]
So can it go ! I'm hoping things will improve with the** Gutsy** release in a couple of weeks....

Henri

---

### Post by Coyote21 on 2007-10-02
[quote=mhenriday]

This last week or so, none of the upure64 repositories for Feisty have been loading for me :
Quote:

> 
[http://janvitus.interfree.it/ubuntu/...4/Packages.gz:](http://janvitus.interfree.it/ubuntu/...4/Packages.gz:) 302 Found
[http://janvitus.interfree.it/ubuntu/...ce/Sources.gz:](http://janvitus.interfree.it/ubuntu/...ce/Sources.gz:) 302 Found
[http://janvitus.interfree.it/ubuntu/...4/Packages.gz:](http://janvitus.interfree.it/ubuntu/...4/Packages.gz:) 302 Found
[http://janvitus.interfree.it/ubuntu/...ce/Sources.gz:](http://janvitus.interfree.it/ubuntu/...ce/Sources.gz:) 302 Found


I've also been having trouble with automatix2 :
Quote:

> 
[http://www.getautomatix.com/apt/dist...ty/Release.gpg](http://www.getautomatix.com/apt/dist...ty/Release.gpg)
[http://www.getautomatix.com/apt/dist...tion-sv_SE.bz2](http://www.getautomatix.com/apt/dist...tion-sv_SE.bz2)


and more surprisingly (at least to me) with a newly imported key file and repository from Google :

Quote:
> 
[http://dl.google.com/linux/deb/dists/stable/Release:](http://dl.google.com/linux/deb/dists/stable/Release:) Unable to find expected entry non-free/binary-amd64/Packages in Meta-index file (malformed Release file?)


Moreover, when I try to do
Code:

```

apt-get update

```

in a terminal, I get the following pleasant surprise :
Quote:

> 
E: Kunde inte öppna låsfilen [lock file could not be opened] /var/lib/apt/lists/lock - open (13 Åtkomst nekas [Permission denied])
E: Kunde inte låsa listkatalogen [Could not read list catalogue]


So can it go ! I'm hoping things will improve with the Gutsy release in a couple of weeks....

Henri
[/quote]

Well, the apt-get update error, is means that another apt-get ou dpkg, is running.

I've tested automatix repositories and they've working... uPure64 has been offline, so I've taked it off the list...

---

### Post by mhenriday on 2007-10-02
**Coyote**, after a couple of weeks out in the cold, **Automatix2** repositories are now running for me as well. As regards the **upure64** repositories,  my experience has been that sometimes they're online and sometimes not, but when they are they're quite valuable, so I intend to bear with them a while longer. Besides, **Gutsy** is scheduled to be released in a couple of weeks and I intend to upgrade, so _all_ my present repositories are hanging loose....

The most interesting thing here is the **Google** repository ; I've received a letter from a developer there which I reproduce in part below:
> The repository doesn't yet have an amd64-specific branch. This is coming. In the meantime, it should work to use the full, explicit i386 path:

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) dists/stable/non-free/binary-i386/
Replacing the repository source as instructed above worked like a charm, which I mentioned in my reply (excerpted below) :
> ... I very much look forward to the release of the AMD64 branch ; I do hope that you developers will try to also keep us 64-bit weirdos in mind when releasing new applications and improvements....

Henri

PS : I don't quite understand the problem I'm having with the «**apt-get update**» command ; even if I run it in a terminal directly after booting till **Feisty**, I still get the above error notice. This is really a pain, as my repeated attempts to install [**HPLIP**]("http://hplip.sourceforge.net/downloads.html") (with self-installer), which I need to get my **HP Photosmart 3210** running in **Feisty**, just failed due to this problem (**error code 100**). What's going on ?...

**Update** : To solve the dysfunctional «**apt-get update**» problem, I finally had to resort to reinstalling **Feisty**. The silver lining to this particular cloud is that I was then able to download and install the **HPLIP** system, and now can run my **Photosmart 3210** from **Feisty**. All's well that ends well....

---

### Post by Coyote21 on 2007-10-05
So, gutsy is coming in about two months (I think... :confused). So my list should need to be upgrade in the meantime (probably some things will be added and others deleted, and even others updated, particularly e17, the new enlightenment, that isn't included in gutsy... :( ). But for the one's that will do the upgrade now, the good news is that gutsy supports adobe flash plugin... And their use nsswrapper method... 

Now, for yoy Henri... I will still say more, I've also got that problem too, but doing when i've done an ps aux, I looked that there was always an instance of either dpkg or automatix or even adept running... And I've never know why.

---

### Post by mojoman on 2007-10-06
> **Coyote21 said:**
> So, gutsy is coming in about two months (I think... :confused).

Nope, even better.

---

### Post by mhenriday on 2007-10-06
Well, **coyote**, when I checked the updater this afternoon, the **Automatix2** repositories were once again unavailable (they had worked this morning). So can it go ! But as **mojoman** points out, **Gutsy** is scheduled for release in less than two weeks, so we do not lack reasons for joy ! Now if only I could get my **Creative Soundblaster X-Fi** card to work in **Feisty** on my **AMD 64 X 2** setup, my cup would really run over. And indeed, Creative has just released a driver (about time !), even if a few problems seem to remain with respect to getting it to function as designed. But as the discussion on the [**just released x-fi beta driver**]("http://tinyurl.com/359mh9") shows, step by slow step we seem to be getting there !...

Henri

---

### Post by Coyote21 on 2007-10-09
> **mojoman said:**
> Nope, even better.

So that's why in the grub menu (for the one's that have done the update already), the new kernels appear without the development branch after the kernel image name...

---

