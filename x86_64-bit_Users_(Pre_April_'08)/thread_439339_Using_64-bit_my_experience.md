---
title: "Using 64-bit: my experience"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by simbahome on 2007-05-10
Hi,

I got my new AMD about a year ago, and went straight for 64-bit Ubuntu. As a newbie I had no idea what I was letting myself in for, but overall I have enjoyed the experience and learnt a lot. Out of the box  I got everything to work except for the TV card, the Printserver and the NDAS network drive. 

The TV card is working now, thanks to the upgrade to 7.04. :) 

The Printserver isnt working, but it also doesnt work for my windows machine, so I guess it is some other (maybe hardware) problem. 

The NDAS network drive only seems to be supported on the 32 bit version. At least that is the error message when I try and follow the directions on here :[http://code.ximeta.com/trac-ndas/wiki/Ubuntu7.04]("http://code.ximeta.com/trac-ndas/wiki/Ubuntu7.04")

Has anyone got this to work on the 64 bit version? 


Thanks

---

### Post by Cappy on 2007-05-10
For any i386 package you'll have to force the install.

```

sudo dpkg -i --force-architecture packagename_i386.deb

```

make sure you have universe enabled so you can install these packages:
```

sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk

```

---

### Post by Kilz on 2007-05-10
> **Cappy said:**
> For any i386 package you'll have to force the install.

```

sudo dpkg -i --force-architecture packagename_i386.deb

```

make sure you have universe enabled so you can install these packages:
```

sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk

```

Just as a word of caution. Forcing in applications is not bad. But I would never under any circumstances force in a library.

---

### Post by Cappy on 2007-05-10
Build from tarball

"Don't install above driver if the driver is not for the version of your kernel. Build the custom driver with this instruction"

[http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)

You might have to do that instead.

---

### Post by Snargledorf on 2007-05-11
i just recently received my Ubuntu feisty 64bit cd and installed it right away. So far I am very pleased with my system. Beryl installed no problem and the only real issue Ive had is with Firefox not having flash support (fixed by switching to 32 bit Firefox)

---

### Post by simbahome on 2007-05-11
Thanks for the help. Unfortunately I have hit some snags:

First I tried to build it from the tarball. Unfortunately it didnt work. I have no idea what I am doing wrong. If I follow  the instructions here [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB]("http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB")
I get the following error.

 > rpmbuild -tb ndas-1.0.5-16.x86_64.tar.gz
error: Name field must be present in package: (main package)
error: Version field must be present in package: (main package)
error: Release field must be present in package: (main package)
error: Summary field must be present in package: (main package)
error: Group field must be present in package: (main package)
error: License field must be present in package: (main package)

I then tried the force of the packages from here [http://code.ximeta.com/trac-ndas/wiki/Ubuntu7.04]("http://code.ximeta.com/trac-ndas/wiki/Ubuntu7.04")

It seems that the first file (which I think is the driver) seemed to work:
 > sudo dpkg -i --force-architecture ndas-kernel_1.0.4-2.6.20_15_generic.38_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 153819 files and directories currently installed.)
Preparing to replace ndas-kernel 1.0.4-2.6.17_10_generic.12 (using ndas-kernel_1.0.4-2.6.20_15_generic.38_i386.deb) ...
Unpacking replacement ndas-kernel ...
Setting up ndas-kernel (1.0.4-2.6.20_15_generic.38) ...

but the second file (which is the admin utility I think) gives errors:
 > sudo dpkg -i --force-architecture ndas-admin_1.0.4-38_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 153819 files and directories currently installed.)
Preparing to replace ndas-admin 1.0.4-12 (using ndas-admin_1.0.4-38_i386.deb) ...
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: error processing ndas-admin_1.0.4-38_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
 System startup links for /etc/init.d/ndas already exist.
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ndas-admin_1.0.4-38_i386.deb


Any Ideas would be greatly appreciated. Thanks :confused:

---

### Post by Cappy on 2007-05-11
I'm not sure, but maybe it should be:
```

rpmbuild -tb ndas-1.0.3-101.tar.gz --nodeps --target=amd64

```

---

