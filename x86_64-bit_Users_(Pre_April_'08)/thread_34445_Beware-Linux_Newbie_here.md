---
title: "Beware-Linux Newbie here"
date: 2005-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by asbestos on 2005-05-14
I just got a nice new laptop (emachines m6809 AMD64 3200+) and I am itching to try out a 64 bit OS. I have messed around with Linux live cd's for a while but I never have had a wireless card that actually works for Linux.

I downloaded the dvd live/install and set it up. It worked great!

Ok, that was a lie. In the repository I could not find anything about ndiswrapper so I can get my card working. Is this a 64bit issue?

My normal hardwired network card works fine so that will do for now I guess, but I would really like to get it working.

Here is what I did so far:

I downloaded the latest ndiswrapper and followed some instructions from this forum to the T but I kept getting errors when trying to compile it.

Any tips? Should I spend a week or so reading up about Linux before trying something like this? ( I am not opposed to this at all, in fact I would love to get more comfortable with linux)

---

### Post by nad on 2005-05-14
Sounds like you are enjoying yourself. Welcome to the club. You may try this link for starters:

[http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto)

---

### Post by asbestos on 2005-05-14
Following a thread right now... Here is the link to what I am doing:

[http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto)

And the error message I get:

make -C /lib/modules/2.6.10-5-amd64-k8/build SUBDIRS=/home/asbestos/ndiswrapper-1.2rc1/driver \
        NDISWRAPPER_VERSION=1.2rc1 \
        EXTRA_VERSION= modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-k8'
  CC [M]  /home/asbestos/ndiswrapper-1.2rc1/driver/hal.o
/bin/sh: gcc: command not found
make[3]: *** [/home/asbestos/ndiswrapper-1.2rc1/driver/hal.o] Error 127
make[2]: *** [_module_/home/asbestos/ndiswrapper-1.2rc1/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-k8'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/asbestos/ndiswrapper-1.2rc1/driver'
make: *** [all] Error 2
asbestos@asb:~/ndiswrapper-1.2rc1$ sudo make install
make -C driver install
make[1]: Entering directory `/home/asbestos/ndiswrapper-1.2rc1/driver'
make -C /lib/modules/2.6.10-5-amd64-k8/build SUBDIRS=/home/asbestos/ndiswrapper-1.2rc1/driver \
        NDISWRAPPER_VERSION=1.2rc1 \
        EXTRA_VERSION= modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-k8'
  CC [M]  /home/asbestos/ndiswrapper-1.2rc1/driver/hal.o
/bin/sh: gcc: command not found
make[3]: *** [/home/asbestos/ndiswrapper-1.2rc1/driver/hal.o] Error 127
make[2]: *** [_module_/home/asbestos/ndiswrapper-1.2rc1/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-k8'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/asbestos/ndiswrapper-1.2rc1/driver'
make: *** [install] Error 2
asbestos@asb:~/ndiswrapper-1.2rc1$

---

### Post by nad on 2005-05-15
/bin/sh: gcc: command not found

In order to compile source code you need... a compiler.

Please install the build-esentials package. I see that you have the kernel-headers package so you are halfway there.

---

### Post by asbestos on 2005-05-15
I am getting close!!! I got it to fire up, mostly..

Now, the problem I am having is odd.

I go to the network settings in the control panel, go to admin mode but it doesnt give me the options (it puts me to a screen with all the options for networking)

I went into kynaptic and it asks for the root pw there, so I entered it. It said something about dcopserver not running...

---

### Post by nad on 2005-05-15
You've got me!

I'm a hardwired, operating systems and hardware gnome geek. Read any documents that came with the driver and search these forums for issues and setting up your wireless connection with kubuntu.

---

