---
title: "Realtek 8168 Network on ubuntu 6.10 (abit ab9 pro)"
date: 2007-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by rsmith on 2007-04-04
Hi,

Network controller is not natively supported out of the box. 

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)

followed a guide here > [http://halisway.blogspot.com/2006/10/running-ubuntu-610-on-abit-ab9.html](http://halisway.blogspot.com/2006/10/running-ubuntu-610-on-abit-ab9.html) however i get the following:

```
root@hades:~/r1000_v1.05# make clean modules
make -C src/ clean
make[1]: Entering directory `/root/r1000_v1.05/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions
make[1]: Leaving directory `/root/r1000_v1.05/src'
make -C src/ modules
make[1]: Entering directory `/root/r1000_v1.05/src'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/root/r1000_v1.05/src modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.17-11-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/r1000_v1.05/src'
make: *** [modules] Error 2

```

i checked another 6.10 box and it did not have the build dir on it, so i created it manually, retried and got this:

```
root@hades:~/r1000_v1.05# make clean modules
make -C src/ clean
make[1]: Entering directory `/root/r1000_v1.05/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions
make[1]: Leaving directory `/root/r1000_v1.05/src'
make -C src/ modules
make[1]: Entering directory `/root/r1000_v1.05/src'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/root/r1000_v1.05/src modules
make[2]: Entering directory `/lib/modules/2.6.17-11-generic/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.17-11-generic/build'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/r1000_v1.05/src'
make: *** [modules] Error 2

```

other than the above link i cannot find any info on how you are supposed to install drivers..anyone able to please help?

---

### Post by StandardBlueCaboose on 2007-04-04
Have you tried Feisty? It seems to me like you just recently installed Ubuntu on this machine, so trying Feisty couldn't hurt.

I heard that there have been significant improvements on wireless cards and the like.

---

### Post by rsmith on 2007-04-04
yep, all-generic-ide and irqpoll being forced when booting from doesnt help on feisty, as it detects the network controllers, but not the Jmicron controller on this board.

---

