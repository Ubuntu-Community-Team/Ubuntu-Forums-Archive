---
title: "VMware Player- problems installing..."
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by tolstoybikeboy on 2007-06-18
Hi, I am trying to install VMware Player 2.0, on my laptop running Fiesty Fawn 7.04 64bit. Everything seems to proceed nicely until i reach the end of the install...it gives me an error about the VMnet module not being able to load on my kernel...at an earlier point in the process it said that it would try to create a custom module. it said that succeeded, however, as mentioned...once i near the end of the installation...i recieve the following error text:

-------------------------------------------------------------------------------------------------------
Extracting the sources of the vmnet module. 

Building the vmnet module. 

Using 2.6.x kernel build system. 
make: Entering directory `/tmp/vmware-config0/vmnet-only' 
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic' 
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o 
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o 
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o 
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o 
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o 
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o 
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o 
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o 
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o 
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x86_64.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o 
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o 
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic' 
cp -f vmnet.ko ./../vmnet.o 
make: Leaving directory `/tmp/vmware-config0/vmnet-only' 
Unable to make a vmnet module that can be loaded in the running kernel: 
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists 
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory. 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html". 

Execution aborted. 
-----------------------------------------------------------------------------------------------------

now, i understand it offers a "solution"...but i am an ubuntu newbie and don't know what to do.   1) rebuilding a kernel sounds scary with my lack of skill 2) on the other hand, i don't know how to "specify another directory", so that won't help either...

i tried finding an answer on the VMware forums but they are disorganized or incomprehensible to me. 

if anyone can offer help it would be greatly appreciated. i simply want to install whichever version of VMware player that will allow me to load Windows on a virtual machine....i am more than ready to scrap XP but there a few vital applications that I can only run on Windows...and i really don't like a dual-boot setup

if i have left out any info needed to diagnose issue please let me know

thanks

---

### Post by capecove on 2007-06-18
Hello! Have you checked this thread?

[http://ubuntuforums.org/showthread.php?t=460462&highlight=vmnet+module](http://ubuntuforums.org/showthread.php?t=460462&highlight=vmnet+module)

Let us know if it helps you... :)

---

### Post by dabl on 2007-06-18
You posted under "64-bit".  Are you running 64-bit Feisty?  Do you have the correct linux-headers package installed for 64-bit?  I just looked, and there is a particular version cited for my system -- it is as follows:

```
linux-headers-2.6.20-16
``` and also 
```
linux-headers-2.6.20-16-generic
```  and then it says "Installed Version" is ```
2.6.20-16.29
```

You might want to make sure you have it all current, and then try VM Player again. It's working fine on my Kubuntu Feisty (32-bit) installation.  ;)

---

### Post by tolstoybikeboy on 2007-06-18
i haven't checked those but i will.... i tried using the guide posted above...but i couldn't get the process to complete....i got to the point where you   sudo ./vmware-install.pl   but it kept telling me that the file wasn't there...so 
somehow though, after painful attempts...i have just gotten VMware Player 2.0 installed.   it works..but only if i decline to setup all those network modules...when i run the config command..i go through the wizard..and no matter what i setup..it says something like "yay, you've successfully installed vmware player...run it using " " command. but when i do...it just says that "the program is installed but not configured properly"...and the cycle continues....  i suppose i need to have those vmnet modules configured ?  i don't know...

and oh yeah... i am running the 64 bit version of feisty fawn.   my cpu is amd turion 64x2

---

### Post by dabl on 2007-06-18
Yes, after you have it installed, then you have to run ```
sudo /bin/vmware-config.pl
```  (I hope I remembered that right).  After you do that, then you can enter```
 vmplayer
``` and it will run the VM player.

---

### Post by tolstoybikeboy on 2007-06-19
thank you to capecove and dabl for your help. it was appreciated. ultimately, using the howto guide link i was able to get vmserver 1.0.3 installed but never configured properly, on the other hand i was able by my own persistence to get vmplayer 2.0 installed and configured to work.   in the end...i learned from searching that vmserver is now available to install using the synaptics package manager. you just have to manually add in the .deb repository url into the repositories list...it can be found in the ubuntu commercial archive. vmware 1.0.3 installs perfectly..no module patching..no tweaking. vmserver installed correctly for me this way
i believe the url was [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  ...the info in synaptics gave this... and said distro: feisty-commercial

---

