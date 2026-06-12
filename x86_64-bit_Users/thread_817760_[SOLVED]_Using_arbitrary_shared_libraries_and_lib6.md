---
title: "[SOLVED] Using arbitrary shared libraries and /lib64 symbolic link issues?"
date: 2008-06-03
forum: x86 64-bit Users
---

### Post by Superkuh on 2008-06-03
QtX3 is a simple program for interfacing with my intel QX3 USB microscope. I am not having problems with the scope, and xsane and xawtv interface with /proc/cpia/video0 just fine, but I am having specific issues forcing a x86_64 library (downloaded to the same directory in desperation) to be used by the program. Below is what I have tried thusfar. Any hints or direction would be much appreciated.

```
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ ldd QtX3 | grep libqt*
        libqt-mt.so.3 => not found
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ ls -la | grep libqt*
-rw-r--r-- 1 superkuh superkuh 10907624 2008-06-03 13:32 libqt-mt.so.3
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ LD_LIBRARY_PATH=/home/superkuh/app_installs/qtx3/QtX3/
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ echo ${LD_LIBRARY_PATH}
/home/superkuh/app_installs/qtx3/QtX3/
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ export LD_LIBRARY_PATH

superkuh@epimetheus:~/app_installs/qtx3/QtX3$ ./QtX3 
./QtX3: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ file ./libqt-mt.so.3
./libqt-mt.so.3: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), stripped

superkuh@epimetheus:~/app_installs/qtx3/QtX3$ uname -m
x86_64

superkuh@epimetheus:~/app_installs/qtx3/QtX3$ ldconfig -p | grep libqt
	libqtmcop.so.1 (libc6,x86-64) => /usr/lib/libqtmcop.so.1
	libqt-mt.so.3 (libc6,x86-64) => /usr/lib/libqt-mt.so.3
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ ldconfig -p | grep /lib64 | wc -l
**0**

superkuh@epimetheus:~/app_installs/qtx3/QtX3$ [b]file  /usr/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3: symbolic link to 'libqt-mt.so.3.3.8'[/b]
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ locate libqt-mt.so.3.3.8
/usr/lib/libqt-mt.so.3.3.8
superkuh@epimetheus:~/app_installs/qtx3/QtX3$ file /usr/lib/libqt-mt.so.3.3.8
/usr/lib/libqt-mt.so.3.3.8: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), stripped

superkuh@epimetheus:~/app_installs/qtx3/QtX3$ ./QtX3 /dev/video0 /proc/cpia/video0
./QtX3: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64
```

---

### Post by RAOF on 2008-06-04
The more interesting output would be 'file QtX3'; I'm guessing that it's a 32bit application, which can't use x86-64 libraries.  Installing the 'ia32-libs' package may well allow you to use this app.

---

### Post by Superkuh on 2008-06-04
```
QtX3: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped
```
... sigh. I should have checked that. Thank you. I have ia32-libs installed. I guess I'll just try to recompile from source. [edit] Yep. It works in the 32bit chroot and with the correct 32bit libs. Silly me.

---

