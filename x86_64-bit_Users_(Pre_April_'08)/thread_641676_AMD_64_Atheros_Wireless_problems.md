---
title: "AMD 64 Atheros Wireless problems"
date: 2007-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fritzwr on 2007-12-15
I am using a Toshiba Satellite Pro A210 Laptop with an Atheros® Wireless LAN (802.11b/g) card and I am running Gutsy amd64 x-86 however i can not seem to make the Wireless card work. I tried to use ndiswrapper via this tutorial [http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros+feisty+ndiswrapper](http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros+feisty+ndiswrapper) but I got the following error:

"fritz@Fritz2:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/fritz/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/fritz/ndiswrapper-1.5/driver \
DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
LD /home/fritz/ndiswrapper-1.5/driver/built-in.o
CC [M] /home/fritz/ndiswrapper-1.5/driver/hal.o
CC [M] /home/fritz/ndiswrapper-1.5/driver/iw_ndis.o
CC [M] /home/fritz/ndiswrapper-1.5/driver/loader.o
/home/fritz/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/fritz/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/fritz/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/fritz/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/fritz/ndiswrapper-1.5/driver'
make: *** [all] Error 2"

Also I can see the Atheros HAl on my restricted drivers list but when i enable it it says that it is not in use (even after reboot). I am a bit new to linux and would greatly appreciate any help, thank you in advance.

---

### Post by piju on 2008-02-12
im having this problem too,
on acer aspire 5050
can anybody help ?

---

### Post by piju on 2008-02-12
i think i have successfully configured my atheros.
i will try to connect to any AP later..
will post the result here

---

