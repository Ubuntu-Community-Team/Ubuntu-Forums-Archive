---
title: "trying to install Wine on Ubuntu 20.04.6 LTS"
date: 2023-09-18
forum: Wine
---

### Post by reut2 on 2023-09-18
Her is the output I get while trying to install Wine.

> reuven@reuven-OptiPlex-9020:~$ sudo apt install --install-recommends wine-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-stable : Depends: libc6 (>= 2.34) but 2.31-0ubuntu9.9 is to be installed
               Depends: wine-stable-i386 (= 8.0.2~jammy-1)
               Depends: wine-stable-amd64 (= 8.0.2~jammy-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


---

### Post by Rubi1200 on 2023-09-18
I don't use Wine but you need to check your sources list.

You say you are trying to install to 20.04.6 LTS but the errors indicate Jammy repositories which is 22.04 LTS.

Post the output of:
```
cat /etc/apt/sources.list
```

You should also check Software Manager to see what additional repositories or PPAs you've added recently.

---

### Post by MAFoElffen on 2023-09-18
Do:
```

sudo apt-get build-dep --install-recommends wine-stable

```
RE: man apt-get
```

       build-dep
           build-dep causes apt-get to install/remove packages in an attempt
           to satisfy the build dependencies for a source package. By default
           the dependencies are satisfied to build the package natively. If
           desired a host-architecture can be specified with the
           --host-architecture option instead.

           The arguments are interpreted as binary or source package names.
           See the --only-source option if you want to change that.

```

---

### Post by reut2 on 2023-09-18
> **Rubi1200 said:**
> I don't use Wine but you need to check your sources list.

You say you are trying to install to 20.04.6 LTS but the errors indicate Jammy repositories which is 22.04 LTS.

Post the output of:
```
cat /etc/apt/sources.list
```

You should also check Software Manager to see what additional repositories or PPAs you've added recently.

$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe main multiverse restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe main multiverse restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.

---

### Post by reut2 on 2023-09-18
reuven@reuven-OptiPlex-9020:~$ sudo apt-get build-dep --install-recommends wine-stable
Reading package lists... Done
Picking 'wine' as source package instead of 'wine-stable'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 builddeps:wine : Depends: libvkd3d-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


> **MAFoElffen said:**
> Do:
```

sudo apt-get build-dep --install-recommends wine-stable

```
RE: man apt-get
```

       build-dep
           build-dep causes apt-get to install/remove packages in an attempt
           to satisfy the build dependencies for a source package. By default
           the dependencies are satisfied to build the package natively. If
           desired a host-architecture can be specified with the
           --host-architecture option instead.

           The arguments are interpreted as binary or source package names.
           See the --only-source option if you want to change that.

```

---

### Post by MAFoElffen on 2023-09-18
Please go back your last two posts. "Edit Post" > "Go Advanced". Select the text of your commands and output to highlight it. The press the "#" Icon to wrap the highlighted text with CODE Tags.

It is Forum Policy to wrap all commands and output within CODE Tags.

---

### Post by QIII on 2023-09-19
Moved to Wine sub-forum as a more appropriate location.

---

### Post by reut2 on 2023-10-11
I am still trying to get wine64 installed.
See below--is it installed? 
code
> $ wine64 --version
wine-8.0


code
> sudo apt-get remove wine64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wine64' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

code
> $ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe main multiverse restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe main multiverse restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,



---

