---
title: "help with 32 bit apps in 64 bit"
date: 2006-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by neighborlee on 2006-07-07
**I am posting this in here as where it should have gone to begin with**


Quote:
Originally Posted by neighborlee View Post
hi..

Could someone suggest a workaround for this:

neighborlee@Heartseed:~/Programs/plugger-5.1.3$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for atexit in -ldl... yes
configure: error: Unable to find X11 libraries

and I do have x11 libs and dev installed, unless its some other lib its wanting no idea......

thx
nl

sorry to BUMP , but I"d really love to know whats wrong, I just dont possess the knowledge of this system to ascertain a plausible reason so I hope someone here does..

also I get similar issues with another app:

neighborlee@Heartseed:~/Programs/sharpconstruct-bin-0.12/bin$ ./sharpconstruct
./sharpconstruct: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory

yet:
whereis libglademm-2.4.so.1
libglademm-2.4.so: /usr/lib/libglademm-2.4.so.1
neighborlee@Heartseed:~/Programs/sharpconstruct-bin-0.12/bin$ file /usr/lib/libglademm-2.4.so.1
/usr/lib/libglademm-2.4.so.1: symbolic link to `libglademm-2.4.so.1.0.5

shows this..so I did:
file /usr/lib/libglademm-2.4.so.1.0.5
/usr/lib/libglademm-2.4.so.1.0.5: ELF 64-bit LSB shared object, AMD x86-64, version 1 (SYSV), stripped


im rather sure the sharpconstruct isn't a 64 bit app so therein is the problem shrug..I thought 64 bit OS"s could handle running 32 bit apps ?

if not , and running 32bit apps in 64 environments is still far from perfected, is my only option a chroot 6 bit env ?

thx
nl

---

### Post by falcon15500 on 2006-07-07
I think the problem there is that the sharpconstruct app you are trying to run is a 32-bit app, and you only have the corresponding 64-bit libs.  While you are correct in that the 64-bit proc can run 32-bit apps, the apps and the libs have to match.

falc

---

### Post by Kilz on 2006-07-09
> **neighborlee said:**
> **I am posting this in here as where it should have gone to begin with**

im rather sure the sharpconstruct isn't a 64 bit app so therein is the problem shrug..I thought 64 bit OS"s could handle running 32 bit apps ?

if not , and running 32bit apps in 64 environments is still far from perfected, is my only option a chroot 6 bit env ?

thx
nl

You can run 32bit applications, and as falcon15500 said you need 32bit libs.
To do that install dpkg-dev
```
sudo apt-get install dpkg-dev
```
That will alow you to open .deb files with the archive program. [Then go here]("http://packages.ubuntu.com/") search the contents of a package, download the i386 version. Extract the .deb file, extract the data.tar.gz file inside the .deb, inside the data.tar.gz will be a /usr/lib, copy the contents to /usr/lib32 in your file system.

---

### Post by neighborlee on 2006-07-14
> **Kilz said:**
> You can run 32bit applications, and as falcon15500 said you need 32bit libs.
To do that install dpkg-dev
```
sudo apt-get install dpkg-dev
```
That will alow you to open .deb files with the archive program. [Then go here]("http://packages.ubuntu.com/") search the contents of a package, download the i386 version. Extract the .deb file, extract the data.tar.gz file inside the .deb, inside the data.tar.gz will be a /usr/lib, copy the contents to /usr/lib32 in your file system.

ok thx everyone 

cheers
g.leej(nl)

---

