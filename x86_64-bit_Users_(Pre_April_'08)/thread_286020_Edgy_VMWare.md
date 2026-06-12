---
title: "Edgy VMWare?"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by FluffyElmo on 2006-10-27
Does anyone have VMWare player running under Edgy? I've run the vmware-config.pl script as usual for a kernel change but it fails to compile the kernel module. Errors below, any help appreciated.

```

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running 
kernel? [/lib/modules/2.6.17-10-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:62: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.



```

---

### Post by FluffyElmo on 2006-10-27
I was able to install VMWare Server and run my VM from there so this isn't an emergency. I'd still like to get the Player working though as I prefer it for what I need. 

Also, while there are other people having Edgy/VMWare-Player problems they don't seem to have any trouble compiling the kernel module so I'm thinking that is an AMD64 issue?

---

### Post by Mongoose on 2006-10-27
I just installed the new vmware player package the required kernel module was installed.  Look for an upgradable package in synaptic.

 1.0.2 build-29634
 2.6.17-10-generic

Edit:

vmware-player
vmware-player-kernel-modules-2.6.17-10

---

### Post by FluffyElmo on 2006-10-27
Cool, I didn't know it was in the repositories. The latest from the VMWare site is 1.0.1. The downloaded player doesn't recognize the repository headers so I guess I have to install the player from there too.

When I try to install the Player it wants to remove some packages I use (Nautilus CD-Burning) so I may stick with Server for now but will investigate when I have more time.

In any case, thanks! At least there is a working solution when I need it.

---

### Post by Mongoose on 2006-10-27
Nautilus cd/dvd burner should still work, since I assume you mean the removal of the obsolete lib packages.  If you want to confirm without installing first look at the dependenices for the new nautilus packages.  It should confirm you don't need the obsolete libs anymore.  ;)

---

