---
title: "Where the heck is libsasl2-modules-gssapi-heimdal?"
date: 2006-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bitch-Face Jones on 2006-01-27
Hi,

I'm trying to install the Cyrus SASL GSSAPI authentication modules.  When I try to do this I get the following error:

root@tomo:~# apt-get install libsasl2-modules-gssapi-heimdal
Reading package lists... Done
Building dependency tree... Done
Package libsasl2-modules-gssapi-heimdal is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsasl2-modules-gssapi-heimdal has no installation candidate

This seems to be the case with the MIT version of the SASL GSSAPI library as well.  Anyone know what the hitch in the getalong here is?  I really need GSSAPI support in SASL to be able to authenticate to most important services on my network.

---

### Post by Bitch-Face Jones on 2006-01-27
Never mind, I've figured it out.  Apperently these packages are contained in the unspported "Universe" repository.

---

