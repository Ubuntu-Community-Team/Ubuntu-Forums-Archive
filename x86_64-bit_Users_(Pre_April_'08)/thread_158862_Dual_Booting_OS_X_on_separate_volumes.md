---
title: "Dual Booting OS X on separate volumes"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by godard on 2006-04-11
I more or less chickened out on playing around partitioning my HD (which is getting full anyway) and decided to install Ubuntu on a separate HD i had lying around. After much ](*,) with different master/slave/select options, i finally managed to get the yaboot loader to come up properly without a. screen resolution changes, b. grey screens, c. black screens d. no volumes being present etc. - the trick seemed to be OS X as master and the Ubuntu drive as slave or select - make sure the black end of the IDE cable is in the master drive people :rolleyes: .

Anyway, now that i have that sorted out, i'm having trouble getting Ubuntu to load. After selecting the Ubuntu drive it drops into the load process quickly flipping from the options screen (c for cd, l for linux etc) into another screen informing me of the following:

Please wait, loading kernel

/pci@f2000000/mac-io@17/ata-4@3f000/disk@1:3,/boot/vmlinux:input/output error

It then drops into the 'boot:' line.

Any idea what is happening and how to overcome this? As an aside, without the OS X volume being present, Ubuntu seems to boot and load fine.

---

### Post by godard on 2006-04-19
The hard drive that paricular install was on died within 24 hours :( i've installed on an old HD and everything is now working fine!

---

