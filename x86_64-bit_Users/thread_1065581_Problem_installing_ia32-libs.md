---
title: "Problem installing ia32-libs"
date: 2009-02-10
forum: x86 64-bit Users
---

### Post by faziz on 2009-02-10
Hey guys

I am getting 

```
(Reading database ... 127652 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu18_amd64.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.2ubuntu18_amd64.deb (--unpack):

```

on installing ia32-libs, which is preventing both flash-plugin and skype.

This is my sources.list 

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://pk.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pk.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://pk.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://pk.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pk.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://pk.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pk.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://pk.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

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

```

I also have medibuntu.list under /etc/apt/sources.list.d directory which is 

```

## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ intrepid free non-free
#deb-src http://packages.medibuntu.org/ intrepid free non-free

```

Please help me out here.

---

### Post by jespdj on 2009-02-10
The error ("lzma: Decoder error") sounds like the .deb file that you have downloaded is corrupt. The package manager can't unpack the package correctly.

Try:
```
sudo apt-get autoclean autoremove
```
to remove packages, or try removing the downloaded package manually:
```
sudo rm /var/cache/apt/archives/ia32-libs_2.2ubuntu18_amd64.deb
```
and then
```
sudo apt-get update
```
and then try to download and install it again
```
sudo apt-get install ia32-libs
```

---

### Post by faziz on 2009-02-11
Gee thanks!

---

### Post by jespdj on 2009-02-11
So, did you now successfully fix the problem?

---

