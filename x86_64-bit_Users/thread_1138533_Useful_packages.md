---
title: "Useful packages"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by utnr6 on 2009-04-26
Could anyone tell me some helpful packages and libraries for 64bit or ones that help with 32 bit.

also, my apt.conf.d has libc6-i686 blacklisted for no updates.  should i remove this entry or does it not work with 64bit?

---

### Post by stanca on 2009-04-26
Install getlibs.
Sudo dpkg -i --force-all "package_name".deb
getlibs /usr/bin/name

---

