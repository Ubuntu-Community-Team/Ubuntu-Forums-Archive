---
title: "compilation"
date: 2007-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Predrag on 2007-08-12
hi i have a problem.when i wanted to compile Zlib.it is a library i have start 1./configure 2.make 3.sudo aptitute install checkinstall 4 sudo checkinstall. In fourth step is a problem i have a 64bit system but PC make for me i386 package look:
/usr/bin/checkinstall: line 1151: dpkg-architecture: príkaz nenájdený

This package will be built according to these values: 

0 -  Maintainer: [ root@Schumacher ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ zlib ]
3 -  Version: [ 1.2.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ zlib-1.2.3 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]


and

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do u understand it?can u help me?

---

### Post by tszanon on 2007-09-06
> **Predrag said:**
> This package will be built according to these values: 

0 -  Maintainer: [ root@Schumacher ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ zlib ]
3 -  Version: [ 1.2.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ zlib-1.2.3 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
I was wandering in the unanswered posts and I found yours. :)
It seems that, somehow, checkinstall wants to build a i386 package instead of x86_64 or amd64. When checkinstall is running, it gives you the option to alter those settings you listed. You have to change the architecture to amd64 for the package to work in Ubuntu 64bits.

---

### Post by Kilz on 2007-09-06
> **Predrag said:**
> hi i have a problem.when i wanted to compile Zlib.it is a library i have start 1./configure 2.make 3.sudo aptitute install checkinstall 4 sudo checkinstall. In fourth step is a problem i have a 64bit system but PC make for me i386 package look:
/usr/bin/checkinstall: line 1151: dpkg-architecture: príkaz nenájdený



The question is, why are you compiling zlib? A search of the repos brings up [this package ]("http://packages.ubuntu.com/feisty/libs/zlib1g")already compiled.

---

### Post by tszanon on 2007-09-06
> **Kilz said:**
> The question is, why are you compiling zlib? A search of the repos brings up [this package ]("http://packages.ubuntu.com/feisty/libs/zlib1g")already compiled.
Maybe I misunderstood the OP. I understood that s/he was writing a library called zlib, and wanted to create a package of it, not knowing that there already is a library called zlib.

---

### Post by Predrag on 2007-09-07
thank u, i have download it from repositeries

---

### Post by Kilz on 2007-09-07
> **tszanon said:**
> Maybe I misunderstood the OP. I understood that s/he was writing a library called zlib, and wanted to create a package of it, not knowing that there already is a library called zlib.

It happens, and you gave some good info. But I have seen to many people trying to compile stuff because they couldnt find it. So when I see compiling questions I go and look to see if there is a package already.  :D

---

