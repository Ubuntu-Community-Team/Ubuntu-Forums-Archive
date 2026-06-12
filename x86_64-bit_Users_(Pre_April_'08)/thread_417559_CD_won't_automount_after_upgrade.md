---
title: "CD won't automount after upgrade"
date: 2007-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by TonyMontana on 2007-04-21
I have an AMD Athlon64 X2 that I just upgraded to Feisty using the update manager.  Since I've done this CD's are no longer mounted automatically, although I can still mount them manually via the command line.  However, USB disks are still mounted automatically.  This isn't a huge deal, but it would be nice to get it working if anyone has any clues... TIA

---

### Post by cap_gemo on 2007-07-08
It isn't the problem of x64-arch. It's some bug in hal. I have the same issue on my x86-system after a clean install of Ubuntu fesity. CDs won't mount automatically, but USB-Sticks do.

  I found a description of this bug here: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95868](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95868) . I tried to follow the instructions, but it didn't work. The package won't be build with that patch.

  Does anybody have a corresponding for hal 0.5.9-1, which is the current version in Ubuntu feisty? Or is there some other solution to this problem?

---

