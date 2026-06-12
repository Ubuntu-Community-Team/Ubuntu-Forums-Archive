---
title: "Samba 3.0.2 or higher?"
date: 2006-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by mjrmurray on 2006-03-21
I am trying to upgrade samba to at least 3.0.21c to fix some compatibility issues with tiger file sharring.  I can not figure out how to do it though.  Doing an apt-get update gives me the same version 3.0.16a even if i add all the repositories and the only samba .deb files i can find are for i386.  Can someone please tell me (I am extremely new to linux) how to upgrade samba?  Thank you.  P.S. if you say compile from source, i have no idea what that means or how to do it.  I would preferably like a .deb file, or some other "newbie" way of doing it.  Can anyone help?

Thanks.

---

### Post by mjrmurray on 2006-03-22
Please Help!

---

### Post by ssam on 2006-03-22
ubuntu has a policy of not adding any new features or new versions to a release.this means that synaptic will only provide security and serious bug fixes to the software you have installed.

to get new versions you either have to wait until the next ubuntu release, use backports, or go it alone and find/make your own package.

the next release ubuntu 6-06 (dapper) is in the last stages of testing. some people are already using it. it will be considered pretty much ready for day to day use by about mid april, and fully ready and polished by the start of june. the version of samba in dapper is 3.0.21b-1ubuntu2 (which is a few bug fixes above 3.0.21b).

backports is a projects to repackage some of the software from the next release of ubuntu into the current one. they have a subforum on this site, you could find out there is they have backported samba.

the going it alone options will probably require building from source, unless you can find a powerpc .deb somewhere. there is a basic intro to building from source at [https://wiki.ubuntu.com/forum/software/OpenSource/SourceCode](https://wiki.ubuntu.com/forum/software/OpenSource/SourceCode)

---

### Post by mjrmurray on 2006-03-22
Thanks ssam! that really helped me. :)

---

### Post by ssam on 2006-03-23
just to let you know samba 3.0.21c-1ubuntu1 went into dapper today.

---

