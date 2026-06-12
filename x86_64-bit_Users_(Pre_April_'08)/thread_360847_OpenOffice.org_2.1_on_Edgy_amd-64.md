---
title: "OpenOffice.org 2.1 on Edgy amd-64"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-02-13
Can it be done?

---

### Post by John Jason Jordan on 2007-02-14
> **John Jason Jordan said:**
> Can it be done?
Yep, it can! I found it here:

[http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/20061213/?C=S;O=A](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/20061213/?C=S;O=A)

For further details, go here:

[http://ubuntuforums.org/showthread.php?t=316934&page=2](http://ubuntuforums.org/showthread.php?t=316934&page=2)

I found that aptitude refused to recognized the .deb files as packages, but dpkg worked. It is now running just fine on my Edgy amd64 laptop.

Unfortunately, it did not resolve my problem with drag and drop text not working. But at least since it worked in 2.02 under Dapper, broke after upgrading to Edgy and 2.04, and remains broken after a fresh install of 2.1, then now I know the problem is in Edgy, not OOo.

---

### Post by penvzila on 2007-02-21
Bingo! This fixes my problem of importing 2.1 files into the 2.0 edgy has.  It was screwing up Math objects big time.

---

