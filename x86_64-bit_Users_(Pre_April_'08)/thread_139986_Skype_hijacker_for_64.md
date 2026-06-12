---
title: "Skype hijacker for 64 ?"
date: 2006-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbee on 2006-03-05
I'm running skype and I'm having trouble trying to get it to work properly. I get the /dev/dsp issue...

There isn't any skype_hijacker.deb on seveas' site, and when I download the source and try to compile it I get 
```

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libdl.so when searching for -ldl
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libdl.a when searching for -ldl
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libdl.so when searching for -ldl
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libdl.a when searching for -ldl
/usr/bin/ld: skipping incompatible /usr/lib/libdl.so when searching for -ldl
/usr/bin/ld: skipping incompatible /usr/lib/libdl.a when searching for -ldl
/usr/bin/ld: cannot find -ldl
collect2: ld returned 1 exit status
make: *** [all] Error 1

```
... what's up with my linker ?
... and why didn't seveas make a .deb for 64 bit :( 

Thanks

---

### Post by SirKillalot on 2006-03-05
> Known problems:

Under AMD64, there has been problems with getting the library to work. Compiling with -m32 seems to fix it. Credits to Dominique Schaefer for first mentioning the problem, and providing a fix. 
see [http://195.38.3.142:6502/skype/](http://195.38.3.142:6502/skype/)

---

### Post by dbee on 2006-03-05
Tried it already, it doesn't make any difference. Thanks anyway though. 
I've also reinstalled build-essential, but no luck there either. 
Why does everything have to be so difficult ?

Can anyone else hazard a guess ... ?

This is what my makefile looks like btw 
```

CC=gcc
CFLAGS=-O2 -Wall -m32
LIBADD_DL=-ldl
OPTIONS=-shared -fpic

PREFIX=/usr/local
BINDIR=$(PREFIX)/bin
LIBDIR=$(PREFIX)/lib

all:
        $(CC) $(CFLAGS) $(LIBADD_DL) $(OPTIONS) skype_dsp_hijacker.c -o libskyp$
install:
        cp libskype_dsp_hijacker.so $(LIBDIR)
        cp skype_dsp_hijacker $(BINDIR)

clean:
#       rm -f *~
        rm -f libskype_dsp_hijacker.so

```
... I've also tried switching the gcc versions between 3.4 and 4.0 but that didn't help...

---

### Post by dbee on 2006-03-07
Does no-one have an answer for this one then ?

I really need to get this working !

---

### Post by dbee on 2006-03-07
Thanks to Jan here for trying to help me out with this one ....

So here I checked for linked libraries in my skype binary, then checked whether that library did actually exist. There doesn't seem to be a problem.

```


root@ubuntu64:/etc/skype/skype-1.2.0.18# ldd skype
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x5557c000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x555ff000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x55614000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0x55617000)
        libXft.so.2 => /usr/lib32/libXft.so.2 (0x55620000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x55632000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x5569c000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x556cb000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x556d2000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x556eb000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x556ee000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556fb000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x557bb000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x557cd000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55887000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x558a9000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x558b4000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0x559e2000)
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0x561a0000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x561a3000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x561f1000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0x561f9000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x561fd000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x56211000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x56231000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x56234000)

root@ubuntu64:/home/babo/Desktop/skype_dsp_hijacker-0.6# ls /lib32
ld-2.3.5.so               libcrypt-2.3.5.so  libnsl.so.1              libnss_nisplus.so.2  libresolv-2.3.5.so
ld-linux.so.2             libcrypt.so.1      libnss_compat-2.3.5.so   libnss_nis.so.2      libresolv.so.2
libacl.so.1               libc.so.6          libnss_compat.so.2       libpamc.so.0         librt-2.3.5.so
libacl.so.1.1.0           libdl-2.3.5.so     libnss_dns-2.3.5.so      libpamc.so.0.76      librt.so.1
libanl-2.3.5.so           libdl.so.2         libnss_dns.so.2          libpam_misc.so.0     libSegFault.so
libanl.so.1               libm-2.3.5.so      libnss_files-2.3.5.so    libpam_misc.so.0.76  libthread_db-1.0.so
libattr.so.1              libmemusage.so     libnss_files.so.2        libpam.so.0          libthread_db.so.1
libattr.so.1.1.0          libm.so.6          libnss_hesiod-2.3.5.so   libpam.so.0.76       libutil-2.3.5.so
libBrokenLocale-2.3.5.so  libncurses.so.5    libnss_hesiod.so.2       libpcprofile.so      libutil.so.1
libBrokenLocale.so.1      libncurses.so.5.4  libnss_nis-2.3.5.so      libpthread-0.10.so   tls
libc-2.3.5.so             libnsl-2.3.5.so    libnss_nisplus-2.3.5.so  libpthread.so.0

root@ubuntu64:/etc/skype/skype-1.2.0.18# cd /usr/lib32

root@ubuntu64:/usr/lib32# ls
AuErrorDB                          libglib-1.2.so.0               libpangoft2-1.0.so.0                libXdmcp.so.6
gconv                              libglib-1.2.so.0.0.10          libpangoft2-1.0.so.0.1000.0         libXdmcp.so.6.0.0
gdk-imlib1                         libglib-2.0.so.0               libpangohack.so.0                   libXext.so.6
gtk-2.0                            libglib-2.0.so.0.800.1         libpangohack.so.0.0                 libXext.so.6.4.1
i686                               libGL.la                       libpangox-1.0.so.0                  libXfixes.so.3
libart_lgpl_2.so.2                 libGL.so                       libpangox-1.0.so.0.1000.0           libXfixes.so.3.0.0
libart_lgpl_2.so.2.3.17            libGL.so.1                     libpangoxft-1.0.so.0                libXft.so.2
libatk-1.0.so.0                    libGL.so.1.0.8178              libpangoxft-1.0.so.0.1000.0         libXft.so.2.1.2
libatk-1.0.so.0.1011.0             libGLU.so.1                    libpixman.so.1                      libXinerama.so.1
libaudio.so.2                      libGLU.so.1.3.060302           libpixman.so.1.0.0                  libXinerama.so.1.0.0
libaudio.so.2.3                    libgmodule-1.2.so.0            libpng12.so.0                       libXi.so.6
libbz2.so.1.0                      libgmodule-1.2.so.0.0.10       libpng12.so.0.1.2.8                 libXi.so.6.0.0
libbz2.so.1.0.2                    libgmodule-2.0.so.0            libportaudio.so.0                   libxml2.so.2
libcairo.so.2                      libgmodule-2.0.so.0.800.1      libportaudio.so.0.0.18              libxml2.so.2.6.21
libcairo.so.2.2.2                  libgobject-2.0.so.0            libSM.so.6                          libXmu.so.6
libdb-4.2.so                       libgobject-2.0.so.0.800.1      libSM.so.6.0.1                      libXmu.so.6.2.0
libexpat.so.0                      libgthread-1.2.so.0            libsndfile.so.1                     libXmuu.so.1
libexpat.so.1                      libgthread-1.2.so.0.0.10       libsndfile.so.1.0.10                libXmuu.so.1.0.0
libexpat.so.1.0.0                  libgthread-2.0.so.0            libstartup-notification-1.so.0      libXpm.so.4
libfontconfig.so.1                 libgthread-2.0.so.0.800.1      libstartup-notification-1.so.0.0.0  libXpm.so.4.11.0
libfontconfig.so.1.0.4             libgtk-1.2.so.0                libstdc++.so.5                      libXrandr.so.2
libform.so.5                       libgtk-1.2.so.0.9.1            libstdc++.so.5.0.7                  libXrandr.so.2.0.1
libform.so.5.4                     libgtk-x11-2.0.so.0            libstdc++.so.6                      libXrender.so.1
libfreetype.so.6                   libgtk-x11-2.0.so.0.800.2      libstdc++.so.6.0.5                  libXrender.so.1.3.0
libfreetype.so.6.3.5               libICE.so.6                    libstlport_gcc.so.4.6               libXTrap.so.6
libgcc_s.so.1                      libICE.so.6.4.1                libtiff.so.4                        libXTrap.so.6.4.0
libgcj.so.6                        libjpeg.so.62                  libtiff.so.4.1.3                    libXt.so.6
libgcj.so.6.0.0                    libjpeg.so.62.0.0              libwmf-0.2.so.7                     libXt.so.6.0.0
libgdk-1.2.so.0                    liblcms.so.1                   libwmf-0.2.so.7.1.0                 libXtst.so.6
libgdk-1.2.so.0.9.1                liblcms.so.1.0.13              libwmflite-0.2.so.7                 libXtst.so.6.0.1
libgdk_imlib.so.1                  libmenu.so.5                   libwmflite-0.2.so.7.0.1             libz.so.1
libgdk_imlib.so.1.9.14             libmenu.so.5.4                 libX11.so.6                         libz.so.1.2.3
libgdk_pixbuf-2.0.so.0             libmyspell.so.3                libX11.so.6.2.0                     nptl
libgdk_pixbuf-2.0.so.0.800.2       libmyspell.so.3.1              libXau.so.6                         nvidia
libgdk_pixbuf_xlib-2.0.so.0        libnvidia-tls.so.1             libXau.so.6.0.0                     openoffice
libgdk_pixbuf_xlib-2.0.so.0.800.2  libnvidia-tls.so.1.0.8178      libXaw3d.so.6                       openoffice2
libgdk-x11-2.0.so.0                libpanel.so.5                  libXaw3d.so.6.1                     pango
libgdk-x11-2.0.so.0.800.2          libpanel.so.5.4                libXaw7.so.7                        pangohack.so.0
libgij.so.6                        libpango-1.0.so.0              libXaw7.so.7.0.0                    tls
libgij.so.6.0.0                    libpango-1.0.so.0.1000.0       libXaw.so.7                         X11
libGLcore.so.1                     libpangocairo-1.0.so.0         libXcursor.so.1
libGLcore.so.1.0.8178              libpangocairo-1.0.so.0.1000.0  libXcursor.so.1.0.2


```

I also tried to switch around the makefile but no luck there either ...
```

CC=gcc
CFLAGS=-O2 -Wall -m32
LIBADD_DL=-L/lib32 -L/usr/lib32 -ldl
OPTIONS=-shared -fpic

PREFIX=/usr/local
BINDIR=$(PREFIX)/bin
LIBDIR=$(PREFIX)/lib

all:
        $(CC) $(CFLAGS) $(LIBADD_DL) $(OPTIONS) skype_dsp_hijacker.c -o libskype_dsp_hijacker.so

install:
        cp libskype_dsp_hijacker.so $(LIBDIR)
        cp skype_dsp_hijacker $(BINDIR)

clean:
#       rm -f *~
        rm -f libskype_dsp_hijacker.so

```

... with various versions of the above, but still no luck ... :-k

---

### Post by dbee on 2006-03-12
So the new 64bit skype hijacker recommends that I install these rpm's ...

glibc-devel-32bit
glibc-locale-32bit
glibc-32bit

... when I track them down I'll update this thread ...

---

### Post by queenorych on 2006-03-13
What version of gcc are you using?  I believe -m32 only works with gcc 4.x

---

### Post by dbee on 2006-03-14
I tried with both versions but it doesn't work with either ... it's really frustrating

---

### Post by queenorych on 2006-03-14
It looks to me like you need to have a 32 bit libdl.  This can be libdl.a or libdl.so (shared).  I see you have /lib32/libdl.so.2.  I would see what /usr/lib/libdl.so is, it probably is just a link to /usr/lib/libdl.so.2.  So make the link in your  /lib32 to the 32 bit bersion of libdl.so.2.  If that doesn't work, just statically compile a 32 bit version of libdl youself.

On a side note, I am running hijacker/skype/amd64.  It was a very smooth setup with a chroot.

---

### Post by dbee on 2006-03-15
> 
On a side note, I am running hijacker/skype/amd64. It was a very smooth setup with a chroot.

... pls elaborate :-D 

How did you set it up with a chroot ???

---

### Post by queenorych on 2006-03-16
1. setup chroot following one of the many guides
2. dchroot -d sudo apt-get install build-essentials
3.  Install skype into chroot 'dchroot -d sudo dpk -i skype...'
4.  Compile hijacker in chroot :
   'dchroot -d ./configure'
   'dchroot -d make
5.  dchroot -d ./skype_hijacker

I used the library preloading of hijacker directly (see the readme included with hicker).  

Both skype, hijacker, and all the libraries they use are 32 bit code.

---

### Post by dbee on 2006-03-21
So I've done a chroot environment and installed the .deb
Then I've installed the hijacker and everything seems to be fine.

The hijacker needed the /etc/hosts file in order to find localhost to set itself up, but there wasn't any major problems.

I run a
> 
ldd skype 

and everything seems to be fine ... no lost libraries or anything like that.

But when I go into chroot and execute 
> 
./skype

...it runs for a second and then just returns with no error or text output ... AND no skype ... :-#    .... errrr .... where's skype ???

I run a 
> 
ps aux | grep skype 

... and there is no skype process running ...

> 
root@ubuntu64:/usr/bin# file skype
skype: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped


Also ... should my chroot have it's own X ?
There is no X in chroot at the moment ... could that be in ?
How do I import X into chroot ?

Thanks

---

### Post by queenorych on 2006-03-21
if skype won't run, then hijacker won't do you any good.  Get skype working.  I downloaded the non-static skype, and downloaded and installed the missing qt library off some forum post.  You should get skype to come up if you type dchroot -d skype.  If skype doesn't come up, then forget about hijacker.

If you get no errors, try a debugger.  dchroot -d gdb skype
then type "run".

What happens?

---

### Post by dbee on 2006-03-25
> 
Starting program: /usr/bin/skype
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
Error while reading shared library symbols:
Cannot find new threads: generic error
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
....


.... ](*,)

---

### Post by henriquemaia on 2006-04-07
[QUOTE=dbee].... ](*,)[/QUOTE]

This is what I did to get it to work:

**1.** Downloaded the skype_dsp_hijacker package.

**2.** Untared it. 

**3.** Opened the skype_dsp_hijacker directory.

**4.** Edited the Makefile

**5.** In the line where it read 
[INDENT][B]
[COLOR="DarkRed"]CFLAGS=-O2 -m32 -Wall[/COLOR] [/B]
[/INDENT]
removed the **[COLOR="DarkRed"]-m32[/COLOR]** entry.

**6.** Saved the file.

**7.** As I have installed skype through the static tarball provided in skype's site, I also edited the file skype_dsp_hijacker.

**8.** In the bottom of the file where it read:

[INDENT][B][COLOR="DarkRed"]# invoke the program with the args given
exec skype "$@"[/COLOR][/B][/INDENT]

changed **[COLOR="DarkRed"]exec "$@"[/COLOR]** to the path where I installed skype static.

**9.** Saved the file

**10.** Checkinstalled it

ps: I'm running Dapper amd64, not Breezy.

---

