---
title: "Airport (original) monitor mode"
date: 2005-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by jgriffin on 2005-12-25
Hi,

I've been trying to get my original airport card to work with the orinoco drivers off CVS to make monitor mode work, but am encountering a couple problems.  When I try to simply run "make", I get the following result:

jgriffin@dakin140-198:~/orinoco$ make
Makefile:8: *** Kernel tree not found - please set KERNEL_PATH.  Stop.
jgriffin@dakin140-198:~/orinoco$ 

If I try to specify a kernel path (ie /usr/src), I get this:

jgriffin@dakin140-198:~/orinoco$ make KERNEL_PATH=/usr/src
sed: can't read /usr/src/include/linux/version.h: No such file or directory
make -C /usr/src M=/home/jgriffin/orinoco KERNELRELEASE= modules
make[1]: Entering directory `/usr/src'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/usr/src'
make: *** [modules] Error 2
jgriffin@dakin140-198:~/orinoco$ 

Any ideas?

---

### Post by gruepig on 2005-12-25
Try installing the kernel headers: 'apt-get install linux-headers-`uname -r`'.

---

### Post by jgriffin on 2005-12-26
Did the trick, thanks!

---

