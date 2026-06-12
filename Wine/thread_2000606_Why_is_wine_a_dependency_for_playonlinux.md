---
title: "Why is wine a dependency for playonlinux?"
date: 2012-06-09
forum: Wine
---

### Post by venom104 on 2012-06-09
You can install multiple versions of wine from playonlinux, and have a separate wine prefix for ALL of them. Why is having a wine install even a requirement?

---

### Post by matt_symes on 2012-06-09
Hi

```
matthew@matthew-Aspire-7540 /var/lib/dpkg/info
 % apt-cache show playonlinux
Package: playonlinux
Priority: optional
Section: multiverse/otherosfs
Installed-Size: 3507
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Games Team <pkg-games-devel@lists.alioth.debian.org>
Architecture: all
Version: 4.1.1-1
**Depends**: python (>= 2.7.1-0ubuntu2), **wine | wine-unstable**, unzip, wget, xterm | x-terminal-emulator, python-wxgtk2.8, imagemagick, cabextract, mesa-utils, gettext-base, binutils, gnupg, icoutils, x11-utils
Suggests: ttf-mscorefonts-installer
Filename: pool/multiverse/p/playonlinux/playonlinux_4.1.1-1_all.deb
Size: 1471182
MD5sum: eeda0c70176193fffa52cfeeb4aa1c80
SHA1: fff795b4c53d22baafb27ef2ea17927018016ebc
SHA256: 98745b465c92313fa5e010d568b2030a9fc094d0de3146130a0928dab6fd732c
**Description**-en: [B]front-end for Wine
 PlayOnLinux is a front-end for wine[/B]. It permits you to easily install Windows
 Games  and softwares on Linux. It is advised to have a functional internet
 connection.
Homepage: http://www.playonlinux.com/
Description-md5: db0c8caa2b53bca0fcef15d3ee31ef10
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

matthew@matthew-Aspire-7540 /var/lib/dpkg/info
```

Kind regards

---

### Post by venom104 on 2012-06-09
> **matt_symes said:**
> Hi

```
matthew@matthew-Aspire-7540 /var/lib/dpkg/info
 % apt-cache show playonlinux
Package: playonlinux
Priority: optional
Section: multiverse/otherosfs
Installed-Size: 3507
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Games Team <pkg-games-devel@lists.alioth.debian.org>
Architecture: all
Version: 4.1.1-1
**Depends**: python (>= 2.7.1-0ubuntu2), **wine | wine-unstable**, unzip, wget, xterm | x-terminal-emulator, python-wxgtk2.8, imagemagick, cabextract, mesa-utils, gettext-base, binutils, gnupg, icoutils, x11-utils
Suggests: ttf-mscorefonts-installer
Filename: pool/multiverse/p/playonlinux/playonlinux_4.1.1-1_all.deb
Size: 1471182
MD5sum: eeda0c70176193fffa52cfeeb4aa1c80
SHA1: fff795b4c53d22baafb27ef2ea17927018016ebc
SHA256: 98745b465c92313fa5e010d568b2030a9fc094d0de3146130a0928dab6fd732c
**Description**-en: [B]front-end for Wine
 PlayOnLinux is a front-end for wine[/B]. It permits you to easily install Windows
 Games  and softwares on Linux. It is advised to have a functional internet
 connection.
Homepage: http://www.playonlinux.com/
Description-md5: db0c8caa2b53bca0fcef15d3ee31ef10
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

matthew@matthew-Aspire-7540 /var/lib/dpkg/info
```Kind regards

You didn't really answer my question; you are just stating the obvious. I know how to look for dependencies in systematic.

---

### Post by forrestcupp on 2012-06-10
> **venom104 said:**
> You didn't really answer my question; you are just stating the obvious. I know how to look for dependencies in systematic.

It's not that he didn't answer your question; it's that he didn't really read it. In the dependency list he posted, he bolded the parts that said that PlayOnLinux is a GUI frontend to Wine. If he would have read your post more thoroughly, he would have seen that you already know that.

I think the reason is that it has to have some place to start. If you didn't already have Wine, some of the functionality wouldn't work when you start out with it. PlayOnLinux starts working with whatever version of Wine you have installed, but if the app's script specifies that a different version works better, it will check to see if you already have it, and if not, it will download it. It doesn't redownload each version of Wine to a new prefix each time you install something. Those prefixes are just for that app's settings and installed files. Wineprefixes are not for the actual Wine binaries.

---

### Post by matt_symes on 2012-06-10
Hi

> It's not that he didn't answer your question; it's that he didn't really read it.

This is a fair point. I certainly think i misinterpreted your question. 

Please understand that many people post on these forums, of differing ability level, and what may seem obvious to one is not to another.

The number of years on the forums or the number of posts is not really a good gauge either.

> Why is having a wine install even a requirement?

I think the point i was trying to make was that playonlinux installed without wine is pretty pointless. 

If you install it using apt or aptitude it will install wine for you if it's not already installed as it's a dependency.

I have talked to people who did not know that playonlinux was a front end to wine. There was a time when i did not know that either.

Hopefully that makes my post clearer to you and i apologise if you thought my first post was condescending.

Kind regards

---

### Post by cwwilson721 on 2012-06-10
To answer the OP's original question:

Play On Linux (POL) is a Graphical User Interface (GUI) for wine.

Wine is the ACTUAL program that provides the semi-functional hooks, DLLs, API, etc, for a Widows program to run in Linux.

Wine does not require POL to function. It is the "core" program. Think of it as the motor in your car. The exact same motor runs in many different cars, but your model only has that motor. Continuing the analogy, POL provides the entire finished car, with drink holders and air-conditioning. Some prefer to "build their own" cars, so don't even use POL (I'm one of those). So, POL needs wine to work, but wine does NOT need POL.

I say wine is "semi-functional" because Windows is "closed source", meaning alot of it's programming code is "secret", and known ONLY to Microsoft. Wine tries to figure out what some of that code does, and provides an open-source route for those programs to work. Since it is VERY complicated to do this, wine cannot provide all ways for a program that works under Windows to always work in Linux. But it does a remarkable job.

I just wish POL would check and see if your Linux install already has a wine install, rather than it installing one anyway.

---

### Post by forrestcupp on 2012-06-10
For anyone who still doesn't understand the OP's question, this is what I think he is asking. He knows that PlayOnLinux is a frontend for Wine and that Wine is required. What is he pointing out is that PlayOnLinux automatically installs whatever version of Wine is needed for the app you are installing. So if it is going to automatically install the proper version of Wine in the process, then why do you have to have Wine already installed to run PlayOnLinux?

Hopefully I answered that question correctly in my previous post.

---

### Post by forrestcupp on 2012-06-10
> **matt_symes said:**
> 
This is a fair point. I certainly think i misinterpreted your question. 

Please understand that many people post on these forums, of differing ability level, and what may seem obvious to one is not to another.

The number of years on the forums or the number of posts is not really a good gauge either.

True words. The first thing that came to my mind when I read the title is that some people don't know that PoL is a frontend to Wine. The OP probably should have expanded on his question a little more to make it clearer.

---

### Post by Colo2 on 2012-06-10
Correct me if I'm wrong. But I believe that wine is a pre-requisit because it installs all of the games inside the same Wine version, using the same registry etc... and uses individual versions of wine to launch the games. This is because each game needs different settings tweeked.

---

