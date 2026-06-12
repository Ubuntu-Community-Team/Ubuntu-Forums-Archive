---
title: "Help with lirc module/2.6.30 kernel"
date: 2009-07-13
forum: x86 64-bit Users
---

### Post by kwisher on 2009-07-13
Hello,

I have just installed 64-bit Mint-7/Jaunty on my MythTV system for the added support for my TV tuner cards. I manually installed the new kernel by following the instructions from this thread on the Mint forums:

[http://forums.linuxmint.com/viewtopic.php?f=58&t=27963&st=0&sk=t&sd=a]("http://forums.linuxmint.com/viewtopic.php?f=58&t=27963&st=0&sk=t&sd=a")

I then installed the latest nVidia driver. All is working correctly except my USB infrared reciever and remote control. It seems the driver module was not installed during the kernel update.

Can someone please advise?

TIA

---

### Post by Yellow Pasque on 2009-07-13
Try (re)installing lirc-modules-source

---

### Post by kwisher on 2009-07-13
> **Temüjin said:**
> Try (re)installing lirc-modules-source

That did not work. Tried the code below:

```
# dpkg-reconfigure lirc-modules-source
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build

Error!  Build of lirc_cmdir.ko failed for: 2.6.30-020630-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.4a/build/ for more information.
Installing initial module

Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree.
You must run a dkms build for kernel 2.6.30-020630-generic (x86_64) first.
Done.

```

---

### Post by DesertF0x on 2009-07-25
Same problem for me with 32-Bit Jaunty and 2.6.30 Kernel. Seems like lirc is not working with 2.6.30 yet.

---

