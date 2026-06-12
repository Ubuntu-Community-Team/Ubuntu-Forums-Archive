---
title: "Help me get mol working..."
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eleaf on 2005-11-22
Hi, I'm having very vast problems trying to get Mac on Linux to get working on my iBook. I have downloaded all of the mol stuff, the modules and everything like that, and then it says I need a properly configure kernel source when I try and compile the mol modules. Ok, so I download the linux-source and compile it and everything using the instructions from [https://wiki.ubuntu.com/KernelBuildPPCHowTo?highlight=%28kernel%29](https://wiki.ubuntu.com/KernelBuildPPCHowTo?highlight=%28kernel%29) . This however does nothing and it still complains that ```
 --- Error: Unconfigured kernel source! --- (missing file: /include/linux/config.h) 
``` I have no idea what to do at all! I cannot find any instructions anywhere on what to do. I have been trying to figure this out for a few months now. I just don't understand what to do, I think there should be better instructions how to get this to work. Does anybody know what I need to do next? Please??

---

### Post by Eleaf on 2005-11-22
HHHHeeeeelllppp! lol
On restart, I was able to get it to see the kernel source I beleive when I compiled the mol modules.  So I compile the module, but startmol still complains that there is no mol kernel module!

I'm stuck with what to do.... = -S

---

### Post by tmeier on 2005-11-22
Have you tried this wiki : [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto)

I found this to be very helpful.  One thing I found when doing MOl, was that I did not have the M4 modules installed, which I did through synaptic and then everything started working on the Howto.

---

### Post by Eleaf on 2005-11-22
I have m4 installed.  This is where it messes up though.  When I put in the command  ```
   bash:/usr/src$ cd modules/mol
   bash:/usr/src/modules/mol$ sudo debian/rules build
```
It says make:nothing to be done for 'build'.

This is the part where it messes up, it just won't build it there.  If I say "make", it works fine but that doesn't work in the and and is not not what the wiki guide says to do.

I'm confused...

---

### Post by tmeier on 2005-11-23
[QUOTE=Eleaf]
   bash:/usr/src/modules/mol$ sudo debian/rules build[/CODE]
It says make:nothing to be done for 'build'.

[/QUOTE]

To get it to build again, you have to
sudo rm build-stamp
This deletes the stamp that says you already ran a build.  I had to go through that many times before I finally got it to work.

---

### Post by Eleaf on 2005-11-23
[QUOTE=tmeier]To get it to build again, you have to
sudo rm build-stamp
This deletes the stamp that says you already ran a build.  I had to go through that many times before I finally got it to work.[/QUOTE]

That didn't do anything....

---

### Post by Eleaf on 2005-11-23
Here are the 'errors' I get when compiling...
```
ethan@ethanlofton:/usr/src/modules/mol$ sudo rm build-stamp
rm: cannot remove `build-stamp': No such file or directory
ethan@ethanlofton:/usr/src/modules/mol$ sudo make
make -C src/kmod
make[1]: Entering directory `/usr/src/modules/mol/src/kmod'
+ Entering Linux
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[4]: scripts/Makefile.build: No such file or directory
make[4]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[3]: *** [_module_/usr/src/modules/mol/src/kmod/Linux/../build] Error 2
    Kernel source                 : /usr/src/linux-headers-2.6.12-9
    Module compiled for           : 2.6.12
    Running kernel                : 2.6.12
install -d ../../../mollib/modules/`cat ../build/.kuname`
ln -f ../build/mol.ko ../../../mollib/modules/`cat ../build/.kuname`/
make[1]: Leaving directory `/usr/src/modules/mol/src/kmod'
make -C src/netdriver
make[1]: Entering directory `/usr/src/modules/mol/src/netdriver'
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[3]: scripts/Makefile.build: No such file or directory
make[3]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[2]: *** [_module_/usr/src/modules/mol/src/netdriver/build] Error 2
make[1]: Leaving directory `/usr/src/modules/mol/src/netdriver'
ethan@ethanlofton:/usr/src/modules/mol$ sudo make modules-install
make: *** No rule to make target `modules-install'.  Stop.
ethan@ethanlofton:/usr/src/modules/mol$


```

Heeelllppp...

---

### Post by Ptero-4 on 2005-11-23
did you install the kernel source (linux-image IIRC)? It may be missing from your system. Also install debhelper to be sure that it'll work. If it doesn't work just ask in the forums. There's a guy that is hosting precompiled kmods for 4.10 , 5.04 and 5.10.

---

### Post by trash on 2005-12-12
> **Eleaf]Here are the 'errors' I get when compiling...
```
ethan@ethanlofton:/usr/src/modules/mol$ sudo rm build-stamp
rm: cannot remove `build-stamp': No such file or directory
ethan@ethanlofton:/usr/src/modules/mol$ sudo make
make -C src/kmod
make[1]: Entering directory `/usr/src/modules/mol/src/kmod'
+ Entering Linux
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
           is missing said:**
> : scripts/Makefile.build: No such file or directory
make[4]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[3]: *** [_module_/usr/src/modules/mol/src/kmod/Linux/../build] Error 2
    Kernel source                 : /usr/src/linux-headers-2.6.12-9
    Module compiled for           : 2.6.12
    Running kernel                : 2.6.12
install -d ../../../mollib/modules/`cat ../build/.kuname`
ln -f ../build/mol.ko ../../../mollib/modules/`cat ../build/.kuname`/
make[1]: Leaving directory `/usr/src/modules/mol/src/kmod'
make -C src/netdriver
make[1]: Entering directory `/usr/src/modules/mol/src/netdriver'
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[3]: scripts/Makefile.build: No such file or directory
make[3]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[2]: *** [_module_/usr/src/modules/mol/src/netdriver/build] Error 2
make[1]: Leaving directory `/usr/src/modules/mol/src/netdriver'
ethan@ethanlofton:/usr/src/modules/mol$ sudo make modules-install
make: *** No rule to make target `modules-install'.  Stop.
ethan@ethanlofton:/usr/src/modules/mol$


```

Heeelllppp...

I just got MOL up and running using the same wiki howto, did you copy/paste the kernel version in the wiki, for me uname -r is 2.6.12-10-powerpc(breezy), i see you're using 2.6.12-9.. just figured i'd ask.

off topic, anybody getting mol @ 97-100% cpu usage?

---

### Post by pvz on 2005-12-12
[QUOTE=Ptero-4]There's a guy that is hosting precompiled kmods for 4.10 , 5.04 and 5.10.[/QUOTE]
[http://www.petrvz.net/~pvz/mol/](http://www.petrvz.net/~pvz/mol/)

---

