---
title: "wlassistant dependency issue"
date: 2006-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuntubrian on 2006-04-20
I'm trying to get WLAssistant installed on my powerbook. I installed it from a .deb derived from an .rpm with Alien-no problem. It shows up and is executable but when I try to run it I get a message:
wlassistant: /lib/libc.so.6: version `GLIBC_2.4' not found (required by wlassistant)

when I try to install  I get:
e@ubuntu:~$ sudo dpkg -i glibc_2.4-5_powerpc.deb
(Reading database ... 199893 files and directories currently installed.)
Unpacking glibc (from glibc_2.4-5_powerpc.deb) ...
dpkg: error processing glibc_2.4-5_powerpc.deb (--install):
 trying to overwrite `/usr/lib/gconv/ANSI_X3.110.so', which is also in package libc6
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 glibc_2.4-5_powerpc.deb

Does anyone know of a workaround for this?
8-)

---

