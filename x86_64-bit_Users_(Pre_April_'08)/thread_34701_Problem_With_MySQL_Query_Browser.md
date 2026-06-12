---
title: "Problem With MySQL Query Browser"
date: 2005-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by 76thParadox on 2005-05-16
I am trying to get mysql-query-browser to run correctly on an Ubuntu Linux distribution.  I am running the AMD64 (5.04) release of Ubuntu.  The Ubuntu/Debian package for the query browser did not work so I tried compiling the latest 1.1.7 version of the QB.  After resolving all required dependancies using the *.deb packages provided in the Ubuntu repositories I succesfully compiled the latest version of the QB.  However it is still giving me a segmentation fault whenever I try to connect to a database.  When I try to connect the query browser GUI disappears, the application crashes and gives the following output:

./mysql-query-browser: line 9:  9135 Segmentation fault      $MYPATH/mysql-query-browser-bin

Connecting to the same database from the query browser on a 32 bit installation of Ubuntu Linux works just fine.  Can anyone give me some advice as to how to get the QB working on 64bit Ubuntu Linux?

---

### Post by martijntje on 2005-11-06
I've got the same problem here. Running it from a chroot seems to work just fine though.

---

### Post by alkalined on 2006-06-02
sorry for the lame question, but.. what does running from chroot means? :-?

---

