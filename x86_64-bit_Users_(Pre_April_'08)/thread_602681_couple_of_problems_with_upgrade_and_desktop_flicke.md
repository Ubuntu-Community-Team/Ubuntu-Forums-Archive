---
title: "couple of problems with upgrade and desktop flicker"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by elj4176 on 2007-11-04
I have an HPdv9074cl laptop and am running Feisty 64 bit. When trying tp upgrade to Gutsy I get this message:

Failed to fetch [http://ftp.us.debian.org/debian/dists/feisty/main/binary-amd64/Packages.gz](http://ftp.us.debian.org/debian/dists/feisty/main/binary-amd64/Packages.gz) 404 Not Found [IP: 204.152.191.7 80]
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ftp.us.debian.org/debian/dists/feisty/non-free/binary-amd64/Packages.gz](http://ftp.us.debian.org/debian/dists/feisty/non-free/binary-amd64/Packages.gz) 404 Not Found [IP: 204.152.191.7 80]
Failed to fetch [http://ftp.us.debian.org/debian/dists/feisty/contrib/binary-amd64/Packages.gz](http://ftp.us.debian.org/debian/dists/feisty/contrib/binary-amd64/Packages.gz) 404 Not Found [IP: 204.152.191.7 80]

and the update fails. I do not have any of those in my /etc/apt/sources.list either.

My other problem is that I have then nvidia go7600 and it has been working fine with beryl. All the cool effects and whatnot. Recently my desktop will flicker/flash every once in awhile. It's almost like the desktop just does a refresh or something. It's not a constant flicker/flash and it is very inconsistent as to the timing of it.
This is the reason I tried to upgrade in the first place. It is a very annoying problem. I can try turning off beryl/emerald and see if that fixes it but I want the  eye candy ;)

Any ideas on either of  these problems?

---

### Post by elj4176 on 2007-11-04
nevermind. I just disabled those in the sources and the update worked. No screen flicker as of yet either. 

Wireless still works but it seems a lot slower than it was before/

---

