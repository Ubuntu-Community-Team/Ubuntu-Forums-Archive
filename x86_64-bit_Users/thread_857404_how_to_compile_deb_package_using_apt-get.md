---
title: "how to compile deb package using apt-get"
date: 2008-07-12
forum: x86 64-bit Users
---

### Post by pegasusmd on 2008-07-12
Hi all, 

I need to configure a deb package with some options(eg. -fPIC)
I can use apt-get install to install directly but dont know where to add this options. 

how can I use apt-get to compile like this? 

or are there other ways to do this and then install.  

Thanks, 

Dan

---

### Post by forger on 2008-07-12
longer, better form:
[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

short form:
```
sudo apt-get install devscripts build-essential fakeroot
mkdir tempdir
cd tempdir
apt-get source package-name
cd package-name-directory
```
(where package-name-directory is a directory where the package contents are unpacked)
```

sudo apt-get build-dep package-name
debuild -us -uc
```

This is how you package it and not sign it, but don't know how you pass commands to it for configuration

---

### Post by forger on 2008-07-13
You can either edit debian/rules: [http://www.debian.org/doc/debian-policy/ap-pkg-sourcepkg.html#s-pkg-debianrules](http://www.debian.org/doc/debian-policy/ap-pkg-sourcepkg.html#s-pkg-debianrules)
Good tutorial: [http://debathena.mit.edu/packaging/](http://debathena.mit.edu/packaging/)

Or build the package from scratch using: fakeroot checkinstall

---

