---
title: "Error installing libc6-i386"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by Braedley on 2008-09-18
So my libc6 package was updated to version 2.7-10ubuntu4, which is fine and dandy, but the current version of libc6-i386 is 2.7-10ubuntu3, and that package depends on libc6 being the same version.  The new version of libc6-i386 is available in the proposed repository, but when I try to install it, I get this error:
```
E: /var/cache/apt/archives/libc6-i386_2.7-10ubuntu4_amd64.deb: corrupted filesystem tarfile - corrupted package archive
```
Is there any way to get this working again?  I don't want to just uninstall libc6 and install libc6-i386 and force libc6 to version 2.7-10ubuntu3 because there are a number of other packages that depend on libc6.

Thanks in advance
Braedley

PS: Using Hardy

---

### Post by pro003 on 2008-09-18
go to SYNAPTIC and search for libc6 and reinstall it! Or completely remove then install again..

and don't forget to do some common things
```

sudo apt-get update
sudo apt-get install -f
```

---

### Post by Braedley on 2008-09-18
Okay, everything is good now.  I had forgotten to mention that gcc and cpp were also updated when libc6 was updated, and that is where the dependency tree fell apart.  Manually downloading and reinstalling the various packages that became broken kept synaptic for trying to unistall my entire system.

---

### Post by pro003 on 2008-09-18
nice! there you go.

---

