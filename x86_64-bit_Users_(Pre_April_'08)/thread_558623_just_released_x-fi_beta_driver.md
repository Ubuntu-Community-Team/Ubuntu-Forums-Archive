---
title: "just released x-fi beta driver"
date: 2007-09-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by whoop on 2007-09-24
I just thought I would inform everyone of the just released x-fi beta driver from creative labs ([http://connect.creativelabs.com/linux/FAQ/Home.aspx](http://connect.creativelabs.com/linux/FAQ/Home.aspx))

I tried getting it to work but the installer said:

This product only support 64-bit Operating Systems
Setup will now exit

although I am running 64 bit

---

### Post by MrHippocampus on 2007-09-24
Release notes:
> This download is a beta driver providing Linux® 64-bit OS support for Creative Sound Blaster® X-Fi&#8482; series audio devices. For more details, read the rest of this web release note.

Take note of the following:

    * THIS IS AN UNSUPPORTED BETA DRIVER. There is no technical support for this driver.
    * We recommend that only experienced users install this driver. Do not install this driver on a system used to perform critical tasks.
    * Your feedback is a valuable part of our development process. To submit feedback on this driver, visit the Sound Blaster X-Fi Linux Beta Driver Feedback Program.

This download is intended for the following audio devices only:

    * Creative Sound Blaster X-Fi Elite Pro 
    * Creative Sound Blaster X-Fi Platinum
    * Creative Sound Blaster X-Fi Fatal1ty®
    * Creative Sound Blaster X-Fi XtremeGamer
    * Creative Sound Blaster X-Fi XtremeMusic

Current release features:

    * ALSA PCM Playback
    * ALSA MIDI Playback
    * ALSA Synth
    * ALSA Record
    * ALSA Mixer

Known issues:

    * This driver source will not compile with GCC version 4 and above.
    * S/PDIF passthrough is not supported in this driver release.
    * External I/O modules are not supported in this driver release.
    * Applications from the original Sound Blaster X-Fi Installation CD will not work with this driver.

Requirements:

    * Linux x86_64 OS
    * Creative Sound Blaster X-Fi audio devices listed above.

Notes:

    * To install the driver, do the following:
         1. Download the XFiDrv_Linux_US-1.04.tar.gz package onto your local hard disk.
         2. Double-click the downloaded package to unpack its contents.
         3. Read the README file and follow the instructions.

Looks like the important one in there is "This driver source will not compile with GCC version 4 and above."

edit:
In response to your problem whoop, open the "installer" and change the line:
```
platform=$(uname -i) 
```
to
```
platform=$(uname -m)
```
thanks go to [this]("http://forums.gentoo.org/viewtopic-t-587921-highlight-xfi.html") gentoo forums thread

---

### Post by whoop on 2007-09-24
Thanks MrHippocampus, that worked. Although I get an error now :-(

```

Installation is in progress. Please wait...
tar: XFiDrv_Linux_US-1.04: time stamp 2009-09-20 08:31:00 is 62784904.478325 s in the future
/opt/Creative/XFiDrv_Linux_US-1.04
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /opt/Creative/XFiDrv_Linux_US-1.04
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.20-16-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.20-16-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler: gcc 4.1.2 (Ubuntu 4.1.2-0ubuntu4) Used compiler: gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for exported symbol dump_stack... grep: /lib/modules/2.6.20-16-generic/build/kernel/ksyms.c: No such file or directory
no
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for processor type... x86_64
checking for SMP... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for old kill_fasync... no
checking for dma_addr_t... no
checking for MUTEX macros... no
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... yes
checking for Procfs support... yes
configure: creating ./config.status
config.status: creating Makefile.conf
cd /tmp/xfisrc/src/utils/alsaver; make clean
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/utils/alsaver'
rm -f alsaver
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/utils/alsaver'
rm -f alsaver
cd /tmp/xfisrc/src/ossrv; make clean
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/ossrv'
rm -rf ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/ossrv'
rm -f ctossrv.o
cd /tmp/xfisrc/src/emupia; make clean
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/emupia'
rm -rf emupia_guids.o emupia_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/emupia'
rm -f emupia.o
cd /tmp/xfisrc/src/sfman; make clean
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/sfman'
/tmp/xfisrc/src/sfman/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -I../../include -isystem /lib/modules/2.6.20-16-generic/build/include -I/lib/modules/2.6.20-16-generic/build/include/asm/mach-default -I/lib/modules/2.6.20-16-generic/build/include  -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -D__CT_BOUND_64BIT -M ctsfman_main.c   > .depend
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/kobject.h:25,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:17,
                 from ctsfman_main.c:17:
/lib/modules/2.6.20-16-generic/build/include/linux/rwsem.h:24:65: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from ctsfman_main.c:18:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:269:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
make[1]: *** [.depend] Error 1
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.04/src/sfman'
make: *** [ctsfmanclean] Error 2
Copy module files...
cp: cannot stat `ctossrv.o': No such file or directory
cp: cannot stat `emupia.o': No such file or directory
cp: cannot stat `ctsfman.o': No such file or directory
cp: cannot stat `haxfi.o': No such file or directory
cp: cannot stat `ctalsa.o': No such file or directory
cp: cannot stat `ct20xut.o': No such file or directory
cp: cannot stat `ctexfifx.o': No such file or directory
cp: cannot stat `cthwiut.o': No such file or directory
make: *** [copy_modules] Error 1
Installation Unsuccessful

```

---

### Post by whoop on 2007-09-24
Oops, it's using gcc 4.1.2. Looks like ubuntu 4.07 will not accept this driver :-(

---

### Post by krol on 2007-09-25
Did anyone manage to compile this driver on Ubuntu or any other distro?

---

### Post by whoop on 2007-09-25
From what I have gathered it can only be compiled on distros that are about two years old, partially due to the gcc compatibillity problem. 

This makes this driver absolutly useless in my opinion.

It looks like Creative just had a two year old driver attempt lying around and put it online.

This driver should really not carry the beta tag as it is far far from it.

---

### Post by waldorsockbat on 2007-09-25
I am soooo Pi@@$# that I cant see straight. I have been waiting forever to finally get a driver for my x-fi which was the only thing holding me back from linux full time  and this pos is the best  creative could come up with.. a 64 bit only driver that will only compile on a 2 year or older os. Who the hell even put out a 64 bit distro 2 years ago? Creative has now moved into a tie with Micro$oft as my most hated companys!!!:mad::mad::mad:

---

### Post by whoop on 2007-09-25
I'm not sure how literally you should take my two year statement, waldorsockbat. I just made the assumption because gcc 4.x has been available since April 2005.
Thus it would seem logically that any source created to be compilable with gcc < 4 has it's main base created around that period.

This all is just speculation and does not change the fact that this beta driver is a useless peace of vaporware.

O well, I'm just back to using my onboard sound adapter :(

---

### Post by John.Michael.Kane on 2007-09-25
gcc-3.3, and gcc-3.4 are the repos.
```
gksudo aptitude install "the gcc version you need"
``` 
Make sure you install any other needed dependencies.

You should then be able to configure the driver by passing the command to specifying the gcc version doing configure.

---

### Post by whoop on 2007-09-25
just thought I'd inform you that demik has managed to change the source so it is compilable with recent kernel and gcc. His rig: Kernel 2.6.22, gcc 4.2.1

You can find his creation here: [http://blackbox.lostwave.net/x-fi/](http://blackbox.lostwave.net/x-fi/)

I found this info on the gentoo forum ([http://forums.gentoo.org/viewtopic-p-4285346.html#4285346](http://forums.gentoo.org/viewtopic-p-4285346.html#4285346)). I have not tried it out myself yet.

---

### Post by JackyOH on 2007-09-26
I've tried it ...

```

sudo make install
Copy module files...
Update module dependency relationships...
Warning: Can't not find blacklist file /etc/hotplug/blacklist
Install libs...
Install database files...
tar: creative/data/ctp073aw.dat: time stamp 2009-09-17 09:25:02 is 62363985.774134 s in the future
tar: creative/data/ctp055aw.dat: time stamp 2009-09-17 09:25:01 is 62363984.695604 s in the future
tar: creative/data/ctp046aw.dat: time stamp 2009-09-17 09:25:00 is 62363983.682369 s in the future
tar: creative/data: time stamp 2009-09-17 09:25:30 is 62364013.652569 s in the future
tar: creative/ct_reg.dat: time stamp 2009-09-17 08:58:22 is 62362385.642038 s in the future
Create device node files...
Install script files...
install /tmp/xfisrc/ctsound to /etc/init.d...
/bin/sh: /sbin/chkconfig: not found
./ctsound: 35: Syntax error: Bad substitution
make: *** [load] Error 2

```

... but I failed :(

here is a part of my ./ctsound
```

...
KERNELVER=`uname -r`
if [ "${KERNELVER:0:3}" = "2.6" ]; then                     ## line 35
	suffix=.ko
elif [ "${KERNELVER:0:3}" = "2.4" ]; then
	suffix=.o
else
	echo "Unknown kernel version. Exit..."
	exit 1
fi
...

```
.. but I can't find a syntax error

... and ...
```

uname -r
2.6.20-15-generic

```

any ideas???

---------------
Kubuntu 7.04 - 64bit - 2.6.20-15-generic

---

### Post by innocenceisdeath on 2007-09-26
I've tried it too and I have a load of new drivers now in my restricted drivers manager. They are all enabled, but it says none of them are in use :confused:
Any ideas why this is?

---

### Post by demik on 2007-09-26
hi folks.

I created the first patch, but since, two others guys updated it. The version on my server is outdated, I will update it soon.

blubbi from the gentoo forums made a new TODO :
[http://forums.gentoo.org/viewtopic-t-587921.html]("http://forums.gentoo.org/viewtopic-t-587921.html")

About the syntax error, it's because ubuntu is using /bin/dash as /bin/sh, and dash does not support this syntax. Just edit the ctsound script and change #!/bin/sh to #!/bin/bash. It should work.

 If you are interested, We are on #creative @ freenode if you want to talk live.

Edit : files updated, new readme.txt :)

---

### Post by waldorsockbat on 2007-09-26
OK I got the patch and tried it following the guide from gentoo forum and here is the result


-desktop:~/XFiDrv_Linux_US-1.04$ sudo make install
Copy module files...
cp: cannot stat `ctossrv.ko': No such file or directory
cp: cannot stat `emupia.ko': No such file or directory
cp: cannot stat `ctsfman.ko': No such file or directory
cp: cannot stat `haxfi.ko': No such file or directory
cp: cannot stat `ctalsa.ko': No such file or directory
cp: cannot stat `ct20xut.ko': No such file or directory
cp: cannot stat `ctexfifx.ko': No such file or directory
cp: cannot stat `cthwiut.ko': No such file or directory
make: *** [copy_modules] Error 1
daddy@daddy-desktop:~/XFiDrv_Linux_US-1.04$ ./ctsound
./ctsound: 35: Syntax error: Bad substitution

I will never again buy a creative sound card.. This is beyond pathetic that open source folks have to fix a pos closed source driver that I myself have been waiting on for almost a year!

Yes I know I am ranting... sorry just had to get that off my chest.

---

### Post by demik on 2007-09-26
Can I have the full build output please ?

---

### Post by NullHead on 2007-09-26
I have just as of now got this to work :guitar:!!!!!!! all only with the help of demik ... sound is a bit  fuzzy but it is working never the less.  I highly recommend getting on irc and chatting live with him and his friends. install ```
sudo apt-get install xchat-gnome
``` and get to the chatting!!!!! I used gcc 4.1 from the repo 

all extol demik and other writers!!!

---

### Post by waldorsockbat on 2007-09-26
OK here is a little more info.Not afraid to say that I am in over my head here. Tying to use gusty  might make this harder im sure.


daddy@daddy-desktop:~$ find XFiDrv_Linux_US-1.04/ -exec touch -c {} \; && chmod -R 755 XFiDrv_Linux_US-1.04
daddy@daddy-desktop:~$ patch -p0 < XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch
patching file XFiDrv_Linux_US-1.04/include/ctalsa.h
patching file XFiDrv_Linux_US-1.04/Makefile
patching file XFiDrv_Linux_US-1.04/Makefile.conf.in
patching file XFiDrv_Linux_US-1.04/src/ctalsa/amidi.c
patching file XFiDrv_Linux_US-1.04/src/ctalsa/amixer.c
patching file XFiDrv_Linux_US-1.04/src/ctalsa/asynth.c
patching file XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa_main.c
patching file XFiDrv_Linux_US-1.04/src/ctalsa/dummy.c
patching file XFiDrv_Linux_US-1.04/src/ctalsa/pcm.c
patching file XFiDrv_Linux_US-1.04/src/emupia/emupia_guids.c
patching file XFiDrv_Linux_US-1.04/src/emupia/emupia_main.c
patching file XFiDrv_Linux_US-1.04/src/haxfi/haxfi_main.c
patching file XFiDrv_Linux_US-1.04/src/ossrv/ctossrv_main.c
patching file XFiDrv_Linux_US-1.04/src/ossrv/LinuxReg.c
patching file XFiDrv_Linux_US-1.04/src/ossrv/LinuxSys.c
patching file XFiDrv_Linux_US-1.04/src/ossrv/osutils.c
patching file XFiDrv_Linux_US-1.04/src/plugins/pluginutils.c
patching file XFiDrv_Linux_US-1.04/src/sfman/ctsfman_main.c
daddy@daddy-desktop:~$ cd XFiDrv_Linux_US-1.04
daddy@daddy-desktop:~/XFiDrv_Linux_US-1.04$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/daddy/XFiDrv_Linux_US-1.04
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.22-12-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.22-12-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070831 (prerelease) (Ubuntu 4.1.2-16ubuntu1)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for exported symbol dump_stack... grep: /lib/modules/2.6.22-12-generic/build/kernel/ksyms.c: No such file or directory
no
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for processor type... x86_64
checking for SMP... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for old kill_fasync... no
checking for dma_addr_t... no
checking for MUTEX macros... no
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... yes
checking for Procfs support... yes
configure: creating ./config.status
config.status: creating Makefile.conf
daddy@daddy-desktop:~/XFiDrv_Linux_US-1.04$ make
cd /home/daddy/XFiDrv_Linux_US-1.04/src/utils/alsaver; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
rm -f alsaver
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
rm -f alsaver
cd /home/daddy/XFiDrv_Linux_US-1.04/src/ossrv; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv'
rm -rf ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv'
rm -f ctossrv.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/emupia; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/emupia'
/home/daddy/XFiDrv_Linux_US-1.04/src/emupia/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M emupia_guids.c emupia_main.c   > .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/emupia'
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/emupia'
rm -rf emupia_guids.o emupia_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/emupia'
rm -f emupia.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/sfman; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/sfman'
/home/daddy/XFiDrv_Linux_US-1.04/src/sfman/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M ctsfman_main.c   > .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/sfman'
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/sfman'
rm -rf ctsfman_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/sfman'
rm -f ctsfman.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/haxfi; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/haxfi'
/home/daddy/XFiDrv_Linux_US-1.04/src/haxfi/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M haxfi_main.c   > .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/haxfi'
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/haxfi'
rm -rf haxfi_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/haxfi'
rm -f haxfi.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/ctalsa; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ctalsa'
/home/daddy/XFiDrv_Linux_US-1.04/src/ctalsa/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=0 -M amidi.c amixer.c asynth.c ctalsa_main.c dummy.c pcm.c   > .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ctalsa'
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ctalsa'
rm -rf amidi.o amixer.o asynth.o ctalsa_main.o dummy.o pcm.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ctalsa'
rm -f ctalsa.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/plugins/ct20xut; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins/ct20xut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions
cd ../../../src/plugins; make clean
make[2]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M pluginutils.c   > .depend
make[2]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[2]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins/ct20xut'
rm -f ct20xut.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx'
rm -rf  *.o *.ko *.o_shipped *~ *.mod.c .*cmd .tmp_versions .depend
cd ../../../src/plugins; make clean
make[2]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M pluginutils.c   > .depend
make[2]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[2]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx'
rm -f ctexfifx.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/plugins/cthwiut; make clean
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins/cthwiut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions
cd ../../../src/plugins; make clean
make[2]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M pluginutils.c   > .depend
make[2]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend
make[2]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins'
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/plugins/cthwiut'
rm -f cthwiut.ko
cd /home/daddy/XFiDrv_Linux_US-1.04/src/utils/alsaver; make
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
gcc -Wall -O  alsaver.c -o alsaver
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/utils/alsaver'
cp -f /home/daddy/XFiDrv_Linux_US-1.04/src/utils/alsaver/alsaver .
cd /home/daddy/XFiDrv_Linux_US-1.04/src/ossrv; make
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv'
/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M ctossrv_main.c LinuxReg.c LinuxSys.c osutils.c   > .depend
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv'
make[1]: Entering directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv'
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c ctossrv_main.c
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c LinuxReg.c
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c LinuxSys.c
LinuxSys.c: In function &#8216;sysRegisterInterrupt&#8217;:
LinuxSys.c:637: warning: cast from pointer to integer of different size
LinuxSys.c:642: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at /lib/modules/2.6.22-12-generic/build/include/linux/interrupt.h:66)
LinuxSys.c:642: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
LinuxSys.c: In function &#8216;sysGetPagePhysAddr&#8217;:
LinuxSys.c:947: warning: passing argument 1 of &#8216;kvirt_to_phys&#8217; makes integer from pointer without a cast
LinuxSys.c: In function &#8216;sysGetPageBusAddr&#8217;:
LinuxSys.c:974: warning: passing argument 1 of &#8216;kvirt_to_bus&#8217; makes integer from pointer without a cast
LinuxSys.c: In function &#8216;sysWriteFile&#8217;:
LinuxSys.c:1626: warning: pointer targets in passing argument 2 of &#8216;filp->f_op->write&#8217; differ in signedness
LinuxSys.c: In function &#8216;sysReadFile&#8217;:
LinuxSys.c:1675: warning: pointer targets in passing argument 2 of &#8216;filp->f_op->read&#8217; differ in signedness
LinuxSys.c: At top level:
LinuxSys.c:1463: warning: &#8216;errno&#8217; defined but not used
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c osutils.c
osutils.c:804:1: warning: "udelay" redefined
In file included from /lib/modules/2.6.22-12-generic/build/include/linux/delay.h:12,
                 from /lib/modules/2.6.22-12-generic/build/include/asm/apic.h:5,
                 from /lib/modules/2.6.22-12-generic/build/include/asm/smp.h:14,
                 from /lib/modules/2.6.22-12-generic/build/include/linux/smp.h:19,
                 from /lib/modules/2.6.22-12-generic/build/include/linux/topology.h:33,
                 from /lib/modules/2.6.22-12-generic/build/include/linux/mmzone.h:569,
                 from /lib/modules/2.6.22-12-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-12-generic/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-12-generic/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-12-generic/build/include/asm/local.h:4,
                 from /lib/modules/2.6.22-12-generic/build/include/linux/module.h:19,
                 from osutils.c:20:
/lib/modules/2.6.22-12-generic/build/include/asm/delay.h:20:1: warning: this is the location of the previous definition
osutils.c: In function &#8216;myDelay&#8217;:
osutils.c:814: warning: implicit declaration of function &#8216;__bad_delay&#8217;
osutils.c: At top level:
osutils.c:50: warning: &#8216;errno&#8217; defined but not used
ld -m elf_x86_64 -e stext -r ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o -o lin-ctossrv.o
ld -m elf_x86_64 -e stext -Ur ../../arch/x86_64/begin.o \
        ../../src/ossrv/lin-ctossrv.o \
        ../../arch/x86_64/ctossrv.a \
        ../../arch/x86_64/utils.a \
        ../../arch/x86_64/end.o -o ctossrv.o_shipped
make -C /lib/modules/2.6.22-12-generic/build SUBDIRS=/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-12-generic'
/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-12-generic/build/include -I/lib/modules/2.6.22-12-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-12-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M ipc   > .depend
/bin/sh: cannot create .depend: Permission denied
make[3]: *** [.depend] Error 2
make[2]: *** [_module_/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-12-generic'
make[1]: *** [module] Error 2
make[1]: Leaving directory `/home/daddy/XFiDrv_Linux_US-1.04/src/ossrv'
make: *** [ctossrv] Error 2
daddy@daddy-desktop:~/XFiDrv_Linux_US-1.04$ make install
Copy module files...
rm: cannot remove directory `/lib/modules/2.6.22-12-generic/kernel/drivers/ssound': Permission denied
make: *** [copy_modules] Error 1

---

### Post by demik on 2007-09-27
/bin/sh: cannot create .depend: Permission denied  <- permissions are ****** up

Try make as root, it should work.

---

### Post by waldorsockbat on 2007-09-27
./ctsound: 35: Syntax error: Bad substitution
make: *** [load] Error 2


using sudo I got a little farther this time but I failed once again.

---

### Post by waldorsockbat on 2007-09-27
Well after allot of searching and reading I have give up on the dream of a working driver. I refuse to compile my own vanilla kernel just to have crappy sound quality. I guess I will have to live with onboard sound until I can a sound card that is supported in linux that has as close as I can get sound quality to the X-fi.

---

### Post by amtam on 2007-09-28
> **waldorsockbat said:**
> Well after allot of searching and reading I have give up on the dream of a working driver. I refuse to compile my own vanilla kernel just to have crappy sound quality. I guess I will have to live with onboard sound until I can a sound card that is supported in linux that has as close as I can get sound quality to the X-fi.

You don't HAVE to recompile your own kernel. I managed to get it working using the stock-kernel of Ubuntu 7.04. I used instructions from [here](http://olausson.de/x-fi/readme.txt) and [here](http://forums.gentoo.org/viewtopic-t-587921.html).

[[img]http://intranet.etin.nl/images/x-fi_linux_working_small.jpg[/img]](http://intranet.etin.nl/images/x-fi_linux_working.jpg)

Click on the image for a bigger picture.

As you can see I did recompile the kernel, but it also works using the 2.6.20-16-generic kernel.
I use Audacious as a soundplayer and the sound is just fine. No cracks, no pops, no hickups. But if I use Totem, then the sound is 'looping' and generaly unstable. For now, I'm happy:D

It may not be perfect yet (after all, it's the very first beta), but it's useable.

---

### Post by NullHead on 2007-09-28
> **amtam said:**
> You don't HAVE to recompile your own kernel. I managed to get it working using the stock-kernel of Ubuntu 7.04. I used instructions from [here](http://olausson.de/x-fi/readme.txt) and [here](http://forums.gentoo.org/viewtopic-t-587921.html).

[[img]http://intranet.etin.nl/images/x-fi_linux_working_small.jpg[/img]](http://intranet.etin.nl/images/x-fi_linux_working.jpg)

Click on the image for a bigger picture.

As you can see I did recompile the kernel, but it also works using the 2.6.20-16-generic kernel.
I use Audacious as a soundplayer and the sound is just fine. No cracks, no pops, no hickups. But if I use Totem, then the sound is 'looping' and generaly unstable. For now, I'm happy:D

It may not be perfect yet (after all, it's the very first beta), but it's useable.

amtam do you have problems with the driver starting up when you computer boots up? When ever I restart mine the driver doesn't load properly or for that matter at all.

---

### Post by HilliBilly on 2007-09-28
hi,

does this new creative labs beta driver driver support _all_ X-Fi sound cards or only that which are mentioned? 

"This download is intended for the following audio devices only:

* Creative Sound Blaster X-Fi Elite Pro
* Creative Sound Blaster X-Fi Platinum
* Creative Sound Blaster X-Fi Fatal1ty®
* Creative Sound Blaster X-Fi XtremeGamer
* Creative Sound Blaster X-Fi XtremeMusic"

i do have a Creative Sound Blaster X-Fi Xtreme**Audio**. 
[http://www.soundblaster.com/products/product.asp?category=1&subcategory=208&product=15855&nav=1](http://www.soundblaster.com/products/product.asp?category=1&subcategory=208&product=15855&nav=1)

---

### Post by Sampler on 2007-09-28
Hello - bit of a newb here - followed the instructions from:
[http://forums.gentoo.org/viewtopic-t-587921.html](http://forums.gentoo.org/viewtopic-t-587921.html)
and got the "./ctsound: 35: Syntax error: Bad substitution" error so opened ctsound in gedit and globally substituted !/bin/sh for /bin/bash but now get:```
WARNING: Error inserting ctossrv (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctossrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting emupia (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```Being very new to linux quite a bit of this is going over my head - I'm happy now I've found this thread and one step closer to getting some sound. I've decided to start using Ubuntu after trying Vista and being decidedly unimpressed with Redmond's latest offerings!

TIA

Cheers

---

### Post by Sampler on 2007-09-28
Ah - just worked out what dmesg is:```
PU1._PDC] (Node ffff81007cda9ab0), AE_BAD_HEADER
[   32.042992] ACPI: Processor [CPU1] (supports 8 throttling states)
[   32.043025] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node ffff81007cda99b0), AE_BAD_HEADER
[   32.043044] ACPI: Processor [CPU2] (supports 8 throttling states)
[   32.043047] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   32.043051] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   32.210643] usbcore: registered new interface driver usbfs
[   32.210655] usbcore: registered new interface driver hub
[   32.210666] usbcore: registered new device driver usb
[   32.210986] USB Universal Host Controller Interface driver v3.0
[   32.211017] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   32.211023] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   32.211025] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   32.211093] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   32.211112] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000e480
[   32.211160] usb usb1: configuration #1 chosen from 1 choice
[   32.211172] hub 1-0:1.0: USB hub found
[   32.211174] hub 1-0:1.0: 2 ports detected
[   32.240816] ieee1394: Initialized config rom entry `ip1394'
[   32.244528] SCSI subsystem initialized
[   32.246701] libata version 2.20 loaded.
[   32.251046] Floppy drive(s): fd0 is 1.44M
[   32.272356] FDC 0 is a post-1991 82077
[   32.316962] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   32.316972] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   32.316974] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   32.316987] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   32.317006] ehci_hcd 0000:00:1d.7: debug port 1
[   32.317010] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   32.317013] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfebffc00
[   32.320896] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.320933] usb usb2: configuration #1 chosen from 1 choice
[   32.320945] hub 2-0:1.0: USB hub found
[   32.320948] hub 2-0:1.0: 8 ports detected
[   32.428808] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[   32.429131] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   32.429137] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   32.429139] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   32.429149] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   32.429169] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e800
[   32.429214] usb usb3: configuration #1 chosen from 1 choice
[   32.429225] hub 3-0:1.0: USB hub found
[   32.429227] hub 3-0:1.0: 2 ports detected
[   32.478872] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe6ff800-fe6fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.536639] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   32.536645] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   32.536646] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   32.536657] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   32.536675] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
[   32.536715] usb usb4: configuration #1 chosen from 1 choice
[   32.536727] hub 4-0:1.0: USB hub found
[   32.536729] hub 4-0:1.0: 2 ports detected
[   32.644577] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[   32.644582] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   32.644584] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   32.644592] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   32.644610] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000ec00
[   32.644650] usb usb5: configuration #1 chosen from 1 choice
[   32.644661] hub 5-0:1.0: USB hub found
[   32.644663] hub 5-0:1.0: 2 ports detected
[   32.753284] ahci 0000:02:00.0: version 2.1
[   32.753300] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.464168] usb 2-7: new high speed USB device using ehci_hcd and address 6
[   33.609337] usb 2-7: configuration #1 chosen from 1 choice
[   33.609563] hub 2-7:1.0: USB hub found
[   33.609823] hub 2-7:1.0: 4 ports detected
[   33.752106] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000f4600b]
[   33.760062] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   33.760068] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   33.760070] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   33.760124] ata1: SATA max UDMA/133 cmd 0xffffc20000050100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   33.760157] ata2: SATA max UDMA/133 cmd 0xffffc20000050180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   33.760161] scsi0 : ahci
[   33.955942] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   34.075888] ata1: SATA link down (SStatus 0 SControl 300)
[   34.075897] scsi1 : ahci
[   34.245336] usb 3-2: configuration #1 chosen from 1 choice
[   34.387744] ata2: SATA link down (SStatus 0 SControl 300)
[   34.388866] ata_piix 0000:00:1f.1: version 2.10ac1
[   34.388877] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   34.388888] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   34.389563] ata3: PATA max UDMA/133 cmd 0x000000000001d800 ctl 0x000000000001d482 bmdma 0x000000000001d000 irq 22
[   34.389600] ata4: PATA max UDMA/133 cmd 0x000000000001d400 ctl 0x000000000001d082 bmdma 0x000000000001d008 irq 22
[   34.389607] scsi2 : ata_piix
[   34.491690] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   34.615631] usb 4-1: device descriptor read/64, error -71
[   34.711883] ata3.00: ATAPI, max UDMA/66
[   34.711885] ata3.00: limited to UDMA/33 due to 40-wire cable
[   34.843525] usb 4-1: device descriptor read/64, error -71
[   34.879828] ata3.00: configured for UDMA/33
[   34.879832] scsi3 : ata_piix
[   35.050095] ATA: abnormal status 0x7F on port 0x000000000001d407
[   35.051341] scsi 2:0:0:0: CD-ROM            SONY     DVD RW DRU-820A  1.0b PQ: 0 ANSI: 5
[   35.052073] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   35.059425] usb 4-1: new low speed USB device using uhci_hcd and address 3
[   35.183367] usb 4-1: device descriptor read/64, error -71
[   35.211370] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   35.211380] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   35.211395] ata5: SATA max UDMA/133 cmd 0x000000000001e400 ctl 0x000000000001e082 bmdma 0x000000000001d880 irq 23
[   35.211408] ata6: SATA max UDMA/133 cmd 0x000000000001e000 ctl 0x000000000001dc02 bmdma 0x000000000001d888 irq 23
[   35.211415] scsi4 : ata_piix
[   35.396638] ata5.00: ata_hpa_resize 1: sectors = 72303840, hpa_sectors = 72303840
[   35.396639] ata5.00: ATA-6: WDC WD360GD-00FNA0, 35.06K35, max UDMA/133
[   35.396641] ata5.00: 72303840 sectors, multi 16: LBA48 
[   35.396642] ata5.00: applying bridge limits
[   35.397636] ata5.01: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   35.397638] ata5.01: ATA-7: Maxtor 6H400F0, HA431DD0, max UDMA/133
[   35.397639] ata5.01: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   35.408629] ata5.00: ata_hpa_resize 1: sectors = 72303840, hpa_sectors = 72303840
[   35.408630] ata5.00: configured for UDMA/100
[   35.411262] usb 4-1: device descriptor read/64, error -71
[   35.420411] ata5.01: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   35.420413] ata5.01: configured for UDMA/133
[   35.420415] scsi5 : ata_piix
[   35.627161] usb 4-1: new low speed USB device using uhci_hcd and address 4
[   36.042968] usb 4-1: device not accepting address 4, error -71
[   36.087256] ata6.00: ATA-6: Config  Disk, RGL10364, max UDMA/133
[   36.087257] ata6.00: 640 sectors, multi 1: LBA 
[   36.087258] ata6.00: Drive reports diagnostics failure. This may indicate a drive
[   36.087259] ata6.00: fault or invalid emulation. Contact drive vendor for information.
[   36.087556] ata6.00: configured for UDMA/133
[   36.087588] scsi 4:0:0:0: Direct-Access     ATA      WDC WD360GD-00FN 35.0 PQ: 0 ANSI: 5
[   36.087751] scsi 4:0:1:0: Direct-Access     ATA      Maxtor 6H400F0   HA43 PQ: 0 ANSI: 5
[   36.088093] scsi 5:0:0:0: Direct-Access     ATA      Config  Disk     RGL1 PQ: 0 ANSI: 5
[   36.088536] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   36.088540] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 16 (level, low) -> IRQ 16
[   36.088554] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   36.089290] ata7: PATA max UDMA/100 cmd 0x0000000000019c00 ctl 0x0000000000019882 bmdma 0x0000000000019400 irq 16
[   36.089428] ata8: PATA max UDMA/100 cmd 0x0000000000019800 ctl 0x0000000000019482 bmdma 0x0000000000019408 irq 16
[   36.089438] scsi6 : pata_jmicron
[   36.100173] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   36.100175] Uniform CD-ROM driver Revision: 3.20
[   36.100201] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   36.100348] SCSI device sda: 72303840 512-byte hdwr sectors (37020 MB)
[   36.100353] sda: Write Protect is off
[   36.100354] sda: Mode Sense: 00 3a 00 00
[   36.100361] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.100381] SCSI device sda: 72303840 512-byte hdwr sectors (37020 MB)
[   36.100385] sda: Write Protect is off
[   36.100386] sda: Mode Sense: 00 3a 00 00
[   36.100393] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.100395]  sda:<5>sr 2:0:0:0: Attached scsi generic sg0 type 5
[   36.101731] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   36.101739] scsi 4:0:1:0: Attached scsi generic sg2 type 0
[   36.101748] scsi 5:0:0:0: Attached scsi generic sg3 type 0
[   36.115007]  sda1
[   36.115164] sd 4:0:0:0: Attached scsi disk sda
[   36.115249] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[   36.115254] sdb: Write Protect is off
[   36.115255] sdb: Mode Sense: 00 3a 00 00
[   36.115262] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.115280] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[   36.115285] sdb: Write Protect is off
[   36.115286] sdb: Mode Sense: 00 3a 00 00
[   36.115292] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.115294]  sdb: sdb1 sdb2 <<6>usb 4-1: new low speed USB device using uhci_hcd and address 5
[   36.155346]  sdb5 >
[   36.155382] sd 4:0:1:0: Attached scsi disk sdb
[   36.155404] SCSI device sdc: 640 512-byte hdwr sectors (0 MB)
[   36.155409] sdc: Write Protect is off
[   36.155410] sdc: Mode Sense: 00 3a 00 00
[   36.155417] SCSI device sdc: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   36.155434] SCSI device sdc: 640 512-byte hdwr sectors (0 MB)
[   36.155438] sdc: Write Protect is off
[   36.155439] sdc: Mode Sense: 00 3a 00 00
[   36.155446] SCSI device sdc: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   36.155447]  sdc: unknown partition table
[   36.156033] sd 5:0:0:0: Attached scsi disk sdc
[   36.337658] Attempting manual resume
[   36.337661] swsusp: Resume From Partition 8:21
[   36.337662] PM: Checking swsusp image.
[   36.337786] PM: Resume from disk failed.
[   36.358081] kjournald starting.  Commit interval 5 seconds
[   36.358084] EXT3-fs: mounted filesystem with ordered data mode.
[   36.551681] irq 18: nobody cared (try booting with the "irqpoll" option)
[   36.551683] 
[   36.551684] Call Trace:
[   36.551685]  <IRQ>  [<ffffffff802bd235>] __report_bad_irq+0x35/0x90
[   36.551694]  [<ffffffff802bd4b0>] note_interrupt+0x220/0x280
[   36.551704]  [<ffffffff88044465>] :usbcore:usb_hcd_irq+0x25/0x60
[   36.551706]  [<ffffffff802bdf6a>] handle_fasteoi_irq+0xca/0x120
[   36.551708]  [<ffffffff8026223c>] call_softirq+0x1c/0x28
[   36.551711]  [<ffffffff80270189>] do_IRQ+0x89/0x100
[   36.551713]  [<ffffffff8025a180>] mwait_idle+0x0/0x50
[   36.551714]  [<ffffffff80261631>] ret_from_intr+0x0/0xa
[   36.551715]  <EOI>  [<ffffffff8025deb0>] generic_unplug_device+0x0/0x30
[   36.551719]  [<ffffffff8025a1c2>] mwait_idle+0x42/0x50
[   36.551721]  [<ffffffff8024b1ab>] cpu_idle+0x9b/0xd0
[   36.551723]  [<ffffffff805707ca>] start_kernel+0x24a/0x260
[   36.551725]  [<ffffffff80570163>] _sinittext+0x163/0x170
[   36.551726] 
[   36.551727] handlers:
[   36.551728] [<ffffffff88044440>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   36.551734] Disabling IRQ #18
[   36.570724] usb 4-1: device not accepting address 5, error -71
[   36.810613] usb 4-2: new low speed USB device using uhci_hcd and address 6
[   37.542273] usb 4-2: device descriptor read/64, error -71
[   38.297922] usb 4-2: device descriptor read/64, error -71
[   38.549805] usb 4-2: new low speed USB device using uhci_hcd and address 7
[   39.305454] usb 4-2: device descriptor read/64, error -71
[   40.061103] usb 4-2: device descriptor read/64, error -71
[   40.312985] usb 4-2: new low speed USB device using uhci_hcd and address 8
[   40.908709] usb 4-2: device not accepting address 8, error -71
[   41.068636] usb 4-2: new low speed USB device using uhci_hcd and address 9
[   41.664359] usb 4-2: device not accepting address 9, error -71
[   41.840297] usbcore: registered new interface driver hiddev
[   42.080178] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   42.251334] usb 1-2: configuration #1 chosen from 1 choice
[   42.460267] usb 2-7.2: new high speed USB device using ehci_hcd and address 7
[   42.573392] usb 2-7.2: configuration #1 chosen from 1 choice
[   42.780113] usb 2-7.3: new high speed USB device using ehci_hcd and address 8
[   42.882250] usb 2-7.3: configuration #1 chosen from 1 choice
[   43.032827] input: Chicony Saitek Eclipse II Keyboard as /class/input/input1
[   43.032837] input: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:1d.1-2
[   43.185709] input: Chicony Saitek Eclipse II Keyboard as /class/input/input2
[   43.185737] input,hiddev96: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:1d.1-2
[   43.185750] usbcore: registered new interface driver usbhid
[   43.185752] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   44.359856] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.410406] input: PC Speaker as /class/input/input3
[   44.435511] intel_rng: FWH not detected
[   44.480097] iTCO_vendor_support: vendor-support=0
[   44.487887] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   44.708434] input: PS2++ Logitech MX Mouse as /class/input/input4
[   44.711266] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   44.711288] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   44.767492] wmaster0: Selected rate control algorithm 'simple'
[   44.804350] wiphy0: hwaddr 00:15:af:0b:81:e0, rtl8187 V1 + rtl8225z2
[   44.804359] usbcore: registered new interface driver rtl8187
[   44.804361] usbcore: registered new interface driver usbserial
[   44.804372] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   44.804399] usbcore: registered new interface driver libusual
[   44.805760] usbcore: registered new interface driver xpad
[   44.805762] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   44.807282] Initializing USB Mass Storage driver...
[   44.856040] scsi8 : SCSI emulation for USB Mass Storage devices
[   44.856086] usbcore: registered new interface driver usb-storage
[   44.856088] USB Mass Storage support registered.
[   44.856142] usb-storage: device found at 7
[   44.856143] usb-storage: waiting for device to settle before scanning
[   44.856147] usbcore: registered new interface driver usbserial_generic
[   44.856149] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   45.012095] drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[   45.012097] drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[   45.012118] ipaq 1-2:1.0: PocketPC PDA converter detected
[   45.014150] usb 1-2: PocketPC PDA converter now attached to ttyUSB0
[   45.014159] ipaq 1-2:1.1: PocketPC PDA converter detected
[   45.015146] usb 1-2: PocketPC PDA converter now attached to ttyUSB1
[   45.015152] usbcore: registered new interface driver ipaq
[   48.200977] wmaster0: Does not support passive scan, disabled
[   49.286705] NET: Registered protocol family 17
[   49.856683] usb-storage: device scan complete
[   49.862931] scsi 8:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   49.869175] scsi 8:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   49.875546] scsi 8:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   49.881918] scsi 8:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   49.882933] sd 8:0:0:0: Attached scsi removable disk sdd
[   49.882952] sd 8:0:0:0: Attached scsi generic sg4 type 0
[   49.883802] sd 8:0:0:1: Attached scsi removable disk sde
[   49.883819] sd 8:0:0:1: Attached scsi generic sg5 type 0
[   49.884678] sd 8:0:0:2: Attached scsi removable disk sdf
[   49.884694] sd 8:0:0:2: Attached scsi generic sg6 type 0
[   49.885553] sd 8:0:0:3: Attached scsi removable disk sdg
[   49.885569] sd 8:0:0:3: Attached scsi generic sg7 type 0
[   66.248972] ata7.01: qc timeout (cmd 0x27)
[   66.248979] ata7.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 0
[   66.248981] ata7.01: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   66.248983] ata7.01: 320173056 sectors, multi 0: LBA48 
[   66.248987] ata7.01: failed to set xfermode (err_mask=0x40)
[   66.248989] ata7: failed to recover some devices, retrying in 5 secs
[   91.209124] NET: Registered protocol family 10
[   91.209170] lo: Disabled Privacy Extensions
[  101.400645] ata7.01: qc timeout (cmd 0x27)
[  101.400652] ata7.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 0
[  101.400657] ata7.01: failed to set xfermode (err_mask=0x40)
[  101.400660] ata7.01: limiting speed to UDMA/100:PIO3
[  101.400661] ata7: failed to recover some devices, retrying in 5 secs
[  101.628506] wlan0: no IPv6 routers present
[  136.552316] ata7.01: qc timeout (cmd 0x27)
[  136.552323] ata7.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 0
[  136.552326] ata7.01: failed to set xfermode (err_mask=0x40)
[  136.552327] ata7.01: disabled
[  137.056058] scsi7 : pata_jmicron
[  137.223359] ATA: abnormal status 0x7F on port 0x0000000000019807
[  137.223461] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  137.307905] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  137.307913] PCI: Setting latency timer of device 0000:04:00.0 to 64
[  137.307932] sky2 0000:04:00.0: v1.13 addr 0xfe9fc000 irq 19 Yukon-EC (0xb6) rev 2
[  137.312038] sky2 eth0: addr 00:18:f3:a9:b7:49
[  137.312057] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  137.312063] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  137.312083] sky2 0000:03:00.0: v1.13 addr 0xfe8fc000 irq 16 Yukon-EC (0xb6) rev 2
[  137.312144] sky2 eth1: addr 00:18:f3:ab:73:c3
[  137.315695] sky2 eth1: enabling interface
[  137.317504] sky2 eth1: ram buffer 48K
[  137.317612] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  137.415139] sky2 eth0: enabling interface
[  137.416949] sky2 eth0: ram buffer 48K
[  137.417047] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  137.508768] fuse init (API version 7.8)
[  137.529053] lp: driver loaded but no devices found
[  137.558248] Adding 6032368k swap on /dev/disk/by-uuid/8ed65ab6-155d-4ea4-ac53-46dc3a1b2940.  Priority:-1 extents:1 across:6032368k
[  137.704957] EXT3 FS on sdb1, internal journal
[  140.456883] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
[  140.458339] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  142.058054] No dock devices found.
[  142.066423] Using specific hotkey driver
[  142.094231] input: Power Button (FF) as /class/input/input5
[  142.094245] ACPI: Power Button (FF) [PWRF]
[  142.094275] input: Power Button (CM) as /class/input/input6
[  142.094283] ACPI: Power Button (CM) [PWRB]
[  142.133995] ibm_acpi: ec object not found
[  142.177720] pcc_acpi: loading...
[  144.225804] wlan0: starting scan
[  145.500134] wlan0: scan completed
[  146.821287] ppdev: user-space parallel port driver
[  147.378178] Bluetooth: Core ver 2.11
[  147.378215] NET: Registered protocol family 31
[  147.378216] Bluetooth: HCI device and connection manager initialized
[  147.378217] Bluetooth: HCI socket layer initialized
[  147.392157] Bluetooth: L2CAP ver 2.8
[  147.392159] Bluetooth: L2CAP socket layer initialized
[  147.515197] usb 4-1: new low speed USB device using uhci_hcd and address 10
[  148.254858] usb 4-1: device descriptor read/64, error -71
[  149.010509] usb 4-1: device descriptor read/64, error -71
[  149.262392] usb 4-1: new low speed USB device using uhci_hcd and address 11
[  150.018039] usb 4-1: device descriptor read/64, error -71
[  150.773690] usb 4-1: device descriptor read/64, error -71
[  151.025571] usb 4-1: new low speed USB device using uhci_hcd and address 12
[  151.621292] usb 4-1: device not accepting address 12, error -71
[  151.781222] usb 4-1: new low speed USB device using uhci_hcd and address 13
[  152.376940] usb 4-1: device not accepting address 13, error -71
[  152.536869] usb 4-2: new low speed USB device using uhci_hcd and address 14
[  153.292530] usb 4-2: device descriptor read/64, error -71
[  154.048166] usb 4-2: device descriptor read/64, error -71
[  154.300051] usb 4-2: new low speed USB device using uhci_hcd and address 15
[  155.055696] usb 4-2: device descriptor read/64, error -71
[  155.811348] usb 4-2: device descriptor read/64, error -71
[  156.063230] usb 4-2: new low speed USB device using uhci_hcd and address 16
[  156.658952] usb 4-2: device not accepting address 16, error -71
[  156.818881] usb 4-2: new low speed USB device using uhci_hcd and address 17
[  157.414602] usb 4-2: device not accepting address 17, error -71
[  157.566340] Bluetooth: RFCOMM socket layer initialized
[  157.566349] Bluetooth: RFCOMM TTY layer initialized
[  157.566350] Bluetooth: RFCOMM ver 1.8
[  160.573132] eth0: no IPv6 routers present
[  165.522885] wlan0: starting scan
[  166.798244] wlan0: scan completed
[  186.824985] wlan0: starting scan
[  188.100350] wlan0: scan completed
[  208.123103] wlan0: starting scan
[  209.362475] wlan0: scan completed
[  229.417210] wlan0: starting scan
[  230.648589] wlan0: scan completed
[  250.715316] wlan0: starting scan
[  251.990677] wlan0: scan completed
[  272.049411] wlan0: starting scan
[  273.324769] wlan0: scan completed
[  393.297095] wlan0: starting scan
[  394.572458] wlan0: scan completed
[  514.548780] wlan0: starting scan
[  515.824143] wlan0: scan completed
[  635.800470] wlan0: starting scan
[  637.075830] wlan0: scan completed
[  757.052159] wlan0: starting scan
[  758.287544] wlan0: scan completed
[  878.300855] wlan0: starting scan
[  879.535224] wlan0: scan completed
[  999.543531] wlan0: starting scan
[ 1000.774916] wlan0: scan completed
[ 1120.799225] wlan0: starting scan
[ 1122.074580] wlan0: scan completed
[ 1211.015253] ctossrv: module license 'Creative Proprietary License' taints kernel.
[ 1211.015378] ctossrv: Unknown symbol __stack_chk_fail
[ 1211.029955] emupia: Unknown symbol InterlockedIncrement
[ 1211.029969] emupia: Unknown symbol heap_alloc
[ 1211.029982] emupia: Unknown symbol stack_free_page
[ 1211.030008] emupia: Unknown symbol stack_alloc
[ 1211.030037] emupia: Unknown symbol get_ossrv
[ 1211.030049] emupia: Unknown symbol unload_all_plugins
[ 1211.030063] emupia: Unknown symbol stack_alloc_page
[ 1211.030075] emupia: Unknown symbol ioctl_dispatch
[ 1211.030087] emupia: Unknown symbol heap_free
[ 1211.030112] emupia: Unknown symbol InterlockedDecrement
[ 1211.030126] emupia: Unknown symbol stack_free
[ 1211.030687] ctsfman: Unknown symbol heap_alloc
[ 1211.030733] ctsfman: Unknown symbol get_ossrv
[ 1211.030745] ctsfman: Unknown symbol ioctl_dispatch
[ 1211.030757] ctsfman: Unknown symbol heap_free
[ 1211.032874] ct20xut: Unknown symbol InterlockedIncrement
[ 1211.032892] ct20xut: Unknown symbol __stack_chk_fail
[ 1211.032903] ct20xut: Unknown symbol heap_alloc
[ 1211.032916] ct20xut: Unknown symbol unregister_plugin
[ 1211.032932] ct20xut: Unknown symbol heap_free
[ 1211.032950] ct20xut: Unknown symbol register_plugin
[ 1211.032960] ct20xut: Unknown symbol InterlockedDecrement
[ 1211.039136] ctexfifx: Unknown symbol InterlockedDecrement
[ 1211.039154] ctexfifx: Unknown symbol register_plugin
[ 1211.039168] ctexfifx: Unknown symbol unregister_plugin
[ 1211.039182] ctexfifx: Unknown symbol __stack_chk_fail
[ 1211.039200] ctexfifx: Unknown symbol heap_alloc
[ 1211.039215] ctexfifx: Unknown symbol InterlockedIncrement
[ 1211.039227] ctexfifx: Unknown symbol heap_free
[ 1211.041588] cthwiut: Unknown symbol InterlockedIncrement
[ 1211.041605] cthwiut: Unknown symbol __stack_chk_fail
[ 1211.041617] cthwiut: Unknown symbol heap_alloc
[ 1211.041630] cthwiut: Unknown symbol unregister_plugin
[ 1211.041646] cthwiut: Unknown symbol heap_free
[ 1211.041663] cthwiut: Unknown symbol register_plugin
[ 1211.041673] cthwiut: Unknown symbol InterlockedDecrement
[ 1211.053565] haxfi: Unknown symbol InterlockedDecrement
[ 1211.053609] haxfi: Unknown symbol get_ossrv
[ 1211.053658] haxfi: Unknown symbol heap_alloc
[ 1211.053687] haxfi: Unknown symbol InterlockedIncrement
[ 1211.053707] haxfi: Unknown symbol heap_free
[ 1211.055585] ctalsa: Unknown symbol bytes_to_order
[ 1211.055709] ctalsa: Unknown symbol get_ossrv
[ 1211.055750] ctalsa: Unknown symbol __stack_chk_fail
[ 1211.055952] ctalsa: Unknown symbol heap_alloc
[ 1211.056015] ctalsa: Unknown symbol ioctl_dispatch
[ 1211.056038] ctalsa: Unknown symbol heap_free
[ 1242.058902] wlan0: starting scan
[ 1243.334263] wlan0: scan completed
[ 1363.318589] wlan0: starting scan
[ 1364.593946] wlan0: scan completed
[ 1484.574278] wlan0: starting scan
[ 1485.849633] wlan0: scan completed
[ 1605.825958] wlan0: starting scan
[ 1607.101317] wlan0: scan completed
[ 1727.077643] wlan0: starting scan
[ 1728.353004] wlan0: scan completed
[ 1848.345325] wlan0: starting scan
[ 1849.580701] wlan0: scan completed
[ 1969.593006] wlan0: starting scan
[ 1970.824392] wlan0: scan completed

```Any of that help?

---

### Post by amtam on 2007-09-28
> amtam do you have problems with the driver starting up when you computer boots up? When ever I restart mine the driver doesn't load properly or for that matter at all.

Yes, I do. Sometimes only the ctalsa-module loads and the others don't.
Executing /etc/init.d/ctsound stop/restart only results in a message 'ctalsa in use'. But 4 out of 5 attempts are succesfull. Remember, the driver is still a POS, so don't get your expectations up... ;)

> does this new creative labs beta driver driver support _all_ X-Fi sound cards or only that which are mentioned? 
i do have a Creative Sound Blaster X-Fi XtremeAudio.

The Xtreme Audio is not a 'real' X-Fi, it's actually an Audigy 4....

> Hello - bit of a newb here - followed the instructions from:
[http://forums.gentoo.org/viewtopic-t-587921.html](http://forums.gentoo.org/viewtopic-t-587921.html)
and got the "./ctsound: 35: Syntax error: Bad substitution" error so opened ctsound in gedit and globally substituted !/bin/sh for /bin/bash but now get:

You could try installing gcc-3.3
```
apt-get install gcc-3.3
``` and then tell the compiler to use 3.3 instead of gcc 4.1. Just type:
```
export CC=gcc-3.3
```
and then compile and install the modules again.

---

### Post by demik on 2007-09-28
> **Sampler said:**
> Ah - just worked out what dmesg is:

..snip...

any of that help?

The stack protection fails for some unknow reason.

try this :
edit Makefile.conf and add "-fno-stack-protector” to CFLAGS

---

### Post by NullHead on 2007-09-28
> **demik said:**
> The stack protection fails for some unknow reason.

try this :
edit Makefile.conf and add "-fno-stack-protector” to CFLAGS

That worked for me.

---

### Post by waldorsockbat on 2007-09-28
[QUOTE=amtam;3439356]You don't HAVE to recompile your own kernel. I managed to get it working using the stock-kernel of Ubuntu 7.04. I used instructions from [here](http://olausson.de/x-fi/readme.txt) and [here](http://forums.gentoo.org/viewtopic-t-587921.html).


Well I decided that I would try again after your post  I tried the guides and I still get this.
./ctsound: 35: Syntax error: Bad substitution
make: *** [load] Error 2

Q: During "make install" I get: "./ctsound: 35: Syntax error: Bad substitution"
A: If you are using Debian/Ubuntu, your /bin/sh probably points to /bin/dash.
--->Edit ctsound and change #!/bin/sh to #!/bin/bash 

I did that and I still get that error. I am running 64bit Gusty Beta. I have seen alot of people get it to work on FIesty but I have not seen any posts on getting it to work under Gusty so I am beginning to think Gusty is the problem. Still new to this so I am at a loss.

---

### Post by amtam on 2007-09-29
> 
Well I decided that I would try again after your post  I tried the guides and I still get this.
./ctsound: 35: Syntax error: Bad substitution
make: *** [load] Error 2

Q: During "make install" I get: "./ctsound: 35: Syntax error: Bad substitution"
A: If you are using Debian/Ubuntu, your /bin/sh probably points to /bin/dash.
--->Edit ctsound and change #!/bin/sh to #!/bin/bash 

I did that and I still get that error. I am running 64bit Gusty Beta. I have seen alot of people get it to work on FIesty but I have not seen any posts on getting it to work under Gusty so I am beginning to think Gusty is the problem. Still new to this so I am at a loss.

You could try replacing sh with bash systemwide and not just in the script.

```
rm -f /bin/sh
ln -s /bin/bash /bin/sh
```



Or you could edit the ctsound-script and rip out the offending piece of code. All it does is check if you have a 2.6 or 2.4 kernel.

Before:

```
KERNELVER=`uname -r`
if [ "${KERNELVER:0:3}" = "2.6" ]; then
	suffix=.ko
elif [ "${KERNELVER:0:3}" = "2.4" ]; then
	suffix=.o
else
	echo "Unknown kernel version. Exit..."
	exit 1
fi
```

After:

```
KERNELVER=`uname -r`
suffix=.ko

```

Make sure you edit the ctsound in the source and not in /etc/init.d/ctsound because that will get overwritten.
Good luck!

---

### Post by Sampler on 2007-09-29
Thanks for the replies guys:> **amtam said:**
> 
You could try installing gcc-3.3
```
apt-get install gcc-3.3
``` and then tell the compiler to use 3.3 instead of gcc 4.1. Just type:
```
export CC=gcc-3.3
```
and then compile and install the modules again.Thanks but I still get the same error - would it be worth going back to 4.1 and would that simply be **export CC=gcc-4.1**?> **demik said:**
> The stack protection fails for some unknow reason.

try this :
edit Makefile.conf and add "-fno-stack-protector” to CFLAGSWhere abouts would I add this as there's a few occurrences of CFLAGS int he Makefile.conf```
mainsrcdir 		= .
MAINSRCDIR 		= /home/sampler/Desktop/XFiDrv_Linux_US-1.04

CROSS_COMPILE           = 
ARCH                    = x86_64
export CROSS_COMPILE ARCH

AS			= $(CROSS_COMPILE)as
LD			= $(CROSS_COMPILE)ld -m elf_x86_64 -e stext
CC			= $(CROSS_COMPILE)gcc
CPP			= $(CROSS_COMPILE)gcc -E
AR			= $(CROSS_COMPILE)ar
CXX			= $(CROSS_COMPILE)g++

prefix			= /usr
exec_prefix		= ${prefix}
sysconfdir		= ${prefix}/etc
bindir			= ${exec_prefix}/bin
sbindir			= ${exec_prefix}/sbin
mandir			= ${prefix}/man
moddir			= /lib/modules/0.0.0/misc
moddir_tree		= 
processor		= x86_64
msmp			= 1
kdir                    = /lib/modules/2.6.20-16-generic/build
kaversion		= 0.0.0
kversion		= 0
kpatchlevel		= 6
ksublevel		= 0
kextraversion		= 
alsainc                 = /lib/modules/2.6.20-16-generic/build/include
ALSA_BUILD		= n
CONFIG_MODULES		= y
INCLUDES		= -I$(ROOTDIR)/include -isystem /lib/modules/2.6.20-16-generic/build/include -I/lib/modules/2.6.20-16-generic/build/include/asm/mach-default -I/lib/modules/2.6.20-16-generic/build/include
CFLAGS			= -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN \
			  -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" $(INCLUDES)
ifeq ($(USRDLL), y)
CFLAGS			+= -fPIC -D_USRDLL
else
CFLAGS			+= -D__KERNEL__ -DMODULE
endif


ifeq ($(ARCH), x86_64)
    ifneq ($(USRDLL), y)
        CFLAGS          += -mcmodel=kernel
    endif
    CFLAGS              += -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks
    CFLAGS              += -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64
    CFLAGS              += -D__CT_BOUND_64BIT
else
    CFLAGS              += -march=pentium -m32 -D__CT_BOUND_32BIT
endif

CPPFLAGS                = $(INCLUDE) -fno-exceptions -fno-rtti
```I tried adding it on line 35 (the first mention of CFLAGS) after the = and before -Wall -fomit... but this also didn't resolve the problem - I guess I'm putting it in the wrong place?

---

### Post by demik on 2007-09-29
Usually I put -fno-stack-protector just before -D__CT_BOUND_64BIT

---

### Post by JaJaJim on 2007-09-29
hello 
i am a linux "beginner" :D and sorry for may bad english

all your help lets my x-fi :guitar:  under ubuntu 7.04 

with 
# asoundconf list
#asoundconf set-default-card 2 [X-Fi           ]: X-Fi - Creative X-Fi [ac00]

i sett x-fi as default soundcard, works fine and i can play mp3 with xmms (good)  or totem video player (with some errors)

but after restart ubuntu x-fi driver are installet but not loaded (ubuntu restricted drivers gnome tool shows me status not in use but aktivatet)
-> no card -> reinstall

how can i enable the driver automatic? (maybe a beginner question :) )

thx

update:
i add ctalsa, haxfi, cthwiut, ctexfifx, ct20xut, ctsfman, emupia, ctossrv and upia to  /etc/modules, but dosent work for me :(

---

### Post by waldorsockbat on 2007-09-30
[QUOTE=amtam;3445166]You could try replacing sh with bash systemwide and not just in the script.

```
rm -f /bin/sh
ln -s /bin/bash /bin/sh
```



OK did that and got this at the end of make install this time I am going to try the other suggestion now.

WARNING: Error inserting ctossrv (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/ctossrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting emupia (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.22-12-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by waldorsockbat on 2007-09-30
[/QUOTE]Or you could edit the ctsound-script and rip out the offending piece of code. All it does is check if you have a 2.6 or 2.4 kernel.

Before:

```
KERNELVER=`uname -r`
if [ "${KERNELVER:0:3}" = "2.6" ]; then
	suffix=.ko
elif [ "${KERNELVER:0:3}" = "2.4" ]; then
	suffix=.o
else
	echo "Unknown kernel version. Exit..."
	exit 1
fi
```

After:

```
KERNELVER=`uname -r`
suffix=.ko

```

Make sure you edit the ctsound in the source and not in /etc/init.d/ctsound because that will get overwritten.
Good luck![/QUOTE]

Now I cant even get to make install here is as far as I got.God I hate being a noob..
$ sudo chmod -R 755 XFiDrv_Linux_US-1.04 && find XFiDrv_Linux_US-1.04/ -exec touch -c {} \;
touch: setting times of `XFiDrv_Linux_US-1.04/include/linux/devfs_fs_kernel.h': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctstatic.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/Default4.sfm': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctxficm.rfx': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctxfigm.rfx': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/settingsbkup.sfm': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/CT2MGM.SF2': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctdut.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctspn.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctfrn.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctchs.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctcht.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctjpn.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctbrz.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctkor.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctger.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/lang/ctita.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/creative.state': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctxfiem.rfx': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctbas2w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctdaught.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ct_reg.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/settings.sfm': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0460w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0462w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0463w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp055aw.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0776w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0466w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp073aw.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0468w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0465w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0779w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0679w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctd20x.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0730w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/cts20x.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0773w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0464w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0760w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp046aw.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0550w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/data/ctp0469w.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/CT1MGM.ROM': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctxficbm.rfx': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/creative/ctdlang.dat': Permission denied
touch: setting times of `XFiDrv_Linux_US-1.04/Makefile.conf': Permission denied

---

### Post by demik on 2007-09-30
sudo find XFiDrv_Linux_US-1.04/ -exec touch -c {} \;    :)

---

### Post by NullHead on 2007-09-30
Anyone have this installed and running in Gutsy yet? I've been unable to do it.

---

### Post by 0time on 2007-10-01
hi all,

this weekend I compiled successfully the x-fi closed source drivers for my x-fi platium card. Appart from having to load it manually on each system boot, I am experiencing some audio problems which I describe here as follows:

Amarok : It just hangs on load. Cant play any music track. I only get a repeating part of any track I play, just like when you play an scratched cd. I configured in settings with alsa or oss, with no results. Tried to change engine but cant find any other engine even though I have been googling a lot. I get the same issue with rythmbox.

Youtube videos: I finally manage to install flash with swiftweasel, but each time I want to play a video, the buffering gets full, the video starts with no sound and after 3 or 4 seconds it just wont play. Last.fm wont play any sound either. divx stage6 videos work like a charm. And the rest of flash content works fine.

SO I wonder if there is any workaround for such programs, or if anyone has run into the same issues and got them solved. Not beeing able to use amarok or any app with a music data base is very annoying because I have a large music collection which I cannot manage with programs like xmms or bmp, eventhough sound does work well.

Dvd or divx playback work perfectly with mplayer, rather than totem. Thanks in advance for all the help in this forum.

UBUNTU 7.04 2.6.20-16-generic gcc 3.3.

---

### Post by NullHead on 2007-10-01
> **0time said:**
> hi all,

this weekend I compiled successfully the x-fi closed source drivers for my x-fi platium card. Appart from having to load it manually on each system boot, I am experiencing some audio problems which I describe here as follows:

Amarok : It just hangs on load. Cant play any music track. I only get a repeating part of any track I play, just like when you play an scratched cd. I configured in settings with alsa or oss, with no results. Tried to change engine but cant find any other engine even though I have been googling a lot. I get the same issue with rythmbox.

Youtube videos: I finally manage to install flash with swiftweasel, but each time I want to play a video, the buffering gets full, the video starts with no sound and after 3 or 4 seconds it just wont play. Last.fm wont play any sound either. divx stage6 videos work like a charm. And the rest of flash content works fine.

SO I wonder if there is any workaround for such programs, or if anyone has run into the same issues and got them solved. Not beeing able to use amarok or any app with a music data base is very annoying because I have a large music collection which I cannot manage with programs like xmms or bmp, eventhough sound does work well.

Dvd or divx playback work perfectly with mplayer, rather than totem. Thanks in advance for all the help in this forum.

UBUNTU 7.04 2.6.20-16-generic gcc 3.3.

Well I have all of the same problems that you do but I use xmms and it works really good. I also have to load the driver manually. Flash and other online stuff works good though. Totem I've found doesn't work though only VLC and mplayer.

---

### Post by 0time on 2007-10-01
*Well I have all of the same problems that you do but I use xmms and it works really good. I also have to load the driver manually. Flash and other online stuff works good though. Totem I've found doesn't work though only VLC and mplayer.*

So youtube works fine in your setup? hmmm

---

### Post by NullHead on 2007-10-03
I've also got this to work in Debian Lenny or as better known Testing. It actually works better IMHO :guitar:

---

### Post by Garyu on 2007-10-05
Awesome. Finally something happening around X-Fi. Been waiting and waiting to order a card until the drivers were released, but now I couldn't keep myself from the internet store any longer. So I just placed an order for a XtremeGamer card. 

Looks like a bit of a hassle to get it going though. Maybe someone could be kind enough to put together a howto for compiling the driver in Feisty so I can use it monday night when my card is ETA? That would be so great. Having a howto in a separate thread that is updated continuously would be much better than trying to get something out of the links posted here and there in this thread. Even greater if a separate howto for Gutsy could pop up eventually. I'm not switching to Gutsy until october 18th, so Feisty will be my first platform to try this on. :D

---

### Post by mhenriday on 2007-10-05
I tried following the procedure on the** Gentoo Forums**, and things seemed to be working pretty well until the execution of the «cd XFiDrv_Linux_US-1.04 && ./configure && make» command was nearly finished, when the terminal displayed the following :
```
CT_BOUND_64BIT -M ipc   > .depend
/bin/sh: cannot create .depend: Permission denied
make[3]: *** [.depend] Error 2
make[2]: *** [_module_/home/mhenriday/XFiDrv_Linux_US-1.04/src/ossrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [module] Error 2
make[1]: Leaving directory `/home/mhenriday/XFiDrv_Linux_US-1.04/src/ossrv'
make: *** [ctossrv] Error 2
```
Despite the above, I decided to go ahead with «sudo make install», with the following somewhat discouraging result :
```
Copy module files...
cp: cannot take status of "ctossrv.ko": The file or catalogue does not exist
cp: cannot take status of "emupia.ko": The file or catalogue does not exist
cp:cannot take status of "ctsfman.ko": The file or catalogue does not exist
cp: cannot take status of "haxfi.ko": The file or catalogue does not exist
cp: cannot take status of "ctalsa.ko": The file or catalogue does not exist
cp: cannot take status of "ct20xut.ko": The file or catalogue does not exist
cp: cannot take status of "ctexfifx.ko": The file or catalogue does not exist
cp: cannot take status of "cthwiut.ko": The file or catalogue does not exist
make: *** [copy_modules] Error 1
```
So can it go ! Let me echo **Garyu**'s no doubt heartfelt request from «björkarnas stad» that some knowledgeable person put together a «how to» for installation from **Feisty** ; many of us have been waiting a long, long time to get that **Soundblaster X-Fi ** card working in our favourite OS....

Henri

---

### Post by demik on 2007-10-06
Try both make and make install as root (sudo make && sudo make install)

---

### Post by mhenriday on 2007-10-06
> **demik said:**
> Try both make and make install as root (sudo make && sudo make install)**Demik**, thanks for your speedy reply ! Things definitely seem to be going in the right direction, even if I've not yet reached the goal. First I entered ```
cd ~/XFiDrv_Linux_US-1.04$ cd XFiDrv_Linux_US-1.04 && ./configure && sudo make
``` from my home directory, which seemed to work pretty well. While a lot of warnings did appear in terminal, e g,
> WARNING: could not find /home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/.cthwiut.o_shipped.cmd for /home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.o_shipped
WARNING: "InterlockedDecrement" [/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "register_plugin" [/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "heap_free" [/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "unregister_plugin" [/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "heap_alloc" [/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "__stack_chk_fail" [/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "InterlockedIncrement" [/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
I did manage to get this far :
>   CC      /home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.mod.o
  LD [M]  /home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut'
cp -f /home/mhenriday/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko .
 I then entered ```
sudo make install
``` from my **X-Fi** directory (mhenriday@mhenriday-desktop:~/XFiDrv_Linux_US-1.04$), with the following result :
> Copy module files...
Update module dependency relationships...
Warning: Can't not find blacklist file /etc/hotplug/blacklist
Install libs...
Install database files...
tar: creative/data/ctp073aw.dat: time value 2009-09-17 11:25:02 is 61516128.520588 seconds in the future
tar: creative/data/ctp055aw.dat: time value 2009-09-17 11:25:01 is 61516127.48885 seconds in the future
tar: creative/data/ctp046aw.dat: time value 2009-09-17 11:25:00 isr 61516126.48481 seconds in the future
tar: creative/data: time value 2009-09-17 11:25:30 is 61516156.476745 seconds in the future
tar: creative/ct_reg.dat: time value 2009-09-17 10:58:22 is 61514528.473137 seconds in the future
Create device node files...
/dev/emupia already exixts
/dev/x-fi already exists
Install script files...
/etc/init.d/ctsound already exists. Overwrite it...
./ctsound: 35: Syntax error: Bad substitution
make: *** [load] Fel 2
Aside from the fact that the above looks to me rather like a claim to have reversed time's arrow, where do I go from here to push this heavy waggon over the finish line, so that I can begin to listen to audio in **Ubuntu** ? As I said above, I feel I'm very near the goal - but close counts only in horseshoes (and in *boule*)....

Henri

---

### Post by incidence on 2007-10-06
Everybody in this thread, who gets:
```
./ctsound: 35: Syntax error: Bad substitution
```

Change your /bin/sh symlink to point to /bin/bash. It'll work.

Everybody who gets:
```
Copy module files...
cp: cannot take status of "ctossrv.ko": The file or catalogue does not exist
cp: cannot take status of "emupia.ko": The file or catalogue does not exist
cp:cannot take status of "ctsfman.ko": The file or catalogue does not exist
cp: cannot take status of "haxfi.ko": The file or catalogue does not exist
cp: cannot take status of "ctalsa.ko": The file or catalogue does not exist
cp: cannot take status of "ct20xut.ko": The file or catalogue does not exist
cp: cannot take status of "ctexfifx.ko": The file or catalogue does not exist
cp: cannot take status of "cthwiut.ko": The file or catalogue does not exist
make: *** [copy_modules] Error 1
```

Add -fno-stack-protector to CFLAGS in Makefile.conf. Then run make.

See, [http://x-fi.olausson.de/index.php/HOWTO](http://x-fi.olausson.de/index.php/HOWTO)

Anyway, I got X-Fi working, but the sound is crappy, but the sound is kinda cracky / distorted, any idea why? I'm using headphones. And can you adjust the crystalizer yet or such?

---

### Post by mhenriday on 2007-10-06
*Terve*, incidence ! Your instructions on changing my «**/bin/sh**» symlink to point to «**/bin/bash**», to add «**-fno-stack-protector**» to «**CFLAGS**» in «**Makefile.conf**», and then run «**make**» seem to be precisely what I need, but unfortunately I lack sufficient knowledge to carry them out without screwing things up more badly than they are at present. Would you be willing to provide a step-by-step tutorial that people like myself who are not that well-versed in **'nix** machines might have a reasonable chance of following ?...

You mention that the sound you are getting from your **X-Fi** setup is crappy. In addition to **Feisty**, I'm running both **XP** and **Vista** on the machine with an **X-Fi** card, and there have experienced no problems with sound quality. Is the  sound on  your machine of crappy quality only on **Ubuntu,** or is it equally bad on other OS as well ?...

Henri

---

### Post by NullHead on 2007-10-06
I'm not getting the crappy sound problem with xmms ... it actually sounds very good! however I haven't been able to get surround sound to work at all and I haven't been able to change my crystalizer either, but we should all remember this is still a beta driver and it's unstable and not fully functional yet. Back to the xmms thing if you import a winamp preset into your eq it sounds allot better that if you don't.

---

### Post by astraycat on 2007-10-06
Hi, I'm kind of a newbie at this, so I'm having some problems.

I followed the directions at [http://blackbox.lostwave.net/x-fi/readme.txt](http://blackbox.lostwave.net/x-fi/readme.txt) incuding chaing the #!/bin/sh to #/bin/bash and adding -fno-stack-protector to the Makefile, and it all compiles fine. But when I try to install, it ends with:
```
install /home/chris/XFiDrv_Linux_US-1.04/ctsound to /etc/init.d...
FATAL: Error inserting ctalsa (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg shows:
```

[ 2147.410687] ctalsa: disagrees about version of symbol snd_pcm_lib_free_pages
[ 2147.410690] ctalsa: Unknown symbol snd_pcm_lib_free_pages
[ 2147.410703] ctalsa: disagrees about version of symbol snd_pcm_set_ops
[ 2147.410704] ctalsa: Unknown symbol snd_pcm_set_ops
[ 2147.410753] ctalsa: disagrees about version of symbol snd_card_new
[ 2147.410754] ctalsa: Unknown symbol snd_card_new
[ 2147.410784] ctalsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 2147.410785] ctalsa: Unknown symbol snd_pcm_hw_constraint_integer
[ 2147.410805] ctalsa: disagrees about version of symbol snd_pcm_lib_preallocate_free_for_all
[ 2147.410806] ctalsa: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[ 2147.410823] ctalsa: disagrees about version of symbol snd_pcm_lib_ioctl
[ 2147.410824] ctalsa: Unknown symbol snd_pcm_lib_ioctl
[ 2147.410844] ctalsa: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 2147.410845] ctalsa: Unknown symbol snd_pcm_lib_malloc_pages
[ 2147.410859] ctalsa: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 2147.410860] ctalsa: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 2147.410937] ctalsa: disagrees about version of symbol snd_ctl_remove
[ 2147.410938] ctalsa: Unknown symbol snd_ctl_remove
[ 2147.410984] ctalsa: disagrees about version of symbol snd_card_free
[ 2147.410985] ctalsa: Unknown symbol snd_card_free
[ 2147.411020] ctalsa: disagrees about version of symbol snd_ctl_free_one
[ 2147.411021] ctalsa: Unknown symbol snd_ctl_free_one
[ 2147.411033] ctalsa: disagrees about version of symbol snd_pcm_hw_constraint_minmax
[ 2147.411034] ctalsa: Unknown symbol snd_pcm_hw_constraint_minmax
[ 2147.411077] ctalsa: disagrees about version of symbol snd_ctl_add
[ 2147.411078] ctalsa: Unknown symbol snd_ctl_add
[ 2147.411090] ctalsa: disagrees about version of symbol snd_pcm_new
[ 2147.411091] ctalsa: Unknown symbol snd_pcm_new
[ 2147.411102] ctalsa: disagrees about version of symbol snd_pcm_period_elapsed
[ 2147.411103] ctalsa: Unknown symbol snd_pcm_period_elapsed
[ 2147.411117] ctalsa: disagrees about version of symbol snd_card_register
[ 2147.411118] ctalsa: Unknown symbol snd_card_register
[ 2147.411251] ctalsa: disagrees about version of symbol snd_ctl_new1
[ 2147.411252] ctalsa: Unknown symbol snd_ctl_new1

```

I really have no idea what to do about fixing this, and I'd really like my X-Fi to work in Linux. Can anyone help?

---

### Post by diebels on 2007-10-06
So setting gstreamer-properties to alsa output does nothing?

I'm at 32bit, so can't try myself.

---

### Post by Flashstar on 2007-10-07
> **astraycat said:**
> Hi, I'm kind of a newbie at this, so I'm having some problems.

I followed the directions at [http://blackbox.lostwave.net/x-fi/readme.txt](http://blackbox.lostwave.net/x-fi/readme.txt) incuding chaing the #!/bin/sh to #/bin/bash and adding -fno-stack-protector to the Makefile, and it all compiles fine. But when I try to install, it ends with:
```
install /home/chris/XFiDrv_Linux_US-1.04/ctsound to /etc/init.d...
FATAL: Error inserting ctalsa (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg shows:
```

[ 2147.410687] ctalsa: disagrees about version of symbol snd_pcm_lib_free_pages
[ 2147.410690] ctalsa: Unknown symbol snd_pcm_lib_free_pages
[ 2147.410703] ctalsa: disagrees about version of symbol snd_pcm_set_ops
[ 2147.410704] ctalsa: Unknown symbol snd_pcm_set_ops
[ 2147.410753] ctalsa: disagrees about version of symbol snd_card_new
[ 2147.410754] ctalsa: Unknown symbol snd_card_new
[ 2147.410784] ctalsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 2147.410785] ctalsa: Unknown symbol snd_pcm_hw_constraint_integer
[ 2147.410805] ctalsa: disagrees about version of symbol snd_pcm_lib_preallocate_free_for_all
[ 2147.410806] ctalsa: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[ 2147.410823] ctalsa: disagrees about version of symbol snd_pcm_lib_ioctl
[ 2147.410824] ctalsa: Unknown symbol snd_pcm_lib_ioctl
[ 2147.410844] ctalsa: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 2147.410845] ctalsa: Unknown symbol snd_pcm_lib_malloc_pages
[ 2147.410859] ctalsa: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 2147.410860] ctalsa: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 2147.410937] ctalsa: disagrees about version of symbol snd_ctl_remove
[ 2147.410938] ctalsa: Unknown symbol snd_ctl_remove
[ 2147.410984] ctalsa: disagrees about version of symbol snd_card_free
[ 2147.410985] ctalsa: Unknown symbol snd_card_free
[ 2147.411020] ctalsa: disagrees about version of symbol snd_ctl_free_one
[ 2147.411021] ctalsa: Unknown symbol snd_ctl_free_one
[ 2147.411033] ctalsa: disagrees about version of symbol snd_pcm_hw_constraint_minmax
[ 2147.411034] ctalsa: Unknown symbol snd_pcm_hw_constraint_minmax
[ 2147.411077] ctalsa: disagrees about version of symbol snd_ctl_add
[ 2147.411078] ctalsa: Unknown symbol snd_ctl_add
[ 2147.411090] ctalsa: disagrees about version of symbol snd_pcm_new
[ 2147.411091] ctalsa: Unknown symbol snd_pcm_new
[ 2147.411102] ctalsa: disagrees about version of symbol snd_pcm_period_elapsed
[ 2147.411103] ctalsa: Unknown symbol snd_pcm_period_elapsed
[ 2147.411117] ctalsa: disagrees about version of symbol snd_card_register
[ 2147.411118] ctalsa: Unknown symbol snd_card_register
[ 2147.411251] ctalsa: disagrees about version of symbol snd_ctl_new1
[ 2147.411252] ctalsa: Unknown symbol snd_ctl_new1

```

I really have no idea what to do about fixing this, and I'd really like my X-Fi to work in Linux. Can anyone help?

I too am getting the same problem. On the blackbox website guide, it says to recompile your kernel, but I don't want to do that.

Edit: it appears to have something to do with Gutsy being compiled with SLUB, while Fiesty was compiled with SLAB? This is why the driver works in Fiesty and not in Gutsy (I'm running Gutsy).

---

### Post by incidence on 2007-10-07
> **mhenriday said:**
> *Terve*, incidence ! Your instructions on changing my «**/bin/sh**» symlink to point to «**/bin/bash**», to add «**-fno-stack-protector**» to «**CFLAGS**» in «**Makefile.conf**», and then run «**make**» seem to be precisely what I need, but unfortunately I lack sufficient knowledge to carry them out without screwing things up more badly than they are at present. Would you be willing to provide a step-by-step tutorial that people like myself who are not that well-versed in **'nix** machines might have a reasonable chance of following ?...

You mention that the sound you are getting from your **X-Fi** setup is crappy. In addition to **Feisty**, I'm running both **XP** and **Vista** on the machine with an **X-Fi** card, and there have experienced no problems with sound quality. Is the  sound on  your machine of crappy quality only on **Ubuntu,** or is it equally bad on other OS as well ?...

Henri

Hi Henri,

Regarding on the makefile.conf, I took a screenshot for you, here.
[URL="http://animesivu.com/upload/view/381B2E53.png"]
[IMG]http://animesivu.com/upload/thumb/381B2E53.png[/IMG]
[/URL]

And here's for the /bin/bash -thing. Note, this is done as root.
[URL="http://animesivu.com/upload/view/7BE9181D.png"]
[IMG]http://animesivu.com/upload/thumb/7BE9181D.png[/IMG]
[/URL]

---

### Post by mhenriday on 2007-10-07
Well, **incidence**, now I've definitely gone off the deep end ! I was able to follow your instructions with regard to removing the «**bin/sh**» file and then establishing a symbolic link to «**bin/bash**», but those relating to «Makefile.conf», were beyond me ; I was simply unable to work out how you got there (i e, to the screenshot you provided) ! So I tried to do what I usually do in similar situations, I e, backtrack, but when I attempted again to configure and compile the **XFiDrv_Linux_US-1.04** file, the result was not encouraging :
> mhenriday@mhenriday-desktop:~/XFiDrv_Linux_US-1.04$ cd XFiDrv_Linux_US-1.04 && ./configure && make
bash: cd: XFiDrv_Linux_US-1.04: Filen eller katalogen finns inte [The file or catalogue does not exist]
Is there anyway I can reconstruct the  «**bin/sh**» file I removed, so that I can try to muddle through again ? Or perhaps I need to do something entirely different ? Should I simply wait for the «**Gutsy**» upgrade, which will reconfigure most of my files, and then attempt once again to install the **Creative** driver ? Two steps forward and one step back - or is it rather one step forward and two steps back ?...

In any event, thanks a lot for your patience in helping someone with as little Linux experience as myself !

Henri

---

### Post by Sampler on 2007-10-07
Hello - me again!

Not had chance to have a look at this all week but have had a tinker today and still no joy - have added the **-fno-stack-protector** in the **Makefile.conf** and tried to re-run **make install** to no effect - have tried putting it where indicated above in the piccy and also where mentioned earlier before the **-D__CT_BOUND_64BIT** part.

Maybe I'll leave this a little while and go check on how to sort out getting dual screen support from my X1950 before coming back - fingers crossed this will be a little further on by then.

Also for the guy above, from one noob to another, to edit the **Makefile.conf** you need to do the following in **terminal**:

**sudo gedit Makefile.conf**

That is if you haven't already **sudo su**'d to be permanantly as root with full permissions.

Cheers

[edit]

Also noticed if I leave the terminal open for a while after I get all this:```
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
```The first line there interests me, is this trying to reference the PCI port the card is in? As I have it in the last slot not the first (which i believe should be 2 if the first is 0). Is there somewhere I can edit this?

---

### Post by amtam on 2007-10-08
> **mhenriday said:**
> Well, **incidence**, now I've definitely gone off the deep end ! I was able to follow your instructions with regard to removing the «**bin/sh**» file and then establishing a symbolic link to «**bin/bash**», but those relating to «Makefile.conf», were beyond me ; I was simply unable to work out how you got there (i e, to the screenshot you provided) ! So I tried to do what I usually do in similar situations, I e, backtrack, but when I attempted again to configure and compile the **XFiDrv_Linux_US-1.04** file, the result was not encouraging :

> [b]mhenriday@mhenriday-desktop:~/XFiDrv_Linux_US-1.04$ cd XFiDrv_Linux_US-1.04 && ./configure && make
bash: cd: XFiDrv_Linux_US-1.04: Filen eller katalogen finns inte [The file or catalogue does not exist][/b]



That error is easily fixed: you are trying to change to a directory where you already are...:)

```
cd XFiDrv_Linux_US-1.04 && ./configure && make
```

You already are in XFiDrv_Linux_US-1.04 so CD-ing to it doesn't work and you get a simple file not found.
You probably copied these commands from the readme/howto without actually knowing what they do. That can be dangerous... ;)

---

### Post by mhenriday on 2007-10-08
Dangerous, indeed, **amtam**, even if I happen to know what the «**cd**» or «**change directory**» command does (is supposed to do) ! So dangerous, in fact, that when I tried to boot my computer this morning, it couldn't find the «bash» file that had been removed, so I had to reinstall «**Feisty**» from scratch - so can it go ! Good thing I've got that wonderful 64-bit live CD handy....

Be that as it may, I'd really like to install the **X-Fi **driver, but I feel a need for a new «how to» which _includes_ all the modifications suggested by **incidence** and others, so that I don't have to go back after following the **olausson** instructions and modify them, with the risk of inadvertently finding myself in the wrong directory and screwing things up all over again. Anybody feel up to the task ? I'm sure I'm not the only fellow user who would be very grateful indeed....

Henri

PS : **Incidence**, have you managed to straighten out your problem with the crappy sound ?...

---

### Post by NullHead on 2007-10-09
> **mhenriday said:**
> Dangerous, indeed, **amtam**, even if I happen to know what the «**cd**» or «**change directory**» command does (is supposed to do) ! So dangerous, in fact, that when I tried to boot my computer this morning, it couldn't find the «bash» file that had been removed, so I had to reinstall «**Feisty**» from scratch - so can it go ! Good thing I've got that wonderful 64-bit live CD handy....

Be that as it may, I'd really like to install the **X-Fi **driver, but I feel a need for a new «how to» which _includes_ all the modifications suggested by **incidence** and others, so that I don't have to go back after following the **olausson** instructions and modify them, with the risk of inadvertently finding myself in the wrong directory and screwing things up all over again. Anybody feel up to the task ? I'm sure I'm not the only fellow user who would be very grateful indeed....

Henri

PS : **Incidence**, have you managed to straighten out your problem with the crappy sound ?...

[This ]("http://forums.gentoo.org/viewtopic-t-587921.html")page has been updated. Theres a " if you get this problem" section now. Hope it helps :)

---

### Post by mhenriday on 2007-10-09
Thanks for the link, **Nullhead** ! Even if the procedure on the **Gentoo** site looked to me to be precisely the same as that I had tried earlier, I gave it another whirl, but no dice ; here's the final result after doing```
cd XFiDrv_Linux_US-1.04 && ./configure && make
``` > /bin/sh: cannot create .depend: Permission denied
make[3]: *** [.depend] Fel 2
make[2]: *** [_module_/home/mhenriday/XFiDrv_Linux_US-1.04/src/ossrv] Fel 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [module] Fel 2
make[1]: Leaving directory `/home/mhenriday/XFiDrv_Linux_US-1.04/src/ossrv'
make: *** [ctossrv] Fel 2
mhenriday@mhenriday-desktop:~/XFiDrv_Linux_US-1.04$ sudo make install
Password:
Copy module files...
cp: kan inte ta status på "ctossrv.ko": Filen eller katalogen finns inte
cp: kan inte ta status på "emupia.ko": Filen eller katalogen finns inte
cp: kan inte ta status på "ctsfman.ko": Filen eller katalogen finns inte
cp: kan inte ta status på "haxfi.ko": Filen eller katalogen finns inte
cp: kan inte ta status på "ctalsa.ko": Filen eller katalogen finns inte
cp: kan inte ta status på "ct20xut.ko": Filen eller katalogen finns inte
cp: kan inte ta status på "ctexfifx.ko": Filen eller katalogen finns inte
cp: kan inte ta status på "cthwiut.ko": Filen eller katalogen finns inte
make: *** [copy_modules] Fel 1

I e, the same as that I got previously. I thought that perhaps I could try to counter the «permission denied» notice in «/bin/sh: cannot create .depend: Permission denied» above by returning to my home directory and entering ```
cd XFiDrv_Linux_US-1.04 && sudo ./configure && make
```
instead of the original entry, but from what I could see this change had no effect whatsoever on the outcome. Having read through the four pages on the [[COLOR="Blue"]**Gentoo**[/COLOR]]("http://forums.gentoo.org/viewtopic-t-587921-postdays-0-postorder-asc-start-0.html") thread, my impression is that nobody there save the **OP** has succeeded in getting this procedure to work. (From what you have written, however, it does seem to have worked for you as well.) I've also gained the impression that the **OP**'s setup differs from mine, particularly in the kernel used - > Portage 2.1.3.9 (default-linux/amd64/2007.0/desktop, gcc-4.1.2, glibc-2.5-r4, 2.6.22.8 x86_64) whereas I'm still using the standard (updated) **Feisty 2.6.20.16 ** kernel. I don't know if my failure to get the procedure to work is related to this difference, but as mentioned above, I do note that others, even those using the **2.6.22** and **2.6.23** kernels, also seem to be having problems....

**Creative** seems to have thrown us a curve ball here ; I hope a lot of knowledgeable people have written to the developers there with some choice reflections on the matter....

Henri

---

### Post by NullHead on 2007-10-09
> **mhenriday said:**
> Thanks for the link, **Nullhead** ! Even if the procedure on the **Gentoo** site looked to me to be precisely the same as that I had tried earlier, I gave it another whirl, but no dice ; here's the final result after doing```
cd XFiDrv_Linux_US-1.04 && ./configure && make
``` 

I e, the same as that I got previously. I thought that perhaps I could try to counter the «permission denied» notice in «/bin/sh: cannot create .depend: Permission denied» above by returning to my home directory and entering ```
cd XFiDrv_Linux_US-1.04 && sudo ./configure && make
```
instead of the original entry, but from what I could see this change had no effect whatsoever on the outcome. Having read through the four pages on the **Gentoo** thread, my impression is that nobody save the **OP** has succeeded in getting this procedure to work. Have you ? I've also gained the impression that the **OP**'s setup differs from mine, particularly in the kernel used -  whereas I'm still using the standard (updated) **Feisty 2.6.20.16 ** kernel. I don't know if my failure to get the procedure to work is related to this difference, but as mentioned above, I do note that others, even those using the **2.6.22** and **2.6.23** kernels, also seem to be having problems....

**Creative** seems to have thrown us a curve ball here ; I hope a lot of knowledgeable people have written to the developers there with some choice reflections on the matter....

Henri

Let me clear thing up a but ... it's a howto on a gentoo forum ... it's all the same stuff you do the same things. 

ok I want you to start over please do a ```
make clean
```
when you do > Fix permissions and date on the folders and files
Code:
chmod -R 755 XFiDrv_Linux_US-1.04 && find XFiDrv_Linux_US-1.04/ -exec touch -c {} \; make sure you are root at that time ```
sudo -i
```ok after you do this > Apply XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch
Code:
wget [http://olausson.de/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch](http://olausson.de/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch) && patch -p0 < XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch

 then you have to change your "/bin/sh" in you ctsound file to "/bin/bash" then do a ```
./configure
```witch will make a Makefile.conf you need to edit this a nd add ```
-fno-stack-protector
``` to the CFLAGS near the top of the file then do a ```
make && make install
``` then start the  driver after you did all of the other steps ```
sudo /etc/init.d/ctsound start
``` then use xmms or mplayer to test your sound.

---

### Post by Flashstar on 2007-10-09
Simple question, does Gutsy work with this driver?

---

### Post by amtam on 2007-10-10
> **Flashstar said:**
> Simple question, does Gutsy work with this driver?

Simple answer: 

Yes, it does. :)

Long answer:

You wil have to re-compile your kernel with SLAB instead of SLUB. In Feisty, the default kernels were compiled with SLAB, but not so in Gutsy... :(

Or you can wait until Creative releases a new beta-driver, but I heard that could take as long as Q1 2008...

Recompiling the kernel sounds complicated, but it really isn't, if you use the config-file from the already installed and working kernel. The only thing you have to do is change SLUB into SLAB and your basically done. :)

I could write a small HOWTO how I did it if someone is interested. There are some disadvantages of running a custom kernel. One of them is that the restricted nVidia-modules don't work anymore, because they are linked to the default kernels. But you can still compile the nVidia-driver manually. It just takes a little more work.

That's the way I did it and I'm happily running the Gutsy beta with X-Fi sound :)

---

### Post by Flashstar on 2007-10-10
If you don't mind writing a tutorial, that would probably be extremely helpful since people are going to be moving to Gutsy. :popcorn:

Thanks

---

### Post by flyinraptr on 2007-10-10
Before I throw my X-fi card back into my pc and try the new beta driver .... wanted to clarify if the X-fi is fully functional using the beta driver (eg. 5.1 sound) or is it running with degraded functionality?  BTW - I'm currently running Feisty with the Gutsy 2.6.22-11 kernel.

Thanks -

---

### Post by humanity37 on 2007-10-10
I was following the instructions located here: [http://olausson.de/x-fi/readme.txt](http://olausson.de/x-fi/readme.txt)

When I got to ./configure, I received the following:

```
./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

config.log

```

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = [mypc]
uname -m = x86_64
uname -r = 2.6.20-16-generic
uname -s = Linux
uname -v = #2 SMP Sun Sep 23 18:31:23 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = x86_64
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1311: checking for gcc
configure:1327: found /usr/bin/gcc
configure:1337: result: gcc
configure:1581: checking for C compiler version
configure:1584: gcc --version </dev/null >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:1587: $? = 0
configure:1589: gcc -v </dev/null >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:1592: $? = 0
configure:1594: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1597: $? = 1
configure:1620: checking for C compiler default output file name
configure:1623: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1626: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1665: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_prog_ac_ct_CC=gcc

## ----------------- ##
## Output variables. ##
## ----------------- ##

ALSA_BUILD=''
AR=''
ARCH=''
AS=''
CC='gcc'
CFLAGS=''
CONFIG_ALPHA=''
CONFIG_ARCH_PXA=''
CONFIG_ARCH_SA1100=''
CONFIG_ARM=''
CONFIG_EXPERIMENTAL=''
CONFIG_FW_LOADER=''
CONFIG_HPET=''
CONFIG_I2C=''
CONFIG_INPUT=''
CONFIG_ISA=''
CONFIG_ISA_DMA_API=''
CONFIG_L3=''
CONFIG_MIPS=''
CONFIG_PARISC=''
CONFIG_PCI=''
CONFIG_PPC=''
CONFIG_PROC_FS=''
CONFIG_RTC=''
CONFIG_SBUS=''
CONFIG_SGI=''
CONFIG_SND_HPET=''
CONFIG_SND_KERNELDIR=''
CONFIG_SND_MVERSION=''
CONFIG_SND_RTCTIMER=''
CONFIG_SPARC32=''
CONFIG_SPARC64=''
CONFIG_VIDEO_DEV=''
CONFIG_X86=''
CPP=''
CPPFLAGS=''
CROSS_COMPILE=''
CXX=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
INSTALL_DATA=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
KLD=''
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKE_ADDS=''
NEW_KBUILD=''
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
RANLIB=''
SHELL='/bin/bash'
SRCDIR=''
ac_ct_CC='gcc'
ac_ct_RANLIB=''
alsainc=''
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${prefix}/share'
exec_prefix='NONE'
host_alias=''
includedir='${prefix}/include'
infodir='${prefix}/info'
kaversion=''
kerneldir=''
kextraversion=''
kpatchlevel=''
ksublevel=''
kversion=''
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
moddir=''
moddir_tree=''
modsubdir=''
msmp=''
oldincludedir='/usr/include'
prefix='NONE'
processor=''
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""

configure: exit 77

```

I'm just getting back into Ubuntu.  Any ideas how to remedy this?

---

### Post by amtam on 2007-10-11
Try this:

```
sudo apt-get install build-essential
```

and then try ./configure again.

---

### Post by humanity37 on 2007-10-11
Thanks, amtam; that solved the compiler error.  Now, I'm onto another error that a user experienced earlier on in this thread -- though I saw no resolution posted:

Following Make Install:

```

Copy module files...
Update module dependency relationships...
Warning: Can't not find blacklist file /etc/hotplug/blacklist
Install libs...
Install database files...
tar: creative/data/ctp073aw.dat: time stamp 2009-09-17 04:25:02 is 61054862.342486 s in the future
tar: creative/data/ctp055aw.dat: time stamp 2009-09-17 04:25:01 is 61054861.313094 s in the future
tar: creative/data/ctp046aw.dat: time stamp 2009-09-17 04:25:00 is 61054860.308471 s in the future
tar: creative/data: time stamp 2009-09-17 04:25:30 is 61054890.299068 s in the future
tar: creative/ct_reg.dat: time stamp 2009-09-17 03:58:22 is 61053262.295259 s in the future
Create device node files...
/dev/emupia already exixts
/dev/x-fi already exists
Install script files...
/etc/init.d/ctsound already exists. Overwrite it...
WARNING: Error inserting ctossrv (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctossrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting emupia (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

EDIT:  I tried to CFLAGS adjustment mentioned earlier in this thread and also in the How-To.  However, with the CFLAGS adjustment, I repeatedly lock-up partway through the Make Install process.  My cursor freezes and I get no response otherwise from the OS.

---

### Post by NullHead on 2007-10-11
> **humanity37 said:**
> Thanks, amtam; that solved the compiler error.  Now, I'm onto another error that a user experienced earlier on in this thread -- though I saw no resolution posted:

Following Make Install:

```

Copy module files...
Update module dependency relationships...
Warning: Can't not find blacklist file /etc/hotplug/blacklist
Install libs...
Install database files...
tar: creative/data/ctp073aw.dat: time stamp 2009-09-17 04:25:02 is 61054862.342486 s in the future
tar: creative/data/ctp055aw.dat: time stamp 2009-09-17 04:25:01 is 61054861.313094 s in the future
tar: creative/data/ctp046aw.dat: time stamp 2009-09-17 04:25:00 is 61054860.308471 s in the future
tar: creative/data: time stamp 2009-09-17 04:25:30 is 61054890.299068 s in the future
tar: creative/ct_reg.dat: time stamp 2009-09-17 03:58:22 is 61053262.295259 s in the future
Create device node files...
/dev/emupia already exixts
/dev/x-fi already exists
Install script files...
/etc/init.d/ctsound already exists. Overwrite it...
WARNING: Error inserting ctossrv (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctossrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting emupia (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

EDIT:  I tried to CFLAGS adjustment mentioned earlier in this thread and also in the How-To.  However, with the CFLAGS adjustment, I repeatedly lock-up partway through the Make Install process.  My cursor freezes and I get no response otherwise from the OS.

Please try my howto and let me know how it works. 
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

### Post by humanity37 on 2007-10-11
Your How-To was very helpful.  However, after adjusting the CFLAGS and attempting to Make Install, I lock up partway through.  I've repeated with the same result.  My cursor locks up and I get no respose from the OS.

---

### Post by NullHead on 2007-10-11
> **humanity37 said:**
> Your How-To was very helpful.  However, after adjusting the CFLAGS and attempting to Make Install, I lock up partway through.  I've repeated with the same result.  My cursor locks up and I get no respose from the OS.

What version of Ubuntu are you running? I've only tested on 7.04 and Debian testing or Lenny.

---

### Post by humanity37 on 2007-10-11
I'm running a pretty much fresh installation of 7.04.

---

### Post by NullHead on 2007-10-11
> **humanity37 said:**
> I'm running a pretty much fresh installation of 7.04.

I'm very sorry I don't know the problem your are having. I would go get on IRC and join freenode and #creative and talk to demik he should be able to help you.

---

### Post by humanity37 on 2007-10-11
No problem, NH.  I appreciate you trying to help.

---

### Post by Thunder Teaser on 2007-10-12
make gives me back this output, I searched the web for some sort of error, but din't find anything that suits my case.

```
LinuxSys.c:1463: warning: ‘errno’ defined but not used
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.20-16-generic/build/include -I/lib/modules/2.6.20-16-generic/build/include/asm/mach-default -I/lib/modules/2.6.20-16-generic/build/include -D__KERNEL__ -DMODULE -march=pentium -m32 -D__CT_BOUND_32BIT -c osutils.c
osutils.c: In function ‘kvirt_to_page’:
osutils.c:347: warning: passing argument 1 of ‘pmd_offset’ from incompatible pointer type
osutils.c: In function ‘myDelay’:
osutils.c:814: warning: implicit declaration of function ‘__bad_delay’
osutils.c: At top level:
osutils.c:50: warning: ‘errno’ defined but not used
ld -r ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o -o lin-ctossrv.o
ld -Ur ../../arch/i386/begin.o \
        ../../src/ossrv/lin-ctossrv.o \
        ../../arch/i386/ctossrv.a \
        ../../arch/i386/utils.a \
        ../../arch/i386/end.o -o ctossrv.o_shipped
ld: ../../arch/i386/begin.o: No such file: No such file or directory
make[1]: *** [module] Error 1
make[1]: Leaving directory `/home/tk/Packages/X-Fi/XFiDrv_Linux_US-1.04/src/ossrv'
make: *** [ctossrv] Error 2
```

Giving a make as root doesn't bypass the problem. Can anyone tell me what's the problem with begin.o?

---

### Post by amtam on 2007-10-13
You have 'just trying to help' in your sig, Garyu, but you obviously have no idea what that means...
So my little HOWTO didn't work for you. See if I care. Now nobody can use it. It was a piece of crap anyway, right?
Too bad, because it really could have helped some people. Well, at least my X-Fi is running just fine now in Gutsy.

---

### Post by Garyu on 2007-10-16
> **amtam said:**
> Edit: compiling the X-Fi driver under kernel 2.6.23 doesn't seem to work. Maybe they changed something. If you use 2.6.22-10, it still works.

Oh my God! You are so evil! :mad:

So here I am, following your howto thinking "Cool, I'll just recompile the kernel, no sweat"... And then when I get to the end of your little howto (where I used the kernel linked by YOU) I suddenly read that hey, this howto is crap and it won't work for anyone. Have fun?

Well, to be honest, my kernel is still compiling. But seriously, you found out that it doesn't work and still you only put a note in there AND AT THE END??? Bah... If this doesn't work for me, I sure hope that Thor Thunderbringer will strike at your head with lightning until it turns into charcoal, and then I hope you get run over by a hoard of elephants. But I will get back here when the kernel has compiled if it works and change this rant to something more of a praise. Because I really want to get this running in Gutsy. But I'm not very happy with you right now. :evil:

---

### Post by Garyu on 2007-10-16
> **amtam said:**
> Here you go: :)

Well, now I have tried your howto, and when I get to
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
...it runs for a while (I left it alone) and then I get lots and lots of errors about things not being folders and segmentation faults and so on...

So I still haven't even gotten around to trying with the X-Fi driver compilation.


```
mkdir: "/usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/sound/usb": Inte en katalog
cp: bearbetar "/usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/sound/usb": Inte en katalog
  INSTALL sound/usb/usx2y/snd-usb-usx2y.ko
mkdir: "/usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/sound/usb/usx2y": Inte en katalog
cp: bearbetar "/usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/sound/usb/usx2y": Inte en katalog
if [ -r System.map -a -x /sbin/depmod ]; then /sbin/depmod -ae -F System.map -b /usr/src/linux/debian/linux-image-2.6.23.1-custom -r 2.6.23.1-custom; fi
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/typhoon.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/tg3.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/starfire.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/via-velocity.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/skge.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/sunhme.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/yellowfin.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/via-rhine.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/tun.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/sundance.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/sungem_phy.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/sungem.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/sky2.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/slip.ko: Invalid argument
WARNING: Can't read module /usr/src/linux/debian/linux-image-2.6.23.1-custom/lib/modules/2.6.23.1-custom/kernel/drivers/net/slhc.ko: Invalid argument
/bin/sh: line 1: 30664 Segmenteringsfel        (core dumped) /sbin/depmod -ae -F System.map -b /usr/src/linux/debian/linux-image-2.6.23.1-custom -r 2.6.23.1-custom
make[1]: *** [_modinst_post] Fel 139
make[1]: Leaving directory `/usr/src/linux-2.6.23.1'
make: *** [install/linux-image-2.6.23.1-custom] Fel 2
root@BlueZen:/usr/src/linux# 
root@BlueZen:/usr/src/linux# 


```

EDIT: oh shoot... it turns out my harddrive is full... no space left at all, so nothing can be compiled because nothing can be stored... ho hum, how to solve this then... :-S

---

### Post by Warboy on 2007-10-19
```
TIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c emupia_guids.c
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c emupia_main.c
emupia_main.c:90: warning: ‘g_pIasOSSrv’ defined but not used
ld -m elf_x86_64 -e stext -r emupia_guids.o emupia_main.o -o lin-emupia.o
ld -m elf_x86_64 -e stext -Ur ../../arch/x86_64/begin.o \
        ../../src/emupia/lin-emupia.o \
        ../../arch/x86_64/emupia.a \
        ../../arch/x86_64/utils.a \
        ../../arch/x86_64/end.o -o emupia.o_shipped
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/XFiDrv_Linux_US-1.04/src/emupia modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/emupia/emupia.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/XFiDrv_Linux_US-1.04/src/emupia/.emupia.o_shipped.cmd for /root/XFiDrv_Linux_US-1.04/src/emupia/emupia.o_shipped
WARNING: "stack_free" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "InterlockedDecrement" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "heap_free" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "ioctl_dispatch" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "stack_alloc_page" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "unload_all_plugins" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "get_ossrv" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "stack_alloc" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "stack_free_page" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "heap_alloc" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
WARNING: "InterlockedIncrement" [/root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko] undefined!
  CC      /root/XFiDrv_Linux_US-1.04/src/emupia/emupia.mod.o
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/emupia'
cp -f /root/XFiDrv_Linux_US-1.04/src/emupia/emupia.ko .
cd /root/XFiDrv_Linux_US-1.04/src/sfman; make
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/sfman'
/root/XFiDrv_Linux_US-1.04/src/sfman/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M ctsfman_main.c   > .depend
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/sfman'
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/sfman'
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c ctsfman_main.c
ld -m elf_x86_64 -e stext -r ctsfman_main.o -o lin-ctsfman.o
ld -m elf_x86_64 -e stext -Ur ../../arch/x86_64/begin.o \
        ../../src/sfman/lin-ctsfman.o \
        ../../arch/x86_64/ctsfman.a \
        ../../arch/x86_64/utils.a \
        ../../arch/x86_64/end.o -o ctsfman.o_shipped
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/XFiDrv_Linux_US-1.04/src/sfman modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/XFiDrv_Linux_US-1.04/src/sfman/.ctsfman.o_shipped.cmd for /root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.o_shipped
WARNING: "heap_free" [/root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.ko] undefined!
WARNING: "ioctl_dispatch" [/root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.ko] undefined!
WARNING: "get_ossrv" [/root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.ko] undefined!
WARNING: "heap_alloc" [/root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.ko] undefined!
  CC      /root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.mod.o
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/sfman'
cp -f /root/XFiDrv_Linux_US-1.04/src/sfman/ctsfman.ko .
cd /root/XFiDrv_Linux_US-1.04/src/haxfi; make
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/haxfi'
/root/XFiDrv_Linux_US-1.04/src/haxfi/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M haxfi_main.c   > .depend
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/haxfi'
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/haxfi'
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c haxfi_main.c
haxfi_main.c: In function ‘haxfi_init’:
haxfi_main.c:156: warning: implicit declaration of function ‘haCore_InitDriver’
haxfi_main.c:159: warning: implicit declaration of function ‘haCore_ExitDriver’
ld -m elf_x86_64 -e stext -r haxfi_main.o -o lin-haxfi.o
ld -m elf_x86_64 -e stext -Ur ../../arch/x86_64/begin.o \
        ../../src/haxfi/lin-haxfi.o \
        ../../arch/x86_64/haxfi.a \
        ../../arch/x86_64/utils.a \
        ../../arch/x86_64/end.o -o haxfi.o_shipped
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/XFiDrv_Linux_US-1.04/src/haxfi modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/XFiDrv_Linux_US-1.04/src/haxfi/.haxfi.o_shipped.cmd for /root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.o_shipped
WARNING: "heap_free" [/root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.ko] undefined!
WARNING: "InterlockedIncrement" [/root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.ko] undefined!
WARNING: "heap_alloc" [/root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.ko] undefined!
WARNING: "get_ossrv" [/root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.ko] undefined!
WARNING: "InterlockedDecrement" [/root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.ko] undefined!
  CC      /root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.mod.o
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/haxfi'
cp -f /root/XFiDrv_Linux_US-1.04/src/haxfi/haxfi.ko .
cd /root/XFiDrv_Linux_US-1.04/src/ctalsa; make
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/ctalsa'
/root/XFiDrv_Linux_US-1.04/src/ctalsa/../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=65550 -M amidi.c amixer.c asynth.c ctalsa_main.c dummy.c pcm.c   > .depend
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/ctalsa'
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/ctalsa'
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=65550 -c amidi.c
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=65550 -c amixer.c
amixer.c: In function ‘snd_ctalsa_info_capture_volume’:
amixer.c:256: warning: unused variable ‘tMixer’
amixer.c: At top level:
amixer.c:344: warning: pointer targets in initialization differ in signedness
amixer.c:347: warning: pointer targets in initialization differ in signedness
amixer.c:353: warning: pointer targets in initialization differ in signedness
amixer.c:355: warning: pointer targets in initialization differ in signedness
amixer.c:361: warning: pointer targets in initialization differ in signedness
amixer.c:363: warning: pointer targets in initialization differ in signedness
amixer.c:369: warning: pointer targets in initialization differ in signedness
amixer.c:371: warning: pointer targets in initialization differ in signedness
amixer.c:377: warning: pointer targets in initialization differ in signedness
amixer.c:379: warning: pointer targets in initialization differ in signedness
amixer.c:385: warning: pointer targets in initialization differ in signedness
amixer.c:387: warning: pointer targets in initialization differ in signedness
amixer.c:393: warning: pointer targets in initialization differ in signedness
amixer.c:395: warning: pointer targets in initialization differ in signedness
amixer.c:401: warning: pointer targets in initialization differ in signedness
amixer.c:403: warning: pointer targets in initialization differ in signedness
amixer.c:407: warning: pointer targets in initialization differ in signedness
amixer.c:411: warning: pointer targets in initialization differ in signedness
amixer.c:413: warning: pointer targets in initialization differ in signedness
amixer.c:417: warning: pointer targets in initialization differ in signedness
amixer.c:421: warning: pointer targets in initialization differ in signedness
amixer.c:424: warning: pointer targets in initialization differ in signedness
amixer.c:428: warning: pointer targets in initialization differ in signedness
amixer.c:432: warning: pointer targets in initialization differ in signedness
amixer.c:434: warning: pointer targets in initialization differ in signedness
amixer.c:440: warning: pointer targets in initialization differ in signedness
amixer.c:442: warning: pointer targets in initialization differ in signedness
amixer.c:448: warning: pointer targets in initialization differ in signedness
amixer.c:450: warning: pointer targets in initialization differ in signedness
amixer.c:456: warning: pointer targets in initialization differ in signedness
amixer.c:458: warning: pointer targets in initialization differ in signedness
amixer.c:464: warning: pointer targets in initialization differ in signedness
amixer.c:466: warning: pointer targets in initialization differ in signedness
amixer.c:472: warning: pointer targets in initialization differ in signedness
amixer.c:474: warning: pointer targets in initialization differ in signedness
amixer.c:480: warning: pointer targets in initialization differ in signedness
amixer.c:482: warning: pointer targets in initialization differ in signedness
amixer.c:486: warning: pointer targets in initialization differ in signedness
amixer.c:491: warning: pointer targets in initialization differ in signedness
amixer.c:499: warning: pointer targets in initialization differ in signedness
amixer.c:506: warning: pointer targets in initialization differ in signedness
amixer.c:508: warning: pointer targets in initialization differ in signedness
amixer.c:512: warning: pointer targets in initialization differ in signedness
amixer.c:516: warning: pointer targets in initialization differ in signedness
amixer.c:518: warning: pointer targets in initialization differ in signedness
amixer.c:521: warning: pointer targets in initialization differ in signedness
amixer.c:525: warning: pointer targets in initialization differ in signedness
amixer.c:527: warning: pointer targets in initialization differ in signedness
amixer.c:533: warning: pointer targets in initialization differ in signedness
amixer.c:535: warning: pointer targets in initialization differ in signedness
amixer.c:538: warning: pointer targets in initialization differ in signedness
amixer.c:542: warning: pointer targets in initialization differ in signedness
amixer.c:544: warning: pointer targets in initialization differ in signedness
amixer.c:547: warning: pointer targets in initialization differ in signedness
amixer.c:554: warning: pointer targets in initialization differ in signedness
amixer.c:559: warning: pointer targets in initialization differ in signedness
amixer.c:567: warning: pointer targets in initialization differ in signedness
amixer.c:576: warning: pointer targets in initialization differ in signedness
amixer.c:583: warning: pointer targets in initialization differ in signedness
amixer.c:588: warning: pointer targets in initialization differ in signedness
amixer.c:594: warning: pointer targets in initialization differ in signedness
amixer.c:596: warning: pointer targets in initialization differ in signedness
amixer.c:599: warning: pointer targets in initialization differ in signedness
amixer.c: In function ‘get_rec_sel’:
amixer.c:638: warning: assignment from incompatible pointer type
amixer.c: At top level:
amixer.c:734: warning: pointer targets in initialization differ in signedness
amixer.c: In function ‘snd_ctalsa_put_record_mux’:
amixer.c:690: warning: ‘i’ may be used uninitialized in this function
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=65550 -c asynth.c
asynth.c:36:6: warning: backslash and newline separated by space
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=65550 -c ctalsa_main.c
ctalsa_main.c:51: warning: pointer targets in initialization differ in signedness
ctalsa_main.c:53: warning: pointer targets in initialization differ in signedness
ctalsa_main.c:55: warning: pointer targets in initialization differ in signedness
ctalsa_main.c: In function ‘ctalsa_HwObj_new’:
ctalsa_main.c:309: warning: passing argument 3 of ‘pci_read_config_byte’ from incompatible pointer type
ctalsa_main.c: In function ‘snd_ctalsa_probe’:
ctalsa_main.c:278: warning: ‘dwIOBase’ may be used uninitialized in this function
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=65550 -c dummy.c
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -DALSA_VERSION_CODE=65550 -c pcm.c
pcm.c:240: warning: ‘caculate_offset’ defined but not used
ld -m elf_x86_64 -e stext -r amidi.o amixer.o asynth.o ctalsa_main.o dummy.o pcm.o -o lin-ctalsa.o
ld -m elf_x86_64 -e stext -Ur ../../arch/x86_64/begin.o \
        ../../src/ctalsa/lin-ctalsa.o \
        ../../arch/x86_64/ctdriver.a \
        ../../arch/x86_64/utils.a \
        ../../arch/x86_64/end.o -o ctalsa.o_shipped
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/XFiDrv_Linux_US-1.04/src/ctalsa modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/XFiDrv_Linux_US-1.04/src/ctalsa/.ctalsa.o_shipped.cmd for /root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.o_shipped
WARNING: "heap_free" [/root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko] undefined!
WARNING: "ioctl_dispatch" [/root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko] undefined!
WARNING: "malloc_sizes" [/root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko] undefined!
WARNING: "heap_alloc" [/root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko] undefined!
WARNING: "__stack_chk_fail" [/root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko] undefined!
WARNING: "get_ossrv" [/root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko] undefined!
WARNING: "bytes_to_order" [/root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko] undefined!
  CC      /root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.mod.o
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/ctalsa'
cp -f /root/XFiDrv_Linux_US-1.04/src/ctalsa/ctalsa.ko .
cd /root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut; make
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut'
cd ../../../src/plugins; make
make[2]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
../../globalrules.mk:60: .depend: No such file or directory
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -M pluginutils.c   > .depend
make[2]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
gcc -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" -I../../include -isystem /lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm/mach-default -I/lib/modules/2.6.22-14-generic/build/include -D__KERNEL__ -DMODULE -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -D__CT_BOUND_64BIT -c pluginutils.c
ld -m elf_x86_64 -e stext -Ur pluginutils.o -o lin-plugin.o
make[2]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
ld -m elf_x86_64 -e stext -Ur ../../../arch/x86_64/begin.o \
        ../../../src/plugins/lin-plugin.o \
        ../../../arch/x86_64/ct20xut_ar.o \
        ../../../arch/x86_64/utils.a \
        ../../../arch/x86_64/ct20xut.a \
        ../../../arch/x86_64/end.o -o ct20xut.o_shipped
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/.ct20xut.o_shipped.cmd for /root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.o_shipped
WARNING: "InterlockedDecrement" [/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko] undefined!
WARNING: "register_plugin" [/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko] undefined!
WARNING: "heap_free" [/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko] undefined!
WARNING: "unregister_plugin" [/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko] undefined!
WARNING: "heap_alloc" [/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko] undefined!
WARNING: "__stack_chk_fail" [/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko] undefined!
WARNING: "InterlockedIncrement" [/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko] undefined!
  CC      /root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.mod.o
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut'
cp -f /root/XFiDrv_Linux_US-1.04/src/plugins/ct20xut/ct20xut.ko .
cd /root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx; make
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx'
cd ../../../src/plugins; make
make[2]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
ld -m elf_x86_64 -e stext -Ur ../../../arch/x86_64/begin.o \
        ../../../src/plugins/lin-plugin.o \
        ../../../arch/x86_64/ctexfifx_ar.o \
        ../../../arch/x86_64/utils.a \
        ../../../arch/x86_64/ctexfifx.a \
        ../../../arch/x86_64/end.o -o ctexfifx.o_shipped
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/.ctexfifx.o_shipped.cmd for /root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.o_shipped
WARNING: "heap_free" [/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko] undefined!
WARNING: "InterlockedIncrement" [/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko] undefined!
WARNING: "heap_alloc" [/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko] undefined!
WARNING: "__stack_chk_fail" [/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko] undefined!
WARNING: "unregister_plugin" [/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko] undefined!
WARNING: "register_plugin" [/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko] undefined!
WARNING: "InterlockedDecrement" [/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko] undefined!
  CC      /root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.mod.o
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx'
cp -f /root/XFiDrv_Linux_US-1.04/src/plugins/ctexfifx/ctexfifx.ko .
cd /root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut; make
make[1]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut'
cd ../../../src/plugins; make
make[2]: Entering directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/plugins'
ld -m elf_x86_64 -e stext -Ur ../../../arch/x86_64/begin.o \
        ../../../src/plugins/lin-plugin.o \
        ../../../arch/x86_64/cthwiut_ar.o \
        ../../../arch/x86_64/utils.a \
        ../../../arch/x86_64/cthwiut.a \
        ../../../arch/x86_64/end.o -o cthwiut.o_shipped
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/.cthwiut.o_shipped.cmd for /root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.o_shipped
WARNING: "InterlockedDecrement" [/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "register_plugin" [/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "heap_free" [/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "unregister_plugin" [/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "heap_alloc" [/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "__stack_chk_fail" [/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
WARNING: "InterlockedIncrement" [/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko] undefined!
  CC      /root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.mod.o
  LD [M]  /root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut'
cp -f /root/XFiDrv_Linux_US-1.04/src/plugins/cthwiut/cthwiut.ko .
root@warboy-desktop:~/XFiDrv_Linux_US-1.04# make install
Copy module files...
Update module dependency relationships...
Warning: Can't not find blacklist file /etc/hotplug/blacklist
Install libs...
Install database files...
tar: creative/data/ctp073aw.dat: time stamp 2009-09-17 05:25:02 is 60393469.503857678 s in the future
tar: creative/data/ctp055aw.dat: time stamp 2009-09-17 05:25:01 is 60393468.487883502 s in the future
tar: creative/data/ctp046aw.dat: time stamp 2009-09-17 05:25:00 is 60393467.485318055 s in the future
tar: creative/data: time stamp 2009-09-17 05:25:30 is 60393497.480190591 s in the future
tar: creative/ct_reg.dat: time stamp 2009-09-17 04:58:22 is 60391869.474756693 s in the future
Create device node files...
Install script files...
install /root/XFiDrv_Linux_US-1.04/ctsound to /etc/init.d...
./ctsound: 35: Syntax error: Bad substitution
make: *** [load] Error 2
root@warboy-desktop:~/XFiDrv_Linux_US-1.04# 
```

This is the main error from what my newbieness can see
```
./ctsound: 35: Syntax error: Bad substitution
```

Can anyone help me?

---

### Post by Warboy on 2007-10-19
```
Install script files...
/etc/init.d/ctsound already exists. Overwrite it...
/bin/sh: line 9: /sbin/chkconfig: No such file or directory
WARNING: Error inserting ctossrv (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctossrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting emupia (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@warboy-desktop:/XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04# kpatchlevel 6
-bash: kpatchlevel: command not found

```
UPDATE

this is what i get, I tried see'ing how this is resolved but, I don't understand 
<- I'm super newbie to linux lol.

---

### Post by mhenriday on 2007-10-19
**A modest proposal** : I suggest that a lot of posters to this thread have now - in the event that they had not done so previously - upgraded to **Gutsy**. I should therefore like to ask one of our more knowledgeable brethren (or sisters, as the case may be) to post a detailed tutorial which takes the procedure, step by slow step, from performing any necessary modifications to the default **Gutsy 2.6.22-14** kernel, through downloading **Creative**'s** X-Fi** driver, to carrying out the installation in such a way that the latter will work. As others have pointed out, it's been a long wait (**X-Fi** was released in August 2005), and I'm sure I'm not the only user who would be grateful, indeed, for this kind of help....

Henri

---

### Post by rapsball4 on 2007-10-22
I would love to second that idea.  I've spent a total of about 6 hours in the past two days trying to get X-Fi working on Ubuntu after installing Gutsy, and have gotten absolutely nowhere.  I've read this entire thread, and maybe somewhere in there, I just didn't know enough to see if my solution is in there - I honestly think it probably is if I could manage to sort this thread out at this point.  An organized How-To for setting it up with Gutsy would be greatly appreciated. For now, I'm finding myself accepting integrated audio for Ubuntu and the XtremeMusic will only get a chance on my rare trips to Vista.

---

### Post by justmoon on 2007-10-22
This thread contains a howto for Gutsy:
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

