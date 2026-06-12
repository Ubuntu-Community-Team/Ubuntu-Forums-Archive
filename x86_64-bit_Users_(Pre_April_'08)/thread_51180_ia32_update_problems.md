---
title: "ia32 update problems"
date: 2005-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by DRF on 2005-07-22
Just run Ubuntu Update Manager and the new dpkg packages installed fine but the new ia32-libs comes up with the error:

Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_0.5ubuntu3.1_amd64.deb (--unpack):
 error creating symbolic link `./usr/lib32/libGL.so.1': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_0.5ubuntu3.1_amd64.deb

Is there any reason for this error and can I create the link manually etc? (don't know if anyone else has had this error. I think this package must have only been updated in the last couple of days, also not sure which repository it's located on. I have ubuntu main/security/updates and the backport server. ok I know AMD64 packages aren't on it atm but added it expecting them to start being added at some point and not got round to changing my apt sources)

There is no rush so if this is a common error which someone will fix in the next few days I'll happy wait rather than mess around.

Daniel

---

### Post by haloki on 2005-07-22
Available here:
[http://www.ubuntuforums.org/showthread.php?t=19551](http://www.ubuntuforums.org/showthread.php?t=19551)

---

