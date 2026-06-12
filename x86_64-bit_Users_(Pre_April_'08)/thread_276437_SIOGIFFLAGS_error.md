---
title: "SIOGIFFLAGS error"
date: 2006-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bardia on 2006-10-12
Hi all,  

I'm running the latest version of AMD64 Dapper, and my network icon gives this error:

SIOGIFFLAGS error: No Such Device

Interestingly, both Ethernet and WLAN work reasonably well, but the error still bugs me.  I did a bit of snooping, but it appears that usually this issue means one is unable to connect, so I'm a bit hesitent, still pretty new to Linux.

I also believe this is an AMD64 issue, as I did not get this error when running the 32 bit version of Dapper.

I do not have ndiswrapper installed as it appears my drivers are working correctly.

Any advice?

---

### Post by John.Michael.Kane on 2006-10-12
Here [https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=SIOCGIFFLAGS&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=SIOCGIFFLAGS&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=) post a bug report on it.

AS a fix you can right click the icon select properties and type eth0

---

### Post by Bardia on 2006-10-13
Ha... thanks a ton man.  That fixed it.

---

