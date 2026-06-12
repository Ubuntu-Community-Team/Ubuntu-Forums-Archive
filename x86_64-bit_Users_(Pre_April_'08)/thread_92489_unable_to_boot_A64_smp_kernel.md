---
title: "unable to boot A64 smp kernel"
date: 2005-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by krull on 2005-11-19
Hi,

Just installed Kubuntu and upgraded to the 

kernel-image-2.6.11-9-amd64-k8-smp 

kernel package. When booting this package from grub the system hangs with the following error messages:

First I receive messages that 
/lib/modules/2.6.11-9-amd64-k8-smp/kernel/drivers/video/console/tilebilt.ko
and same prefix, /video/softcursor.ko can not be read (no such file/directory)

then I receive the message:
alert /dev/sdb1 does not exist, dropping to a shell

At this point the system simply stops booting and hangs.

Hardware info:
A64 4800 X2
DFI lanparty NF4-Ultra D
2 sata hard drives. Drive 1 contains grub and windows xp pro, drive 2 contains the kubuntu install. /dev/sdb1 should refer to drive 2.

Note that the non-smp A64 kernel boots just fine.

Any help/suggestions would be greatly appreciated!

Thanks,

   -Sam

---

### Post by krull on 2005-11-19
Nevermind, had installed universe packages... Switched to SMP packages on Kubuntu install DVD and everything works fine...

   -Sam

---

