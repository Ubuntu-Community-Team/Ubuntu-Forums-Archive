---
title: "Cant install EDA Alliance on Gutsy 64 ! Please, Help"
date: 2007-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by tarekeldeeb on 2007-12-30
Hello all,

It's about 3 months since my switching to ubuntu <from winxp> and i feel gr8 :popcorn:

I want to install an EDA prgram called Alliance, this package is not fount at aany repos .. i downloaded the binaries (x86) .. extracted to /opt

when i tried to open any of the BINs, it gave an error that libXm.so.3 cannot be found

I thought that it might be a 64/32 lib problem .. so i forced an installation of libmotif3 <x86> ..same problem .. and i tried to force the libxp6 <x86> as well .. no advance ..

when i try to allocate the library, i find this:
```

$ ls -l `locate libXm.so.3`
lrwxrwxrwx 1 root root      14 2007-12-12 02:30 /opt/matlab/etc/sys/os/glnxa64/libXm.so.3 -> libXm.so.3.0.1
-rw-r--r-- 1 root root 2811528 2005-11-27 23:40 /opt/matlab/etc/sys/os/glnxa64/libXm.so.3.0.1


```
i got mad .. something must be wrong !

so i reinstalled the original libs .. and deleted the binaries of Alliance ! :mad:


I found an RPM package for the Alliance .. downloaded it .. and made
```
sudo apt-get install rpm
```

bu it gave a dependeciy errors:
> /bin/sh is needed by alliance-5.0-20070718.i386
        libICE.so.6 is needed by alliance-5.0-20070718.i386
        libSM.so.6 is needed by alliance-5.0-20070718.i386
        libX11.so.6 is needed by alliance-5.0-20070718.i386
        libXext.so.6 is needed by alliance-5.0-20070718.i386
        libXm.so.3 is needed by alliance-5.0-20070718.i386
        libXp.so.6 is needed by alliance-5.0-20070718.i386
        libXpm.so.4 is needed by alliance-5.0-20070718.i386
        libXt.so.6 is needed by alliance-5.0-20070718.i386
        libc.so.6 is needed by alliance-5.0-20070718.i386
        libc.so.6(GLIBC_2.0) is needed by alliance-5.0-20070718.i386
        libc.so.6(GLIBC_2.1) is needed by alliance-5.0-20070718.i386
        libc.so.6(GLIBC_2.1.3) is needed by alliance-5.0-20070718.i386
        libc.so.6(GLIBC_2.3) is needed by alliance-5.0-20070718.i386
        libc.so.6(GLIBC_2.3.4) is needed by alliance-5.0-20070718.i386
        libgcc_s.so.1 is needed by alliance-5.0-20070718.i386
        libgcc_s.so.1(GCC_3.0) is needed by alliance-5.0-20070718.i386
        libm.so.6 is needed by alliance-5.0-20070718.i386
        libm.so.6(GLIBC_2.0) is needed by alliance-5.0-20070718.i386
        libstdc++.so.6 is needed by alliance-5.0-20070718.i386
        libstdc++.so.6(CXXABI_1.3) is needed by alliance-5.0-20070718.i386
        libstdc++.so.6(GLIBCXX_3.4) is needed by alliance-5.0-20070718.i386


Can any1 help me ?
:confused::confused:

Thanks in advance,
Tarek

---

### Post by Kilz on 2007-12-30
> **tarekeldeeb said:**
> Hello all,

It's about 3 months since my switching to ubuntu <from winxp> and i feel gr8 :popcorn:

I want to install an EDA prgram called Alliance, this package is not fount at aany repos .. i downloaded the binaries (x86) .. extracted to /opt

when i tried to open any of the BINs, it gave an error that libXm.so.3 cannot be found

I thought that it might be a 64/32 lib problem .. so i forced an installation of libmotif3 <x86> ..same problem .. and i tried to force the libxp6 <x86> as well .. no advance ..

when i try to allocate the library, i find this:
```

$ ls -l `locate libXm.so.3`
lrwxrwxrwx 1 root root      14 2007-12-12 02:30 /opt/matlab/etc/sys/os/glnxa64/libXm.so.3 -> libXm.so.3.0.1
-rw-r--r-- 1 root root 2811528 2005-11-27 23:40 /opt/matlab/etc/sys/os/glnxa64/libXm.so.3.0.1


```
i got mad .. something must be wrong !

so i reinstalled the original libs .. and deleted the binaries of Alliance ! :mad:


I found an RPM package for the Alliance .. downloaded it .. and made
```
sudo apt-get install rpm
```

bu it gave a dependeciy errors:


Can any1 help me ?
:confused::confused:

Thanks in advance,
Tarek

You may have messed your install. Never ever, ever force in libraries. They overwrite 64bit versions. 32bit libraries go in a different place in a 64bit system. You need to reinstall 64bit versions of those libraries [then get Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs"). It will install the 32bit libraries in the correct place without overwriting 64bit libraries and making your system unstable.

---

