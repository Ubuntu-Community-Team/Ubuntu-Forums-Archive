---
title: "libofx2 package broken?"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by dchart on 2005-10-14
When I try to install libofx2, I get the following error message:

E: /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_powerpc.deb: trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102

Is this a problem in the deb? Deleting that file before trying the install makes no difference.

(libofx2 is one of gnucash's dependencies, incidentally.)

---

### Post by ssam on 2005-10-14
head over to [https://launchpad.net/](https://launchpad.net/) and file a bug.

---

### Post by geofff on 2005-10-14
[QUOTE=ssam]head over to [https://launchpad.net/](https://launchpad.net/) and file a bug.[/QUOTE]
I've also had this problem and having noted that the bugzilla bug filed by rsay on forum thread 72486 has been closed as it relates to universe repo I have filed a bug with Launchpad. ref [https://launchpad.net/distros/ubuntu/+sources/gnucash/+bug/3145](https://launchpad.net/distros/ubuntu/+sources/gnucash/+bug/3145). 
Geofff

---

