---
title: "Compiling isses"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by bobbymcsteels on 2006-01-28
Hi, I have tried to compile a couple of things now, at 1st I just thought it was bad/corrupt files that I was trying but same sort of thing keeps happening have got build-essentials but still keep getting similar errors... Any help with this would be great. ```
root@ubuntu:/home/mcsteels/tuxracer/tuxracer-0.61# ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for working const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for strdup... yes
checking for finite... yes
checking for isnan... yes
checking for _finite... no
checking for _isnan... no
checking for ieeefp.h... no
checking for Win32 platform... no
checking for X... no
checking for main in -ldl... yes
checking for main in -lm... yes
checking for tcl8.3 library... no
checking for tcl83 library... no
checking for tcl8.2 library... no
checking for tcl82 library... no
checking for tcl8.0 library... no
checking for tcl80 library... no
checking for tcl library... no
configure: error: Cannot find Tcl library
 
```

---

### Post by bernardfrancois on 2006-01-28
You need to have some library called Tcl.

Looking at my installed software in synaptic here, I see that I have **tcl8.4** installed over here. If it doens't work after installing that (if you don't already have it), you can install **tcl8.4-dev**. Mostly you need those *dev*-packages for compiling.

If it still doesn't work, try other tcl versions which are available.

If it still doesn't work after that, try searching for the official page of tcl and install it from source first. Or first read the documentation on the official site of the program you are trying to compile.

Most dependencies while compiling can be resolved by installing binary packages using synaptic. Make sure you have all repositories enabled (check the [wiki](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=AddingMultimediaRepositories) if you don't have them or if you don't know what I'm talking about)

---

### Post by JAwuku on 2006-01-28
Also you can install the packages

[B]autoconf
automake1.8
aclocal
libtool
gnome-devel
libx11-dev[/B]

which may satisfy some dependencies.

---

### Post by pradhishkumar on 2006-02-13
hey guys  this is pradhish i got a new kubuntu version hoary juz days before the breezy release,  the problem i m facing is i cannot install new apps as when i try to install ie compile from source it says c compiler not found, can anyone help with this

---

### Post by bastiegast on 2006-02-13
[QUOTE=pradhishkumar]hey guys  this is pradhish i got a new kubuntu version hoary juz days before the breezy release,  the problem i m facing is i cannot install new apps as when i try to install ie compile from source it says c compiler not found, can anyone help with this[/QUOTE]
So you need a C compiler, run:
```
sudo apt-get install build-essential
```

---

