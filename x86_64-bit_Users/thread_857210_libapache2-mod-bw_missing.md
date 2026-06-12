---
title: "libapache2-mod-bw missing?"
date: 2008-07-12
forum: x86 64-bit Users
---

### Post by Termina on 2008-07-12
I'm unable to install libapache2-mod-bw on a 8.04 x86_64 server install.

Here is my /etc/apt/sources.list

```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Does anyone know how I can install it? Google has been no help, and I'm very surprised that such an important package is available on Debian but not Ubuntu. :(

---

### Post by Kilz on 2008-07-12
> **Termina said:**
> I'm unable to install libapache2-mod-bw on a 8.04 x86_64 server install.

Here is my /etc/apt/sources.list

Does anyone know how I can install it? Google has been no help, and I'm very surprised that such an important package is available on Debian but not Ubuntu. :(

That package is not in the repositories. Perhaps it is under a different name.

---

### Post by Termina on 2008-07-12
[http://packages.ubuntu.com/search?keywords=libapache2-mod-bw](http://packages.ubuntu.com/search?keywords=libapache2-mod-bw)

I'm guessing this is yet another package that Ubuntu has no amd64 support for (in hardy at least). I guess I can install the intrepid version... :/

---

### Post by Kilz on 2008-07-12
> **Termina said:**
> [http://packages.ubuntu.com/search?keywords=libapache2-mod-bw](http://packages.ubuntu.com/search?keywords=libapache2-mod-bw)

I'm guessing this is yet another package that Ubuntu has no amd64 support for (in hardy at least). I guess I can install the intrepid version... :/

You might be able to install that package, have you tried?

---

### Post by nikgare on 2008-07-12
There are instructions for building and installing here:
[http://linuxadministration.us/2008/07/12/apache2-bandwidth-limiting-in-ubuntu-hardy-804/](http://linuxadministration.us/2008/07/12/apache2-bandwidth-limiting-in-ubuntu-hardy-804/)

---

