---
title: "[SOLVED] 8.10 - sources.list for 64-bit server"
date: 2008-12-28
forum: x86 64-bit Users
---

### Post by IQRules on 2008-12-28
I got some error here. What should I use in sources.list file?
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) intrepid-updates/multiverse Packages
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-secuirty/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-secuirty/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-secuirty/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-secuirty/restricted/binary-amd64/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Here is my copy,

root@ubuntuHP:/etc/apt# cat sou*list
deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-secuirty main restricted
deb [http://security.archive.ubuntu.com/ubuntu](http://security.archive.ubuntu.com/ubuntu) intrepid universe multiverse

deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-updates main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-updates universe multiverse

---

### Post by felker2 on 2008-12-28
> **IQRules said:**
> I got some error here. What should I use in sources.list file?
<snip>
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-secuirty main restricted


You edited by hand, didn't you? ;-)

There's a typo: it says "secuirty" where it should be "security". Correct that, and do a update.

HTH

---

### Post by IQRules on 2008-12-29
Good catch, thanks

---

