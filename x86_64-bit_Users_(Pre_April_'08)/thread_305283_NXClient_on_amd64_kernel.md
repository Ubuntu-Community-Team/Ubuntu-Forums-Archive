---
title: "NXClient on amd64 kernel"
date: 2006-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by jackocleebrown on 2006-11-23
Hello,

Just got NXClient working on edgy amd64, thought I would add it here - might be useful for someone.

Basically all I had to do was to force the i386 package to install. There was one unmet dependency "libstdc++2.10-glibc2.2" which I could not find for amd64 so again I forced an install of the 32bit version

1) download nxclient
[http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-9_i386.deb](http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-9_i386.deb)

2) dowmload edgy 32bit package of libstdc++2.10-glibc2.2
[http://packages.ubuntulinux.org/edgy/libs/libstdc++2.10-glibc2.2](http://packages.ubuntulinux.org/edgy/libs/libstdc++2.10-glibc2.2)


3) install libstdc++2.10-glibc2.2
"sudo dpkg -i --force-architecture libstdc++2.10-glibc2.2_2.95.4-24_i386.deb"

4) install nxclient
"sudo dpkg -i --force-architecture nxclient_2.1.0-9_i386.deb"

This did the job for me.

Thanks, Jack

---

### Post by exohuman on 2006-12-06
Thanks for the info! I have been searching for a way to get that working! Thanks! :-D

---

### Post by cow_racer on 2006-12-08
Thanks.  I got it working.

:)

---

