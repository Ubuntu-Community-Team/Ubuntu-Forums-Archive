---
title: "recompiling/patching 64-bit kernel?"
date: 2005-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by OneSeventeen on 2005-08-10
Every guide I see shows how to apt-get the kernel-package, but that doesn't seem to have a linux-source for the amd64 (it just has the linux-headers for amd64 and linux-source for normal)

Is there a guide on recompiling the kernel for the amd64?

If I try make-kpkg --append-to-version=.10082005 kernel_image --initrd binary
it starts as though all is going well, until it gives me the following:
```

echo done >  stamp-kernel-configure
echo done >  stamp-configure
test -f stamp-configure || /usr/bin/make -f /usr/share/kernel-package/rules configure
/usr/bin/make  EXTRAVERSION=.20050810.2  ARCH=x86_64 \
                     bzImage
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-generic'
  CHK     include/linux/version.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-generic'
make: *** [stamp-build] Error 2

```

I've rebuilt the kernel using linux-source-2.6.10, and it gave me: 
kernel-doc-2.6.10.20050810_10.00.Custom_all.deb
kernel-headers-2.6.10.20050810_10.00.Custom_amd64.deb
kernel-image-2.6.10.20050810_10.00.Custom_amd64.deb
kernel-source-2.6.10.20050810_10.00.Custom_all.deb

so I installed kernel-image-2.6.10.20050810_10.00.Custom_amd64.deb and my wireless networking no longer worked, and I didn't see any of the text during startup...

As it is probably obvious, this is my first attempt at kernel patching, but all I want to do now is make my current kernel myself, *then* start messing with stuff and recompiling it.

---

### Post by locutus42 on 2005-08-11
I really don't remember what packages I installed to build my amd64 kernel but you might try just getting the standard kernel-package, unpack the linux-sourcexxxxx.tgz file, copy /boot/configxxxxxx to /usr/src/linux-sourcexxxxx/.config and then run "sudo make menuconfig" in your source directory. Change the Processor type and features section, for the processor, to the K8 processor type. enter esc, esc, and save the configuration.  then build the kernel and install it.

My Sempron 3000+ seems to run as fast compiled to the K7 type as the K8 type... go figure.

---

### Post by Tamir on 2005-08-11
If you want to add/remove modules etc, just change directory to /usr/src/linux, then run: make oldconfig, make menuconfig and configure you kernel.

---

### Post by OneSeventeen on 2005-08-11
I've figured out how to use make menuconfig and whatnot, but I copied the config file from /boot to /usr/src/linux/.config and after compiling, I would assume things should work the same, since I made no changes to the .config file.

My wireless stopped working, so I was assuming I should have been using a different linux source?  or are they all the same?

It just seems odd to me that compiling with the same config as my existing system would come up with something different than what I already have.

I am recompiling it now after configuring the hell out of it using xconfig, we'll see if the wireless card works now, and if not, I'll probably post a lot of questions here... I just really don't want to have to switch back to windows, but if I can't patch the kernel without loosing wireless capabilities, then I don't have much choice :(

---

### Post by locutus42 on 2005-08-11
[QUOTE=Tamir]If you want to add/remove modules etc, just change directory to /usr/src/linux, then run: make oldconfig, make menuconfig and configure you kernel.[/QUOTE]

yes but if your just want to see if you can build a copy of the distribution kernel, you don't need "make oldconfig" and "make menuconfig" and anybody building the kernel for the first time shouldn't be in the config file until they know what's going on. Or atleast knows how to get back to a working starting point.

---

### Post by locutus42 on 2005-08-11
[QUOTE=OneSeventeen]I've figured out how to use make menuconfig and whatnot, but I copied the config file from /boot to /usr/src/linux/.config and after compiling, I would assume things should work the same, since I made no changes to the .config file.

My wireless stopped working, so I was assuming I should have been using a different linux source?  or are they all the same?[/QUOTE]

a new kernel build will create a new /lib/modules/yourKernelName directory tree for all the modules built for the kernel. It's one of the reasons why you need to reinstall/build the ATI driver when you change kernels.

It could be that your wireless card driver was installed after your system install and so the new kernel does not have the driver to load. ?  If you have a pure Ubuntu installation, and build another kernel with the default config file from /boot, then you should get a copy of the original kernel. Or, something wasn't done as expected.


[QUOTE=OneSeventeen]I am recompiling it now after configuring the hell out of it using xconfig, we'll see if the wireless card works now, and if not, I'll probably post a lot of questions here... I just really don't want to have to switch back to windows, but if I can't patch the kernel without loosing wireless capabilities, then I don't have much choice :([/QUOTE]
IMO, this is asking for trouble since you have no idea what your starting point is. If you are doing something wrong with a default kernel compile, tweaking your kernel settings randomly isn't going to get you anywhere but lost.

May I suggest you go back to building a default kernel and figure out what went wrong. THEN, jump into changing things piece by piece. Atleast you'll know when you change something whether it fixed or broke what you intended to change. ](*,)

---

### Post by OneSeventeen on 2005-08-11
[QUOTE=locutus42]a new kernel build will create a new /lib/modules/yourKernelName directory tree for all the modules built for the kernel. It's one of the reasons why you need to reinstall/build the ATI driver when you change kernels.

It could be that your wireless card driver was installed after your system install and so the new kernel does not have the driver to load. ?  If you have a pure Ubuntu installation, and build another kernel with the default config file from /boot, then you should get a copy of the original kernel. Or, something wasn't done as expected.



IMO, this is asking for trouble since you have no idea what your starting point is. If you are doing something wrong with a default kernel compile, tweaking your kernel settings randomly isn't going to get you anywhere but lost.

May I suggest you go back to building a default kernel and figure out what went wrong. THEN, jump into changing things piece by piece. Atleast you'll know when you change something whether it fixed or broke what you intended to change. ](*,)[/QUOTE]
 Yeah, it was just a last effort to mess with stuff and see what it does.  I think I'll boot the first kernel I made, reinstall ndiswrapper, and see if I can get the wireless interface working again.

If I can, then I'll work on patching the kernel with all of the stuff that should get DMA working, drop my CPU usage to zero during idle, and set the clock to run at a normal rate.

If I can't, then I may just switch over to a 32-bit version instead...

---

### Post by locutus42 on 2005-08-11
[QUOTE=OneSeventeen]Yeah, it was just a last effort to mess with stuff and see what it does.  I think I'll boot the first kernel I made, reinstall ndiswrapper, and see if I can get the wireless interface working again.

If I can, then I'll work on patching the kernel with all of the stuff that should get DMA working, drop my CPU usage to zero during idle, and set the clock to run at a normal rate.

If I can't, then I may just switch over to a 32-bit version instead...[/QUOTE]

hint 1: "lsmod" will dump a listing of your loaded kernel modules
hint 2: "lsmod | grep ndiswrapper" will display any modules listing with the ndiswrapper name in it. Ie, if the module is installed, it'll show up after the command.

It does make sense that the ndiswrapper would not work after installing and running a new kernel since ndiswrapper does require a kernel driver module to run. And now you know that you get a new kernel module hierarchy with a new kernel... 
I think you'll be working on patching last couple of issues pretty soon.

---

