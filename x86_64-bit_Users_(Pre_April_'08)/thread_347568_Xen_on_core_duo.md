---
title: "Xen on core duo"
date: 2007-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by uphill on 2007-01-27
Hi,
I try currently to install Xen 3. But the 2.6.17 image from the Repository won't work for me.([see here](https://launchpad.net/ubuntu/+source/xen-source-2.6.17/+bug/71552)).  Then I used the 2.6.16 image, But there is no restricted-modules(need nvidiaand r1000) for it. And i installed xen-headers-2.6.16 for compiling the modules by myself... Won't work... The r1000 has more importance for me than the nvidia one.

```

Script started on Sa 27 Jan 2007 19:14:48 CET
root@julian-desktop:/usr/src/r1000_v1.05# make clean
#make -C src/ clean
make[1]: Betrete Verzeichnis '/usr/src/r1000_v1.05/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions
make[1]: Verlasse Verzeichnis '/usr/src/r1000_v1.05/src'
root@julian-desktop:/usr/src/r1000_v1.05# make modules
make -C src/ modules
make[1]: Betrete Verzeichnis '/usr/src/r1000_v1.05/src'
make -C /lib/modules/2.6.16-11.2-generic/build SUBDIRS=/usr/src/r1000_v1.05/src modules
make: Betrete ein unbekanntes Verzeichnis
make: *** /lib/modules/2.6.16-11.2-generic/build: No such file or directory.  Schluss.
make: Verlasse ein unbekanntes Verzeichnis
make[1]: *** [modules] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/r1000_v1.05/src'
make: *** [modules] Fehler 2
root@julian-desktop:/usr/src/r1000_v1.05#
Script done on Sa 27 Jan 2007 19:15:08 CET

```

tank you for helping
Uphill

---

### Post by uphill on 2007-01-29
Now i compiled my own kernel with [this]("http://www.backenhoernchen.de/dokuwiki/doku.php?id=computer:howtos:xen_howto")
tutorial using oldconfig as kernelconfig...

it is working now but... my network(r1000) is sooooooooooooooo slow...

any ideas?

---

