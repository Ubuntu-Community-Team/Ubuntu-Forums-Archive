---
title: "Ugly aptitude problem"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ariek on 2006-09-22
Hi,

I have been playing around trying to get (beautiful, wonderful) Compiz running on my nVidia AMD64 machine. I know Ubuntu is not a toy, but very hard te resist;-)
Anyway, now I'm getting lib errors which are quite stubborn.

> The following packages have unmet dependencies:
  libcairo2: Depends: libglitz1 (>= 0.5.1+cvs20060213) but it is not installable

This is my sources.list
```
deb http://nl.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#deb http://www.beerorkid.com/automatix/apt dapper main

#deb http://kubuntu.org/packages/amarok-143 dapper main

## These repositories provides the latest Xgl/Compiz stuff built for AMD64
#deb http://ubuntu.systemadministrator.org dapper eyecandy
#deb-src http://ubuntu.systemadministrator.org dapper eyecandy

#deb http://www.beerorkid.com/compiz dapper main
#deb http://ubuntu.compiz.net/ dapper main

```

Hopefully anyone has got some suggestions.

Thanx in advance.

---

### Post by croak77 on 2006-09-22
Are you using the Xgl/Compiz repo? Cause you have to remove the '##' in front of the deb line. Then run sudo aptitude update.

---

### Post by ariek on 2006-09-23
I have tried that several times with the following result:

```
root@server07:/home/arie# aptitude install -f
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libglitz1
The following NEW packages will be installed:
  libglitz1 xserver-xgl
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1786kB/1871kB of archives. After unpacking 4989kB will be used.
Do you want to continue? [Y/n/?]
Get:1 http://ubuntu.systemadministrator.org dapper/eyecandy xserver-xgl 7.0.0+cvs20060625 [1786kB]
Fetched 1786kB in 7s (229kB/s)
(Reading database ... 126121 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz1_0.5.6-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz.so.1.0.0', which is also in package glitz-cvs
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0+cvs20060625_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0+cvs20060625_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/Xgl', which is also in package xorg-xgl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz1_0.5.6-0ubuntu1_amd64.deb
 /var/cache/apt/archives/xserver-xgl_7.0.0+cvs20060625_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libcairo2:
 libcairo2 depends on libglitz1 (>= 0.5.1+cvs20060213); however:
  Package libglitz1 is not installed.
dpkg: error processing libcairo2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libcairo2 (>= 1.0.2-2); however:
  Package libcairo2 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libcairo2 (>= 1.0.2-2); however:
  Package libcairo2 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairo2
 firefox-gnome-support
 firefox

```

---

