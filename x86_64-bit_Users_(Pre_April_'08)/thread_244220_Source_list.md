---
title: "Source list"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Matrixy on 2006-08-26
Hi,
Can any 1 post a full sources.list with the repositories that are good for amd 64 bit version?
i got mine a bit not working....

---

### Post by xopher on 2006-08-26
Hmm, Here's my sources.list, hope it helps:



```


# Ubuntu supported packages (packages)
deb http://fi.archive.ubuntu.com/ubuntu dapper-updates main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources)
# deb-src http://fi.archive.ubuntu.com/ubuntu dapper main restricted
# deb-src http://fi.archive.ubuntu.com/ubuntu dapper-updates main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages)
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb http://fi.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources)
# deb-src http://fi.archive.ubuntu.com/ubuntu dapper universe multiverse
# deb-src http://fi.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# XGL and Compiz
deb http://ubuntu.compiz.net dapper main
# deb-src http://ubuntu.compiz.net dapper main
# deb http://raof.dyndns.org/falcon/ dapper all
deb http://ubuntu.moshen.de/ dapper all

# Ubuntu backports project (packages)
deb http://fi.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Ubuntu backports project (sources)
# deb-src http://fi.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# BMPx Source
deb-src http://files.beep-media-player.org/packages/ubuntu dapper testing #main universe

# Janvitus
deb http://janvitus.interfree.it/ ./

```

---

### Post by Matrixy on 2006-08-26
should i put il for israel?
or can i use for instance usa or uk

---

