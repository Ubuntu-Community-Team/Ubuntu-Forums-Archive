---
title: "I wana test software"
date: 2006-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sqwishy on 2006-11-14
I'm switching to ubuntu (edjy) kuz I keep breaking gentoo, but I wana be able to install and test packages that havn't been tested on amd64, because (on gentoo at least) otherwise i'm restricted to only using a small number of programs. Does anyone know what i'm trying to say lol

---

### Post by incubus on 2006-11-14
Can you give us a concrete example?  : )

---

### Post by kuja on 2006-11-14
Which software do you want to test? If you're that interested in testing experimental software, then get the source from cvs/svn and try it... nothing there to stop you.

---

### Post by RAOF on 2006-11-14
Almost everything available from the Ubuntu repositories is available for **all** supported architectures.  From memory, about 2% of the (~20,000) IA32 packages are not available for x86-64, and most of those are tremendously obscure.  The notable exception being, of course, wine.

If you really want to test stuff, the Feisty repositories are open :)

---

### Post by kuja on 2006-11-14
Pre-Beta Ubuntu ... ewwwww. Even Debian Sid's less prone to breakage than that.

---

### Post by RAOF on 2006-11-14
(currently) Works For Me(tm) :)

---

### Post by Sqwishy on 2006-11-14
right well when i look for glest and there are linux ports and stuff
[http://www.stud.uni-karlsruhe.de/~uxsm/glest/](http://www.stud.uni-karlsruhe.de/~uxsm/glest/)
and i read somewhere that therses a port for ubuntu or debian or something but its unstable in amd64 and its not in the main repo's but i didn't know much about anything at the time and didn't think to look for a link or anything to repo's thatbe would lemme get the 'beta'. So i'm wondering if anyone knows of any repos were i can get access to unstable software stuffs.

---

### Post by d3v1ant_0n3 on 2006-11-14
> **RAOF said:**
> (currently) Works For Me(tm) :)

Same here! Only 1 bit of breakage so far!

---

### Post by RAOF on 2006-11-15
> **Sqwishy said:**
> right well when i look for glest and there are linux ports and stuff
[http://www.stud.uni-karlsruhe.de/~uxsm/glest/](http://www.stud.uni-karlsruhe.de/~uxsm/glest/)
and i read somewhere that therses a port for ubuntu or debian or something but its unstable in amd64 and its not in the main repo's but i didn't know much about anything at the time and didn't think to look for a link or anything to repo's thatbe would lemme get the 'beta'. So i'm wondering if anyone knows of any repos were i can get access to unstable software stuffs.

Generally stuff like that won't be in a repository, and almost certainly won't be in a centralised repository.  If they make debian packages, awesome.  You can just download them and install them (using Gdebi, or dpkg from the CLI).  A debian package may not work on Ubuntu, some of the packages are named differently/have different versions.

---

### Post by kuja on 2006-11-15
> **RAOF said:**
> Generally stuff like that won't be in a repository, and almost certainly won't be in a centralised repository.  If they make debian packages, awesome.  You can just download them and install them (using Gdebi, or dpkg from the CLI).  A debian package may not work on Ubuntu, some of the packages are named differently/have different versions.
Or worse yet, come with a mess of library dependencies, well, newer versions of the libraries anyhow.

---

### Post by Sqwishy on 2006-11-15
> **kuja said:**
> Or worse yet, come with a mess of library dependencies, well, newer versions of the libraries anyhow. yeah kuz when i try to install it from the deb package it's missing a bunch of library's that i don't wana spend 2 hours looking for elsewhere :neutral:

---

### Post by RAOF on 2006-11-15
> **Sqwishy said:**
> yeah kuz when i try to install it from the deb package it's missing a bunch of library's that i don't wana spend 2 hours looking for elsewhere :neutral:

You should be able to get many/most of those by running ```
sudo apt-get -f install
```
That will try to download all the missing dependencies of any packages you've manually installed.

---

### Post by kuja on 2006-11-15
True enough, but what I was thinking was along the lines of lets say new version of package a, lets say version 1.0, depends on package b version 1.0.
Now lets say you want to upgrade package a to version 1.1, but this also requires that you have version 1.1 of package b as well, but only version 1.0 is in the repos.

I'm not sure if this is what Sqwishy meant or not though.

---

