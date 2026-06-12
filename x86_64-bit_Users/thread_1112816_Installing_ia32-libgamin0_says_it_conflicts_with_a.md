---
title: "Installing ia32-libgamin0 says it conflicts with a non-installed package"
date: 2009-04-01
forum: x86 64-bit Users
---

### Post by StarkRG on 2009-04-01
I have ia32-apt-get installed which might be where the confusion is coming from. When I try to install this package it says that it depends on gamin which is already installed. When I add it to the apt-get install command it says it conflicts with libfam0c102, yet it isn't installed.

```
$ sudo apt-get install gamin ia32-libgamin0 libfam0c102-
apt-get: install gamin ia32-libgamin0 libfam0c102-
Reading package lists... Done
Building dependency tree
Reading state information... Done
gamin is already the newest version.
**Package libfam0c102 is not installed, so not removed**
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libgamin0: Conflicts: libfam0c102
  libgamin0: Conflicts: libfam0c102
E: Broken packages
```

If I remove the ia32-libgamin0 package it works fine so that's the obvious culprit, however when I view the package info I can't find why it's trying to install libfam0c102.

```
$ apt-cache show ia32-libgamin0
Package: ia32-libgamin0
Architecture: amd64
Version: 0.1.9-2ubuntu4~11ubuntu1
Conflicts: ia32-libfam0, libfam0c102
Depends: **libc6-i386** (>= 2.4~11ubuntu1), **gamin**
Provides: ia32-libfam0, libfam0c102
Replaces: ia32-libfam0, libfam0c102
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Description: Client library for the gamin file and directory monitoring system
 Gamin is a file and directory monitoring system defined to be a
 subset of the FAM (File Alteration Monitor) system.
 .
 This package contains the client library for the gamin file and directory
 monitoring system.
Filename: pool/main/g/gamin/libgamin0_0.1.9-2ubuntu4_i386.deb
Installed-Size: 112
MD5sum: 56d66e08665e25a3a87878d2a66aba9a
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Origin: Ubuntu
Original-Maintainer: Michael Banck <mbanck@debian.org>
Priority: optional
SHA1: 6303517277c581022398c6f5a479f3d7efd75dae
SHA256: 5e714239e59b5aa106ff644e950d12b95c9c15730b7289f1b3807b90f7a13862
Section: libs
Size: 19478
Source: gamin (0.1.9-2ubuntu4)
Task: ubuntu-desktop, kubuntu-live, edubuntu-desktop, edubuntu-desktop-kde, xubuntu-desktop,mobile-live, mobile-mid, mobile-netbook-remix, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend
```

As you can see it depends on only two packages, both of which are already installed. Why is it suddenly deciding to install a package it can't?

The non-ia32 version installs just fine.

---

### Post by loomsen on 2009-04-01
Just a thought, what if you remove the 64bit version and install only the ia32 package? Does this work? 
If so, I'd say you're trying to install a 32bit pkg, and it's 64bit equivalent is already installed, right?

Now, while libgamin0 and ia32-libgamin0 differe in their naming, having both installed side by side should be fine. Actually I guess the broken dep is caused by 
libfam0c102

which has the same name for 32 and 64 bit. And because libgamin0 provides libfam0c102, this will not work together... It would prlly if libfam0c102 was named ia32-libfam0c102

---

### Post by StarkRG on 2009-04-01
> **loomsen said:**
> Just a thought, what if you remove the 64bit version and install only the ia32 package? Does this work? 
If so, I'd say you're trying to install a 32bit pkg, and it's 64bit equivalent is already installed, right?

Now, while libgamin0 and ia32-libgamin0 differe in their naming, having both installed side by side should be fine. Actually I guess the broken dep is caused by 
libfam0c102

which has the same name for 32 and 64 bit. And because libgamin0 provides libfam0c102, this will not work together... It would prlly if libfam0c102 was named ia32-libfam0c102
The gamin package requires the libgamin0 package, so it must be installed.

The way ia32-apt-get works is that it modifies the library packages from the 32 bit distro to unpack them in /usr/lib32 and adds ia32- to the begining of the package name. This means I have no clear picture of if this package is from the amd64 repository or the i386 repository.

libfam0c102 isn't installed, nor is it required by any package I'm installing. It shouldn't have any effect. Because of the way ia32-apt-get works there is a package called ia32-libfam0c102, but it isn't installed either. I've tried the same thing with one or both libfam packages installed with the same or very similar results.

I see no reason apt should even be considering libfam for installation in this procedure, it's listed as a conflict, and it's not installed, thus there is NO conflict.  If someone knows of a program that could more easily show me a dependancy/conflict tree of packages it might help figure out apt's thought process.

---

