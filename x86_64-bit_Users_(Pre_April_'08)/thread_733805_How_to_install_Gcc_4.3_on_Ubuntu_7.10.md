---
title: "How to install Gcc 4.3 on Ubuntu 7.10"
date: 2008-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by henkm on 2008-03-24
How can I install gcc 4.3 on ubuntu 7.10 64bits

Does the new version of ubuntu uses gcc 4.3??

Does anybody has some experience with this??

---

### Post by insineratehymn on 2008-03-24
My 7.10 box is running this version:
```

gcc:
  Installed: 4:4.1.2-9ubuntu2
  Candidate: 4:4.1.2-9ubuntu2
  Version table:
 *** 4:4.1.2-9ubuntu2 0
        500 cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Packages
        500 http://us.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status

```

But my Hardy box is running:

```

gcc:
  Installed: 4:4.2.3-1ubuntu3
  Candidate: 4:4.2.3-1ubuntu3
  Version table:
 *** 4:4.2.3-1ubuntu3 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

```

So I don't know if that answers your first question or not...

A quick google brings me a debian package for 4.3:

[http://http.us.debian.org/debian/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.0-1_mipsel.deb](http://http.us.debian.org/debian/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.0-1_mipsel.deb)

As per the 64 version... I don't run 64bit, so no experience on installing 32-bit packages on a 64-bit system.

But it should (?) run fine(?).

Anyone else with some experience on this would be greatly appreciated, if not... try installing the above deb, but make sure gcc is removed from your machine first.

---

### Post by fjgaude on 2008-03-24
The beta version of 64-bit Hardy shows gcc as version 4.2.3.

---

### Post by henkm on 2008-03-24
Gcc 4.2 is also oke for me. I want to use OPENMP for building Blender.

Si I could use ubuntu 8.04 Hardy, but is it stable enough??

I tried to install gcc 4.2 in ubuntu 7.10.
First I removed gcc 4.1 and then installed gcc 4.2.
As result ubuntu is not working properly anymore.
The compleet graphicall interface is gone.
I'm sending this message with windows :-)

---

### Post by henkm on 2008-03-24
On the website [http://gcc.gnu.org/install/]("http://gcc.gnu.org/install/")
an installation guide for building gcc is available, mayby I will try that.

---

### Post by spitf1r3 on 2008-04-04
[https://launchpad.net/~ubuntu-toolchain/+archive](https://launchpad.net/~ubuntu-toolchain/+archive)

---

