---
title: "Alien won't install rpm"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by smkururu on 2009-05-18
Hi, I was just installed alien to install rpm files on Ubuntu but it fails. Here's the output:
```
evans@evans-pc:~/Desktop$ sudo alien -d lilo-22.8-40.3.x86_64.rpm 
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
warning: lilo-22.8-40.3.x86_64.rpm: Header V3 RSA/SHA256 signature: NOKEY, key ID 3dbdc284
Unpacking of 'lilo-22.8-40.3.x86_64.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 155.
evans@evans-pc:~/Desktop$
```
Entering the command without -d also give the same message. Is there any workaround about this? Thanks;)

---

### Post by logos34 on 2009-05-18
Is there any reason you're not using the lilo .deb pkg in the ubunt repos?

> lilo_22.8-3.1ubuntu1_amd64.deb

---

