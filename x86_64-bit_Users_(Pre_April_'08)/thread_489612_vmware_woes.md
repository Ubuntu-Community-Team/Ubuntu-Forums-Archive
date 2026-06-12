---
title: "vmware woes"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by r_rehashed on 2007-07-01
hi all.

i downloaded Vmware-server (1.0.3) and installed it. however i am having problems in configuring it.
here's the message. it's pretty long, please excuse me.

> 
/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Also i want to run Windows 98 as the guest OS. will it run on the core-2-duo? I am running 64-bit Feisty.

Any help is greatly appreciated.

---

### Post by insane_alien on 2007-07-01
either download the anypatch(google it) or add the canonical commercial repo and install it through apt-get.

win98 runs on a virtual machine on a core-2-duo. i'm running it just now.

---

### Post by janbockaert on 2007-07-01
If you just are gonna use vmware to run windows inside ubuntu, you should take a look at virtualbox. I believe virtualbox is actually a better sollution, and it never fails an installation. They offer a .deb for ubuntu, and have no problems running on 64 bit.

[www.virtualbox.org](www.virtualbox.org)

---

### Post by jespdj on 2007-07-02
How are you trying to install and configure VMWare? Are you using Canonical's Ubuntu package or are you trying to install and configure it manually?

I used the following instructions and it works without a problem. I'm running Windows XP SP2 (32-bit) on Ubuntu 7.04 (64-bit).

Link: [How to install Vmware server From Canonical commercial repository in Ubuntu Feisty](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

