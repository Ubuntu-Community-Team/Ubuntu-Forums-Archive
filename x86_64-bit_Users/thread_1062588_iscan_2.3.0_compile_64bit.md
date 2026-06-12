---
title: "iscan 2.3.0 compile 64bit"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by dpsleep on 2009-02-07
Hey all, I'm trying to get [iscan]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do#SD00000028") to compile for my 64bit machine. The packages they have available are i386 RPMs so I have no way of using alien to convert to debs. I've satisfied all dependencies but it errors on compile.

```
gilokee@foobar:~/Desktop/iscan-2.3.0$ make
make  all-recursive
make[1]: Entering directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0'
Making all in include
make[2]: Entering directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/include'
Making all in libltdl
make[2]: Entering directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/libltdl'
make  all-am
make[3]: Entering directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/libltdl'
/bin/bash ./libtool --mode=compile --tag=CC gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c -o ltdl.lo ltdl.c
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
/bin/bash ./libtool --mode=link --tag=CC gcc  -g -O2   -o libltdlc.la   ltdl.lo -ldl 
rm -fr  .libs/libltdlc.a .libs/libltdlc.la
ar cru .libs/libltdlc.a .libs/ltdl.o
ranlib .libs/libltdlc.a
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[3]: Leaving directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/libltdl'
make[2]: Leaving directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/libltdl'
Making all in lib
make[2]: Entering directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/lib'
Making all in sanei
make[2]: Entering directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/sanei'
if /bin/bash ../libtool --mode=compile --tag=CC gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane  -I../include -I../include   -g -O2 -MT libsanei_la-sanei_config.lo -MD -MP -MF ".deps/libsanei_la-sanei_config.Tpo" -c -o libsanei_la-sanei_config.lo `test -f 'sanei_config.c' || echo './'`sanei_config.c; \
	then mv -f ".deps/libsanei_la-sanei_config.Tpo" ".deps/libsanei_la-sanei_config.Plo"; else rm -f ".deps/libsanei_la-sanei_config.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane -I../include -I../include -g -O2 -MT libsanei_la-sanei_config.lo -MD -MP -MF .deps/libsanei_la-sanei_config.Tpo -c sanei_config.c  -fPIC -DPIC -o .libs/libsanei_la-sanei_config.o
In file included from sanei_config.c:52:
../include/sane/sanei.h:89:23: error: sane/sane.h: No such file or directory
In file included from sanei_config.c:52:
../include/sane/sanei.h:163: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sanei_check_value'
../include/sane/sanei.h:166: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sanei_constrain_value'
In file included from sanei_config.c:53:
../include/sane/sanei_config.h:124: error: expected declaration specifiers or '...' before 'SANE_Status'
sanei_config.c: In function 'sanei_config_get_string':
sanei_config.c:166: warning: incompatible implicit declaration of built-in function 'strndup'
make[2]: *** [libsanei_la-sanei_config.lo] Error 1
make[2]: Leaving directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0/sanei'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gilokee/.local/share/Trash/files/iscan-2.3.0'
make: *** [all] Error 2

```

Does anyone know of a way to fix this? and if not could someone possibly alien those RPMs so I can try to force install them?

thanks

---

### Post by cariboo on 2009-02-07
Alien is pretty easy to use, open a terminal and type:

```
sudo alien -d name_of.rpm
```

you have to be in the same directory as the file. Once alien has finished just double-click the deb and gdebi will install it.

Jim

---

### Post by Yellow Pasque on 2009-02-07
> ../include/sane/sanei.h:89:23: error: sane/sane.h: No such file or directory

...
```
sudo apt-get install libsane-dev
```

---

### Post by dpsleep on 2009-02-08
> **cariboo907 said:**
> Alien is pretty easy to use, open a terminal and type:

```
sudo alien -d name_of.rpm
```

you have to be in the same directory as the file. Once alien has finished just double-click the deb and gdebi will install it.

Jim

i guess you didn't really read my post... alien cant convert 32 bit rpms to 64 bit deb. and i dont have a single 32 bit machine.

---

### Post by dpsleep on 2009-02-08
> **Temüjin said:**
> ...
```
sudo apt-get install libsane-dev
```

ahh, thanks for spotting that, must have sliped my eyes. so i got the sane dev packages but now it's giving me a new error.

```
gilokee@foobar:~/Desktop/iscan-2.3.0$ make
make  all-recursive
make[1]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0'
Making all in include
make[2]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0/include'
Making all in libltdl
make[2]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0/libltdl'
make  all-am
make[3]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0/libltdl'
/bin/bash ./libtool --mode=compile --tag=CC gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c -o ltdl.lo ltdl.c
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
/bin/bash ./libtool --mode=link --tag=CC gcc  -g -O2   -o libltdlc.la   ltdl.lo -ldl 
rm -fr  .libs/libltdlc.a .libs/libltdlc.la
ar cru .libs/libltdlc.a .libs/ltdl.o
ranlib .libs/libltdlc.a
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[3]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0/libltdl'
make[2]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0/libltdl'
Making all in lib
make[2]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0/lib'
Making all in sanei
make[2]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0/sanei'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0/sanei'
Making all in backend
make[2]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0/backend'
make  all-am
make[3]: Entering directory `/home/gilokee/Desktop/iscan-2.3.0/backend'
/bin/bash ../libtool --mode=link --tag=CC gcc  -g -O2   -o libsane-epkowa.la -rpath /usr/local/lib/sane -version-info 1:15:0 libsane_epkowa_la-epkowa.lo libsane_epkowa_la-epkowa_ip.lo libsane_epkowa_la-epkowa_scsi.lo libsane_epkowa_la-epkowa_usb.lo libsane_epkowa_la-sane_strstatus.lo libsane-epkowa-s.la ../sanei/libsanei.la ../libltdl/libltdlc.la -lsane -lusb 
gcc -shared  .libs/libsane_epkowa_la-epkowa.o .libs/libsane_epkowa_la-epkowa_ip.o .libs/libsane_epkowa_la-epkowa_scsi.o .libs/libsane_epkowa_la-epkowa_usb.o .libs/libsane_epkowa_la-sane_strstatus.o -Wl,--whole-archive ./.libs/libsane-epkowa-s.a ../sanei/.libs/libsanei.a ../libltdl/.libs/libltdlc.a -Wl,--no-whole-archive  -Wl,--rpath -Wl,/usr/lib -Wl,--rpath -Wl,/usr/lib -ldl /usr/lib/libsane.so /usr/lib/libusb.so  -Wl,-soname -Wl,libsane.so.1 -o .libs/libsane-epkowa.so.1.0.15
[B]/usr/bin/ld: ./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): could not read symbols: Bad value
collect2: ld returned 1 exit status[/B]
make[3]: *** [libsane-epkowa.la] Error 1
make[3]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0/backend'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0/backend'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gilokee/Desktop/iscan-2.3.0'
make: *** [all] Error 2

```

---

### Post by Yellow Pasque on 2009-02-09
I'm not quite sure how to fix that off the top of my head. Editing the Makefile might be needed. Hopefully, my motherboard replacement will be here by the end of the week and I can try and duplicate your task. I'm stuck on an old 32-bit system at the moment.

---

### Post by Yellow Pasque on 2009-02-20
Will a newer version work or do you need the older one?
[http://linux.avasys.jp/drivers/iscan/2.16.1/iscan_2.16.1-1_amd64.deb](http://linux.avasys.jp/drivers/iscan/2.16.1/iscan_2.16.1-1_amd64.deb)

BTW, make sure you have libsane-extras installed (found in the restricted repository)

---

