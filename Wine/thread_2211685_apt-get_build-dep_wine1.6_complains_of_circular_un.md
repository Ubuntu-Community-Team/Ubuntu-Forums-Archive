---
title: "apt-get build-dep wine1.6 complains of circular unmet dependencies"
date: 2014-03-17
forum: Wine
---

### Post by EvilSupahFly on 2014-03-17
I went to the WINE forum at WINEHQ first, and they sent me here instead saying is a distro issue. So, here I am, attempting to build from source so as to incorporate the 1.6 patch from [bug 18070]("http://bugs.winehq.org/show_bug.cgi?id=18070"), but I'm getting problems when using build-dep. I can't install something because it can't install something else and when I trace it through the list, all of the items failing because the next thing in the list can't be installed, because the next thing in the list can't be installed (etc, etc, ad nauseum), I eventually get to a bunch of things that are the current version, leaving me scratching my head and wondering why there's a problem. Even when I force the package version in Synaptic, it tells me there's still unmet stuff that can't be installed because of unmet stuff that can't be installed because of unmet stuff... and so forth, and I would REALLY appreciate some help and insight here! ... Please?

 This is copied from my terminal (apt only -- I'll spare you the junk from Synaptic):

```
evilsupahfly@OptiPlex-GX620:~$ sudo apt-get update
(--- snipped to save space ---)
Reading package lists... Done

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get build-dep wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
 libgl1-mesa-dev : Depends: mesa-common-dev (= 9.2.1-1ubuntu3) but it is not going to be installed
                   Depends: libdrm-dev (>= 2.4.45) but it is not going to be installed
E: Build-dependencies for wine1.6 could not be satisfied.

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get install libgl1-mesa-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dev : Depends: mesa-common-dev (= 9.2.1-1ubuntu3) but it is not going to be installed
                   Depends: libdrm-dev (>= 2.4.45) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get install mesa-common-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mesa-common-dev : Depends: libdrm-dev (>= 2.4.45) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get install libdrm-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libdrm-dev : Depends: libdrm2 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
              Depends: libdrm-intel1 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
              Depends: libdrm-radeon1 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
              Depends: libdrm-nouveau2 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
E: Unable to correct problems, you have held broken packages.

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get install libdrm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdrm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get install libdrm-intel1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdrm-intel1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get install libdrm-radeon1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdrm-radeon1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

evilsupahfly@OptiPlex-GX620:~$ sudo apt-get install libdrm-nouveau2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdrm-nouveau2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Also, in case it helps, I nuked Unity completely, and switched to Cinnamon, and kept LightDM instead of Cinnamon's GDM - much better performance - and I've upgraded my kernel since initial upgrade from 13.04 to 13.10:

```
evilsupahfly@OptiPlex-GX620:~$ uname -a
Linux OptiPlex-GX620 3.13.6-031306-generic #201403070154 SMP Fri Mar 7 06:55:03 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

**/etc/apt/sources.list:**
```
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted
deb-src http://archive.ubuntu.com/ubuntu saucy main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.mirror.iweb.ca/ saucy main restricted
deb-src http://ubuntu.mirror.iweb.ca/ saucy multiverse restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirror.iweb.ca/ saucy-updates main restricted
deb-src http://ubuntu.mirror.iweb.ca/ saucy-updates multiverse restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.mirror.iweb.ca/ saucy universe
deb http://ubuntu.mirror.iweb.ca/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.mirror.iweb.ca/ saucy multiverse
deb http://ubuntu.mirror.iweb.ca/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.mirror.iweb.ca/ saucy-backports main multiverse universe restricted
deb-src http://ubuntu.mirror.iweb.ca/ saucy-backports main multiverse universe restricted #Added by software-properties

deb http://ubuntu.mirror.iweb.ca/ saucy-security restricted main multiverse universe
deb-src http://ubuntu.mirror.iweb.ca/ saucy-security restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb http://ubuntu.mirror.iweb.ca/ saucy-proposed main restricted universe multiverse
deb-src http://ubuntu.mirror.iweb.ca/ saucy-proposed main restricted universe multiverse #Added by software-properties

# Chrome & Google Earth
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://dl.google.com/linux/earth/deb/ stable main

# Minecraft Map Overviewer Project
deb http://overviewer.org/debian ./

# Cinnamon, Gnome3, Java, GIMP, Firefox, XOrg Development,
deb http://ppa.launchpad.net/diesch/testing/ubuntu saucy main
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu saucy main
deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu saucy main
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu saucy main
deb http://ppa.launchpad.net/tualatrix/ubuntu saucy main
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu saucy main
deb http://ppa.launchpad.net/webupd8team/java/ubuntu saucy main
deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu saucy main
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main

# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu saucy main

# Cinelerra Video Editor
deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu saucy main
# deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu saucy main

# Playstation2 EMU
deb http://ppa.launchpad.net/noobslab/pcsx2/ubuntu raring main
deb-src http://ppa.launchpad.net/noobslab/pcsx2/ubuntu raring main

# .MOBI / .EPUB reader
deb http://ppa.launchpad.net/rgibert/ebook/ubuntu saucy main
# deb-src http://ppa.launchpad.net/rgibert/ebook/ubuntu saucy main

# Video4Linux
deb [arch=amd64] http://www.linux-projects.org/listing/uv4l_repo/raring/ raring main

# TimeKpr
#deb http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu oneiric main
#deb-src http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu oneiric main

################################ OLD WINE ###############################
#
# WINE is located in /etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list
#
################################ OLD WINE ###############################
```

**/etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list**:
```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main
```

If any other info is required, please don't hestitate to ask, and I will gladly post it for you!

---

### Post by EvilSupahFly on 2014-03-17
I think I found my problem:

```

The following packages have unmet dependencies:
 libdrm-dev : Depends: libdrm2 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
              Depends: libdrm-intel1 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
              Depends: libdrm-radeon1 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
              Depends: libdrm-nouveau2 (= 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt~raring) but 2.4.49+git20131202.c3d96897-0ubuntu0sarvatt is to be installed
E: Unable to correct problems, you have held broken packages.

```

These came in with Cinnamon and WINE doesn't like them because they aren't the "correct" version for Ubuntu. If I force them to downgrade, will that mess up Cinnamon?

---

### Post by sffvba[e0rt on 2014-03-17
There is a high probability that Cinnamon may not like you doing that (there is a reason they where installed to begin with).

---

### Post by EvilSupahFly on 2014-03-18
From my post on the WINE forums:

[quote="Bob Wya"]@EvilSupahFly

There are WineHQ FAQ pages for this issue.
[SysWow Multiarch 32-bit/64-bit Wine on 64-bit OS](http://wiki.winehq.org/BuildingBiarchWineOnUbuntu)
[32-bit Wine on 64-bit Linux](http://wiki.winehq.org/WineOn64bit)

If you stuck then I would ask on LQ or the Ubuntu forums.

You should be warned that it's quite an advanced/fiddly process now that Canonical/Debian do not ship the build dependencies for 32-bit Wine on 64-bit versions of the OS (since Ubuntu 12.04). When it's easier to install different versions of Wine on 64-bit Gentoo - you know you've got a problem!! I certainly can't be bothered with using Debian as a testing base, for Wine patches, anymore.

Bob[/quote]

Following the directions for Multi-Arch has put me much further ahead than I ever was before, and for simplicity's sake, I've created the directory structure exactly as the guide has, so all my pathnames match letter for letter, except now when I get to this part:

> Still inside the container, do it again, this time pointing to the 64 bit build for data, and the 32 bit tools build for tools:
```
cd $HOME
mkdir wine32
cd wine32
~/wine-git/configure --with-wine64=$HOME/wine64 --with-wine-tools=$HOME/wine32-tools
make -j4

```

I get hung up on **~/wine-git/configure --with-wine64=$HOME/wine64 --with-wine-tools=$HOME/wine32-tools** with this:
```
evilsupahfly@my32bitbox:~/wine32-tools$ ~/wine-git/configure --with-wine64=$HOME/wine64 --with-wine-tools=$HOME/wine32-tools/tools
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for cpp... cpp
checking for the directory containing the Wine tools... configure: error: could not find Wine tools in /home/evilsupahfly/wine32-tools/tools

```

What am I missing?

---

### Post by rofik on 2014-03-24
why you instaled from PPA  ppa:ubuntu-wine/ppa

 If you instal from source 
sudo dpkg -i wine.deb && Sudo apt-get -f install

 for autoFIX depedency

---

