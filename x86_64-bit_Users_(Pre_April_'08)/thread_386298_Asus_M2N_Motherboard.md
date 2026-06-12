---
title: "Asus M2N Motherboard"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by justin on 2007-03-16
I recently built a new computer using a Asus M2N motherboard.

[http://www.newegg.com/product/product.asp?item=N82E16813131042]("http://www.newegg.com/product/product.asp?item=N82E16813131042")

Unfortunately, the onboard sound and lan are not being detected by Edgy (or by openSuse 10.2)

Any ideas on how I can get them up and running?

---

### Post by 8 Ball on 2007-03-16
I have an Asus M2V. Check your drivers cd that came with it and they should be in the Linux folder.

---

### Post by justin on 2007-03-16
There's only an audio driver, no driver for lan.

---

### Post by h3_ on 2007-08-12
I installed Feisty on a brand new PC with a Asus M2N-MX motherboard and I ran into lots of problems. I though that having a 3 generations old motherboard would save me some hassles .. how naive.

In summary this is my install log:


1: First attempt the live CD crashes at first loading screen. The system doesn't like ACPI, disabling it resolved this issue (in a somewhat non-green way).

2: I finally boot the live CD and install feisty flawlessly, but when I first boot up the network interface act really weird, I can't get the DHCP working, when I try to set static IP I can ping my laptop but not my router .. ? And the only way to get internet is direct PPPOE. (I still hasn't find nothing on this, for the moment my main suspect is avahi).

3: The audio don't work at all, I just get an intolerable high pitch sound.

4: Restricted drivers modules tells me that my nvidia 8600GT doesn't need restricted drivers and won't install them. I had to install them manually.

6: The amount of bugs I face discourage me, so I decide to give Edgy a try. The live CD
freeze at the first progress bar .. with ACPI disabled..

7: After hours of trials error I came to the conclusion that I might be lucky and fix some bug by upgrading my kernel to 2.6+. I installed 2.6.22-9-generic, surprise ! Now the system boot with ACPI enabled, I still havn't really tested it yet but it seems to work. The sounds too started working, but with major glitches. And I still have the same problems with my network. Oh, and now when my LCDs goes to sleep, my secondary does wake up, but it only draws the mouse cursor, not the windows.. in fact, everything is black except the cursor.

Another annoying thing, I never been able to compile the Nforce drivers provided by nvidia, I always get the same errors,, I have tried to force gcc-3.4 then 4.1, specify kernel version, no results, Here's my nvidia-nforce-installer.log:

```

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sun Aug 12 19:10:05 2007

option status:
  license pre-accepted      : true
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : /usr/src/linux-headers-2.6.22-9-generic
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
   NVIDIA network driver for Linux-x86 (1.0-13)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted by command line option.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.22-9-generic (buildd@palmer) (gcc version
   4.1.3 20070718 (prerelease) (Ubuntu 4.1.2-14ubuntu1)) #1 SMP Fri Aug 3
   00:50:37 GMT 2007
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/usr/src/linux-headers-2.6.22-9-generic' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.22-9-generic'
-> Kernel output path: '/lib/modules/2.6.22-9-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /usr/src/linux-headers-2.6.22-9-generic/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/usr/src/linux-headers-2.6
   .22-9-generic SYSOUT=/lib/modules/2.6.22-9-generic/build'...
   make -C /lib/modules/2.6.22-9-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.22-9-generic \
   	KBUILD_EXTMOD="/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
   " -f /usr/src/linux-headers-2.6.22-9-generic/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_v
   ersions
   rm -f /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_vers
   ions/*
   make -f /usr/src/linux-headers-2.6.22-9-generic/scripts/Makefile.build obj=/
   tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.n
   valinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D
   __KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.22-9-generic/in
   clude -include include/linux/autoconf.h  -I/tmp/selfgz18476/NFORCE-Linux-x86
   -1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs
   -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-st
   ruct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreest
   anding -maccumulate-outgoing-args -I/usr/src/linux-headers-2.6.22-9-generic/
   include/asm-i386/mach-default -Iinclude/asm-i386/mach-default -fomit-frame-p
   ointer -g -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-si
   gn  -I/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wi
   mplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpo
   inter-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHA
   NGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /tmp/selfgz18
   476/NFORCE-Linux-x86-1.0-0
   310-pkg1/nvsound/main/.tmp_nvalinux.o /tmp/selfgz18476/NFORCE-Linux-x86-1.0-
   0310-pkg1/nvsound/main/nvalinux.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:10,
                    from /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsoun
   d/main/nvalinux.c:19:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c: In 
   function &#8216;AosFpuSave&#8217;:
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:181:
   error: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:191:
   error: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:214:
   error: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c: In 
   function &#8216;AosFpuRestore&#8217;:
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:234:
   error: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:235:
   error: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   make[4]: *** [/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/n
   valinux.o] Error 1
   make[3]: *** [_module_/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvsoun
   d/main] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> License accepted by command line option.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.22-9-generic (buildd@palmer) (gcc version
   4.1.3 20070718 (prerelease) (Ubuntu 4.1.2-14ubuntu1)) #1 SMP Fri Aug 3
   00:50:37 GMT 2007
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/usr/src/linux-headers-2.6.22-9-generic' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.22-9-generic'
-> Using the kernel output path '/lib/modules/2.6.22-9-generic/build' as
   specified by the '--kernel-output-path' commandline option.
-> Kernel output path: '/lib/modules/2.6.22-9-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /usr/src/linux-headers-2.6.22-9-generic/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvnet.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvnet; make clean'...
   rm -f *.ko *mod.* *.cmd nvenet.o nvenetif.o nvnet.o *~ core
-> Building kernel module:
   executing: 'cd ./nvnet; make module SYSSRC=/usr/src/linux-headers-2.6.22-9-g
   eneric SYSOUT=/lib/modules/2.6.22-9-generic/build'...
   make -C /lib/modules/2.6.22-9-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.22-9-generic \
   	KBUILD_EXTMOD="/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet" -f /u
   sr/src/linux-headers-2.6.22-9-generic/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/.tmp_versions
   rm -f /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/.tmp_versions/*
   make -f /usr/src/linux-headers-2.6.22-9-generic/scripts/Makefile.build obj=/
   tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet
     cc -Wp,-MD,/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/.nvenet.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL_
   _ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.22-9-generic/include -in
   clude include/linux/autoconf.h  -I/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310
   -pkg1/nvnet -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-ali
   asing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args -I/usr/src/linux-headers-2.6.22-9-generic/include/asm-i38
   6/mach-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-
   stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DDRIVERVER=
   \"9999\"  -I/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet -Wall -Wim
   plicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoi
   nter-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DMODULE 
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvenet)"  -D"KBUILD_MODNA
   ME=KBUILD_STR(nvnet)" -c -o /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/
   nvnet/.tmp_nvenet.o /tmp/selfgz18476/NFORCE-Linux-x86-1
   .0-0310-pkg1/nvnet/nvenet.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:10,
                    from /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/
   nvenet.h:20,
                    from /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/
   nvenet.c:22:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/
   nvenet.c:22:
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.h:21:26: error:
   linux/config.h: No such file or directory
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c: At top level
   :
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:217: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:220: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:223: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:226: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:229: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:232: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:235: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:238: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:241: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:244: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:247: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:250: error: e
   xpected &#8216;)&#8217; before string constant
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:336: warning:
   initialization from incompatible pointer type
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c: In function 
   &#8216;nvenet_open&#8217;:
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:738: warning:
   &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt
   .h:66)
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:738: warning:
   passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c: In function 
   &#8216;nvenet_xmit&#8217;:
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:1218: error: 
   &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:1218: error: 
   (Each undeclared identifier is reported only once
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:1218: error: 
   for each function it appears in.)
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:1224:5: warni
   ng: "SKB_GSO_TCPV4" is not defined
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c: In function 
   &#8216;nvenet_init_module&#8217;:
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:1325: warning
   : implicit declaration of function &#8216;pci_module_init&#8217;
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c: In function 
   &#8216;proc_fill_hardware_info&#8217;:
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:3247: warning
   : format &#8216;807f8e8&#8217; expects type &#8216;long unsigned int&#8217;, but argument 6 
   has type &#8216;resource_size_t&#8217;
   /tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:3250: warning
   : format &#8216;134740200&#8217; expects type &#8216;long int&#8217;, but argument 6 has typ
   e &#8216;resource_size_t&#8217;
   make[4]: *** [/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.o
   ] Error 1
   make[3]: *** [_module_/tmp/selfgz18476/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet]
   Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.

```

Somewhere it says "Run 'make oldconfig && make prepare' on kernel src to fix it", It doesn't work, I won't paste the whole command ouput here since it's quite big, but it ends like this:

```

CRC32c (Castagnoli, et al) Cyclic Redundancy-Check (LIBCRC32C) [M/y/?] m
#
# configuration written to .config
#
scripts/kconfig/conf -s arch/i386/Kconfig

*** Error during writing of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.

```

I installed ubtuntu lots of times on many PCs, I never had that much troubles. I guess I picked up the wrong board. 

This is definitely my worst ubuntu experience ever, after 3 days of messing around with every possible configs and countless reinstalls, I still have a half working/unstable system.

desesparatly yours, 

h3.

UPDATE: I installed Gutsy to see if my drivers a better supported. I had less troubles, but I still have the same problem with my network card.. no DHCP, can ping other computers but not the router or the internet. I also found out that the nForce drivers is only for 2.4.* kernels, hell.

---

### Post by nss0000 on 2007-08-13
Yes, the onboard ETHport and sound_chip are well known problems with the ASUS_m2n mobos. Likewise LM_Sensors.

No need to suffer. I've been running DAPPERx64 for several months on AMD5400+/ASUS-m2n kit. I use a legacy NIC-card and SB16 workalike without issue. LMS == SOL.

Otherwise kit + OS behave admirably.

---

### Post by ender8282 on 2007-08-16
I have also been trying to get kubuntu (fiesty) running with the M2N-MX mobo.  I have had some issues.  
I have not yet gotten sound working.  
The lan worked out of the box.  
I think that some of my problems were with the onboard graphics.  When I bought a cheap nVidia graphics card it installed (I had to install the nvidia drivers to get it to support my wide screen display)
It would be awsome if we get all of the information together and create a HowTo for this mobo.
I don't really know enough to get all of this stuff working myself but I am happy to help any way that I can.

---

### Post by h3_ on 2007-08-16
> **ender8282 said:**
> I have also been trying to get kubuntu (fiesty) running with the M2N-MX mobo.  I have had some issues.  
I have not yet gotten sound working.  
The lan worked out of the box.  
I think that some of my problems were with the onboard graphics.  When I bought a cheap nVidia graphics card it installed (I had to install the nvidia drivers to get it to support my wide screen display)
It would be awsome if we get all of the information together and create a HowTo for this mobo.
I don't really know enough to get all of this stuff working myself but I am happy to help any way that I can.

I have to say that as surprising as it sound, I run the 64 bit version of Gutsy and it's  very stable and it's damn fast. The sounds is A1, I had some noise problems but turns out it was my cables.

I installed and compiled the latest Nvidia drivers (I don't use the cheap onboard card btw), Since I run the development version of Ubuntu I have to recompile my drivers quite often because most updates breaks them, but with a system that fast it takes me about 2min .. restart included :)
 
I even got flash working flawlessly with nswrapper :)

The only things that really don't work is the desktop effects. First time I installed Nvidia drivers they worked, but I tried to enabled advanced effects and I got an error message telling me that no Nvidia card was found, I tried to disable it but now I can't re-enable them.. I get the same error message. Anyway, desktop effects never worked for me out of the box, I always had to install beryl.

Cheers.

---

