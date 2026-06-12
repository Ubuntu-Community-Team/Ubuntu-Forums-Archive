---
title: "VLC 0.8.5 won't update?"
date: 2006-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by halcyon on 2006-09-16
I want to be able to use a newer version of VLC since the package that comes with Dapper has horrible h.264 support, so I tried upgrading.  I followed the directions in this thread: [http://ubuntuforums.org/showthread.php?t=198132](http://ubuntuforums.org/showthread.php?t=198132) to the letter, and Synaptic shows that I have their PGP key and everything, but it doesn't recognize the repository, it always installs the 0.8.4 version that comes with Dapper.

It didn't look like they had any amd64 builds, so I'm wondering if it's not possible for me to run their nightlies.


EDIT: I force-architecture'd their nightly i386 deb packages instead, now I get:

vlc: error while loading shared libraries: libhal.so.1: cannot open shared object file: No such file or directory

Sighhhh!  A fix for either method would be appreciated.

---

### Post by Kilz on 2006-09-16
> **halcyon said:**
> I want to be able to use a newer version of VLC since the package that comes with Dapper has horrible h.264 support, so I tried upgrading.  I followed the directions in this thread: [http://ubuntuforums.org/showthread.php?t=198132](http://ubuntuforums.org/showthread.php?t=198132) to the letter, and Synaptic shows that I have their PGP key and everything, but it doesn't recognize the repository, it always installs the 0.8.4 version that comes with Dapper.

It didn't look like they had any amd64 builds, so I'm wondering if it's not possible for me to run their nightlies.


EDIT: I force-architecture'd their nightly i386 deb packages instead, now I get:

vlc: error while loading shared libraries: libhal.so.1: cannot open shared object file: No such file or directory

Sighhhh!  A fix for either method would be appreciated.

There are a few options to run the nightlies.

1. Download the source and compile it for 64bit.
2. [Follow the instructions here]("http://www.tghc.org/staticpages/index.php/32bitapplications") for forcing in a 32bit application. This is going to be a bit of work.
3. Install a [chroot with this script]("http://www.ubuntuforums.org/showthread.php?t=157412") Then you can run any 32bit application by just switching to the chroot. This is probably the easiest because its a media application.

---

### Post by jamesford on 2006-09-16
so h.264 support in dapper vlc is broken ? aha that explains why i cant view certain streams im supposed to be able to view

---

### Post by ron999 on 2006-09-22
posted in error

---

