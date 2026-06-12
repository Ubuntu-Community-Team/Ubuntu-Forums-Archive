---
title: "eagle-usb &amp; the kernel header files"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by aatiis on 2007-10-26
After years of openSUSE, I switched to Ubuntu, and I already have a pboblem :(

Anyway, I have a SAGEM F@st 800-840 modem and I could not compile the right module for it. I have installed the following packages:

eagle-usb-utils_2.1.1-3ubuntu1
eagle-usb-data_2.1.1-3ubuntu1
eagle-usb-modules-source_2.1.1-3ubuntu1

and the kernel header files for my 2.6.22-14-generic kernel.

The first problem is configuring the modules-source package. It cannot find the kernel version, because instead of `uname -r` it uses this code:
```
#include <linux/version.h>
fprintf(stdout, "%s", SOMETHING)
```
where SOMETHING should be #define'd in versions.h, but it doesn't. So I fixed it whit a simple fprintf(stdout, "2.6.33-14-generic") and now it finds the header files.

The next problem was <linux/config.h>, which is renamed to <config/autoconf.h> in my kernel headers. So I made a symlink to fix this.
Then there was another include error, <asm/bitops.h> which is <asm-x86_64/bitops.h> on my system. Now when I 'fixed' the #include preprocessor directive, I realysed that there were broken #includes in "bitops.h", too! So I started to edit the linux header files, although I'm not a C expert...

So, when done, I got a few errors, mostly undefined macros and macros that changed the number of arguments. So I commented out some "unnecessary" lines and compiled the module, which was, of course, useless.

Did anyone manage to compile it? I'm tired of messing around in source files, maybe there's a simple kernel patch to solve this?

PS: I also tried the Fast8x0_3-0-6 driver, which is patched for SAGEM F@st 800-840, and the official one from the SAGEM website.

I wonder if it can be done in a more Ubuntu-like way, eg. getting a precompiled module... Does anyone have a working **eagle_usb.ko**?

---

### Post by aatiis on 2007-10-27
OK, I fount a precompiled module for ueagle-atm. BTW this serbian wiki helped a lot:
[http://ubuntu-rs.org/wiki/Sagem_F%40st_800](http://ubuntu-rs.org/wiki/Sagem_F%40st_800)

---

