---
title: "skype and libqt"
date: 2006-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yumi on 2006-08-30
I downloaded and installed skype beta. It said the deb file is incompatible with the AMD64 architecture but --force all helped as described in hosto's. 

Starting Skype with skype& brings up the error libqt-mt.so.3 cannot open shared object file: No such file or directory.

Reading through postings it has been recommended to install libqt3c102-mt_3.3.4-3_i386.deb . But this file does not exist in the current repositories only back at Warty's.

libqt3-mt from Ubuntu packages is installed.

Another solution?

Michael

---

### Post by Kilz on 2006-08-30
> **Yumi said:**
> I downloaded and installed skype beta. It said the deb file is incompatible with the AMD64 architecture but --force all helped as described in hosto's. 

Starting Skype with skype& brings up the error libqt-mt.so.3 cannot open shared object file: No such file or directory.

Reading through postings it has been recommended to install libqt3c102-mt_3.3.4-3_i386.deb . But this file does not exist in the current repositories only back at Warty's.

libqt3-mt from Ubuntu packages is installed.

Another solution?

Michael

You will want to install this package
[http://packages.ubuntu.com/dapper/libs/ia32-libs-kde](http://packages.ubuntu.com/dapper/libs/ia32-libs-kde)

---

### Post by Yumi on 2006-08-30
Thanks, it is working now. But I do not understand why I need the KDE package being on GNU. Never mind. Thanks Kilz.

Michael

---

