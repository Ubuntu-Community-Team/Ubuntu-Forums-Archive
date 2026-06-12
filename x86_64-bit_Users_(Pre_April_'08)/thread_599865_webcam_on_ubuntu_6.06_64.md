---
title: "webcam on ubuntu 6.06 64"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruiruas on 2007-11-01
Hi,
Im trying to install a Logitech Communicate STX webcam on my machine, but it&#347; not working...
I've install spca5xx, but it didn't work, so I went to the spca5xx website and found that my kernel (2.6.15-29-amd64-generic) should use "gspca" instead. I downloaded it and tried to install, but when trying to compile, the following error occurs:

make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20070508 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-29-amd64-generic'
  CC [M]  /usr/src/gspcav1-20070508/gspca_core.o
/usr/src/gspcav1-20070508/gspca_core.c:2559: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
make[2]: *** [/usr/src/gspcav1-20070508/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20070508] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-29-amd64-generic'
make: *** [default] Error 2

It  seems the driver is for the 32bit kernel... (...error:‘v4l_compat_ioctl32’ undeclared here...)
Can someone help? I wouldn't like to have to upgrade at this point!

Thanks,
Rui Ruas

---

### Post by ruiruas on 2007-11-05
HEI GUYS!
please help... please help...
Can anyone hear me?
:-D
Thanks.

---

### Post by ForAiur on 2007-12-29
Hi! 
Could you solve the problem? I have the same output here... :(

---

### Post by ForAiur on 2007-12-30
> **ruiruas said:**
> HEI GUYS!
please help... please help...
Can anyone hear me?
:-D
Thanks.

You have to take an older release from here:
[http://mxhaard.free.fr/spca50x/Download/oldrelease/](http://mxhaard.free.fr/spca50x/Download/oldrelease/)

It seems the new driver needs higher kernel then 2.6.15

---

### Post by ruiruas on 2008-01-13
Thanks. I've alrerady given up on it and upgraded to gutsy. Gutsy is great. It seems to recognize and properly setup almost anything you throw at it. Thanks anyway.

---

### Post by rambn on 2008-02-08
Sadly, Gutsy is not so keen with my video driver, so I am stuck with Dapper and my own webcam nightmare.

---

