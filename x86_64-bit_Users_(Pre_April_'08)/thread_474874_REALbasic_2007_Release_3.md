---
title: "REALbasic 2007 Release 3"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by ecs_pf5 on 2007-06-15
Has anyone had success installing REALbasic 2007 Release 3 on Feisty 7.04 x64 on AMD64?

I just get the error

```

error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

```

When trying to run the installer from the extracted REALbasicLinux.tgz download. Elsewhere on the forum I read that it might be an issue caused by the 64-bittism, but I'm wholly unsure how to go about fixing it.

[http://www.realbasic.com/download/](http://www.realbasic.com/download/)

Or maybe I need to install something extra?

[http://www.realbasic.com/products/realbasic/requirements/](http://www.realbasic.com/products/realbasic/requirements/)

---

### Post by darknightuk on 2007-06-15
have u installed the cups dev?

---

### Post by ecs_pf5 on 2007-06-15
I *think* so.. well I'm basing that on the fact that the last thing I did was to get my printer working over the network using CUPS..

In synaptic I am showing green for:

cupsys
cupsys-bsd
cupsys-client
cupsys-common
cupsys-driver-gutenprint 

I am showing not installed for:

cupsys-driver-gimpprint
cupsys-pt
cups-pdf

there is nothing else cups-related showing at the mo

I'm changing my mind here. No I don't think what I did, did constitute installing cups dev.

so do I need to add a line to my sources.list or something?

[edit]

I *think* I've got it now - libcups.so.2 is present in /usr/lib - but still getting that same error

[edit]

ahh.. this is where I should be, sorry

[http://ubuntuforums.org/showthread.php?p=2850923#post2850923](http://ubuntuforums.org/showthread.php?p=2850923#post2850923)

---

