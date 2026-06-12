---
title: "Dlan usb adapter"
date: 2008-06-16
forum: x86 64-bit Users
---

### Post by neurovillage on 2008-06-16
Hi all, I installed few months ago the dlan usb drivers in ubuntu Gutsi Gibbon and all worked. Today I have updated Ubuntu to Hardy Heron (8.04 LTS) and the device doesn't work. I tried to re-install the driver but when I made "make istall" he gives me error.I have archtecture x86_64.So I suppose that the problem is caused by the update. Anyone can help me?I'll post all the logs of the "make install" procedure.The kernels that not load  the driver are: 2.6.24-18 and 2.6.24-19. With 2.6.22-14 the driver were loaded properly.  

This is the code the terminal return when I make install:

root@sergio-ubuntu:/dlanprova# make install
make install in tool
make[1]: Entering directory `/dlanprova/tool'
mkdir -p /usr/local/sbin && \
	/usr/bin/install -c -m700  dlanconfig_son dlanconfig  /usr/local/sbin
mkdir -p /usr/local/man/man8 && \
	/usr/bin/install -c -m 644 dlanconfig.8.gz /usr/local/man/man8
make[1]: Leaving directory `/dlanprova/tool'
make install in driver
make[1]: Entering directory `/dlanprova/driver'
mkdir -p /lib/modules/2.6.24-18-generic/extra && /usr/bin/install -c -m 644 devolo_usb.ko /lib/modules/2.6.24-18-generic/extra
/sbin/depmod -a &&	/sbin/modprobe devolo_usb
FATAL: Error inserting devolo_usb (/lib/modules/2.6.24-18-generic/extra/devolo_usb.ko): Invalid module format
make[1]: *** [insdriver] Error 1
make[1]: Leaving directory `/dlanprova/driver'
make: *** [install] Error 2
root@sergio-ubuntu:/dlanprova# 

The code says modprobe cannot insert the module. Someone can help me??

---

