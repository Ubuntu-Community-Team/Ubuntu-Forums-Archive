---
title: "[SOLVED] Installing 64 or 32 bit apps"
date: 2007-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Damanther on 2007-12-20
Maybe a silly question, but I was curious how apt-get install, or synaptic knows to install the 64 bit version of some app verses the 32.

I haven't installed it yet, but I was looking over the winehq.com site and they state that the .deb's they provide have 64bit support in them. So I'm left curious as to how, or if it really knows which one to install without doing something like --force-architecture

I'm pretty new to the debian version so I'm not as aquainted with the way debian packages work as I am the RPM types.

---

### Post by Cappy on 2007-12-20
Short Answer: It's hard coded and can ONLY download the 64-bit version

Long Answer:

Apt can only install native architecture package. This is due to several limitations of apt.
This means you can only install 64-bit packages, applications, and libraries. This is the reason for the relatively poor workarounds that ia32-libs and getlibs provide.

Moving on, when you do a "sudo apt-get update" apt-get downloads the package list from your mirror. Let's take a look at 

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)
Apt finds the package lists for your architecture (amd64) on these kinds of lists and creates a database of just the amd64 packages.

You can see this data using the apt-cache tool. Look at ```
apt-cache show apt
```
```

Package: apt
Priority: important
Section: base
Installed-Size: 4500
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: APT Development Team <deity@lists.debian.org>
Architecture: amd64
Version: 0.7.6ubuntu14.1
Replaces: libapt-pkg-doc (<< 0.3.7), libapt-pkg-dev (<< 0.3.7)
Provides: libapt-pkg-libc6.6-6-4.5
Depends: libc6 (>= 2.6-1), libgcc1 (>= 1:4.2.1), libstdc++6 (>= 4.2.1)
Recommends: ubuntu-keyring
Suggests: aptitude | synaptic | gnome-apt | wajig, dpkg-dev, apt-doc, bzip2, lzma, gnupg
Filename: pool/main/a/apt/apt_0.7.6ubuntu14.1_amd64.deb
Size: 1500124
MD5sum: e7e38106446d3b3fe1c4c73f5fffe74c
SHA1: b961fc0670ee047f22d4c4d5bbe02a9452ceb38d
SHA256: 0a87094b4e8d0f753b509d61fb067b458c0b38ccb9b184d418600bf5ff7fd53f
Description: Advanced front-end for dpkg
 This is Debian's next generation front-end for the dpkg package manager.
 It provides the apt-get utility and APT dselect method that provides a
 simpler, safer way to install and upgrade packages.
 .
 APT features complete installation ordering, multiple source capability
 and several other unique features, see the Users Guide in apt-doc.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Build-Essential: yes
Origin: Ubuntu
Task: minimal

```

You can see that the database has the url address stored for the amd64 package already. You can go to any mirror and get that file using that address. For instance,
[http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu14.1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu14.1_amd64.deb)
is just the mirror mirrors.kernel.org/ubuntu/ + pool/main/a/apt/apt_0.7.6ubuntu14.1_amd64.deb

---

### Post by Damanther on 2007-12-21
Thats what I call a quality answer, thanks Cappy.

---

