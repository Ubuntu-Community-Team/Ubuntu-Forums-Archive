---
title: "Latest ATI Driver"
date: 2007-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwacky on 2007-10-10
I'm trying to install the latest driver from ATI with the Gusty AMD64 setup, it is telling me the package Ubuntu/gusty does not exist.  Is this just a typo on my part?  The directory I need gets create then erased.


```
mwacker@Milhouse:~/ATI$ sudo bash ./ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/gusty
[sudo] password for mwacker:
Created directory fglrx-install.uN5823
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gusty
Requested package is not supported.
Removing temporary directory: fglrx-install.uN5823
```

---

### Post by jocko on 2007-10-11
Yep. That's true. It can't build any package for anything called "gusty" (but it will build fine for gutsy). Check your spelling.

---

### Post by mwacky on 2007-10-15
Thanks!

---

