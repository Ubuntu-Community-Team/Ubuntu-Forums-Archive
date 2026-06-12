---
title: "Intel 536 modem install"
date: 2005-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ckr on 2005-01-19
Hi,

Trying to install the driver for an intel 536 pci modem.  I downloaded the source from intel's website.  I have the kernel source and build-essential installed.  When following the directions I'm told to : make clean, make 536, make install.  This is the result.  Sorry for it being a bit lengthly.

root@ubuntu:/home/brian/intel-536EP-2.56.76.0 # make 536
   Module precompile check
   Current running kernel is: 2.6.8.1-3-amd64-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
cd coredrv && make 536core_26 && \
cp Intel536.ko .. && cd .. && \
strip --strip-debug Intel536.ko && \
exit; \
ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to buil d driver" && exit; \
if [  ]; then \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELA H -DTARGET_LINUX -DLINUX" 536core; \
else \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/bui ld/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
cp Intel536.o .. ; \
if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/v ersion.h;\
        fi
2.6.8.1-3-amd64-generic
make[1]: Entering directory `/home/brian/intel-536EP-2.56.76.0/coredrv'
make -C /lib/modules/2.6.8.1-3-amd64-generic/build SUBDIRS=/home/brian/intel-536 EP-2.56.76.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.8.1-3-amd64-generic'
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/coredrv.o
/home/brian/intel-536EP-2.56.76.0/coredrv/coredrv.c:756: warning: initialization  from incompatible pointer type
/home/brian/intel-536EP-2.56.76.0/coredrv/coredrv.c:757: warning: initialization  from incompatible pointer type
/home/brian/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function `dspdrv_CommRam ISR':
/home/brian/intel-536EP-2.56.76.0/coredrv/coredrv.c:879: warning: function decla ration isn't a prototype
/home/brian/intel-536EP-2.56.76.0/coredrv/coredrv.c: At top level:
/home/brian/intel-536EP-2.56.76.0/coredrv/coredrv.c:286: warning: `power_callbac k' defined but not used
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/clmmain.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/rts.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/task.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/uart.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/wwh_dflt.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/locks.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/softserial_io.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/softserial_ioctl.o
  CC [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/softserial.o
  LD [M]  /home/brian/intel-536EP-2.56.76.0/coredrv/Intel536.o
ld: Relocatable linking with relocations from format elf32-i386 (/home/brian/int el-536EP-2.56.76.0/coredrv/536core.lib) to format elf64-x86-64 (/home/brian/inte l-536EP-2.56.76.0/coredrv/Intel536.o) is not supported
make[3]: *** [/home/brian/intel-536EP-2.56.76.0/coredrv/Intel536.o] Error 1
make[2]: *** [_module_/home/brian/intel-536EP-2.56.76.0/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-amd64-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/brian/intel-536EP-2.56.76.0/coredrv'
2.6.8.1-3-amd64-generic
Failed to build driver

Can someone give me some advice on what may be going wrong?

Thanks, 

Brian.

---

### Post by az on 2005-01-20
"Relocatable linking with relocations from format elf32-i386 (/home/brian/int el-536EP-2.56.76.0/coredrv/536core.lib) to format elf64-x86-64 (/home/brian/inte l-536EP-2.56.76.0/coredrv/Intel536.o) is not supported"

edited:
"Relocatable linking with relocations from format elf32-i386  to format elf64-x86-64 is not supported"

edited more:
"64 is not supported"


Winmodems suck.  Do the sl-modem packages work on amd64?  They usually work for the Intel modem, at least on i386 (32 bit).

---

### Post by az on 2005-01-20
Actually, the alsa module intel8x10m is sometimes known to work for your modem.  I would not know if it compiles under amd64, if it does, you already have it.

Try installing the two sl-modem packages (daemon and source)  Do not compile the driver, since the daemon will try using the default alsa (One of the few GPL modem drivers around)  You need to read the docs and set your modem device in /etc/defaults (I think - -It's in the docs...)

If you can load the module and you are sure you got the right alsa device in your settings and you still can't dial, then try compiling the non-free sl-modem driver.  Good Luck!

---

