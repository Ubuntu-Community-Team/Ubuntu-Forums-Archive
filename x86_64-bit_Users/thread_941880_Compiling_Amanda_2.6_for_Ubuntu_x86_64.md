---
title: "Compiling Amanda 2.6 for Ubuntu x86_64"
date: 2008-10-08
forum: x86 64-bit Users
---

### Post by burnbrighter on 2008-10-08
Just a hint for anyone trying to compile Amanda x86_64.  I've compiled and installed Amanda 2.6 with the following configuration options:

./configure --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu --program-prefix= --prefix=/usr --exec-prefix=/usr --bindir=/usr/bin --sbindir=/usr/sbin --sysconfdir=/etc --datadir=/usr/share --includedir=/usr/include --libdir=/usr/lib64 --libexecdir=/usr/lib64/amanda --localstatedir=/var/lib --sharedstatedir=/usr/com --mandir=/usr/share/man --infodir=/usr/share/info --enable-shared --disable-static --disable-dependency-tracking --with-index-server=amandahost --with-tape-server=amandahost --with-config=DailySet1 --with-gnutar-listdir=/var/lib/amanda/gnutar-lists --with-smbclient=/usr/bin/smbclient --with-dumperdir=/usr/lib64/amanda/dumperdir --with-amandahosts --with-user=amanda --with-group=disk --with-tmpdir=/var/log/amanda --with-gnutar=/bin/tar --with-ssh-security --with-bsdtcp-security --with-bsdudp-security

---

