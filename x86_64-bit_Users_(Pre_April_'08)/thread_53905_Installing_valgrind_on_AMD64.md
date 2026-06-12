---
title: "Installing valgrind on AMD64"
date: 2005-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by UrbanFallout on 2005-08-02
Hello to any developers out there

I've been trying to install valgrind (a very good bounds checker) on my AMD64 laptop.
Unfortunately I cannot locate a deb file for a 64 bit architecture in the ubuntu repositories, only the i386 version.

I tried downloading the source and running a "./configure" and then "make" the old fashioned way, but I get this error when running ./configure:

checking build system type... x86_64-unknown-linux
checking host system type... x86_64-unknown-linux
checking for a supported CPU... no (x86_64)
configure: error: Unsupported host architecture. Sorry

I cannot find anything in the local documentation about whether 64 bit architectures are supported. However the site [http://www.valgrind.org/info/](http://www.valgrind.org/info/) says 64bit architectures ARE supported.

Has anybody had any luck with either finding the correct .deb or installing valgrind on a 64 bit machine?

Many thanks in advance
Nick

---

### Post by jebe on 2005-08-02
did you used the 3.0 version ?

"valgrind-3.0 will support AMD64 on Linux."

dont know it this is already working

[http://valgrind.org/devel/](http://valgrind.org/devel/)

please let me now if you get it working


jebe

---

### Post by UrbanFallout on 2005-08-03
Thanks. 

Yup I just found a sourceforge forum mentioning this [here](http://sourceforge.net/mailarchive/forum.php?thread_id=7622499&forum_id=32038) 
It doesn't sound like they've packaged a release version yet though.

I tried downloading the latest release from their subversion repository using:
[COLOR=Green]svn co svn://svn.valgrind.org/valgrind/trunk valgrind[/COLOR]
(I had to install [COLOR=DarkRed]svn-buildpackage[/COLOR] first)

I then installed [COLOR=DarkRed]autoconf[/COLOR] so that a configure file could be generated, but that bombs out with.
[SIZE=1]configure.in:4: error: possibly undefined macro: AM_CONFIG_HEADER
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:5: error: possibly undefined macro: AM_INIT_AUTOMAKE
configure.in:7: error: possibly undefined macro: AM_MAINTAINER_MODE
configure.in:429: error: possibly undefined macro: AM_CONDITIONAL[/SIZE]

I think its too much work to get this working, so I think I may wait for a release version  :sad:.

Thanks for coming back to me.
Nick

---

### Post by UrbanFallout on 2005-08-03
OK, had a bit more of a fiddle and I managed to install a i386 valgrind into a chroot environment.
Not ideal, but it allows me to do my debugging for now.

Here's what I did:
1. Installed a 32bit chroot envirnment, by followed the instructions in the [chroot32 howto](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot) .

2. Used synaptic to download the following packages in the new chroot envirnoment:
g++, lapack, make

3. Downloaded the valgrind deb from [here](http://packages.ubuntu.com/hoary/devel/valgrind)  (couldn't find it in synaptic for some reason)

4. Installed valgrind
dpkg -i valgrind*.deb

Compiled and the thing actually worked.

Comments and corrections appreciated.

Cheers
Nick

---

### Post by jebe on 2005-08-03
so,

bought athlon 3000+ today ;). 

cause i want to avaid installing a chroot shit, i compiled valgrind:

after downloading just make;

./autogen.sh
make
sudo make install (or better: sudo checkinstall)


works fine, jebe

---

