---
title: "Can't install Soundblaster X-Fi Xtreme Gamer Drivers"
date: 2008-09-26
forum: x86 64-bit Users
---

### Post by ChancreSore on 2008-09-26
Hi,

I'm new to Ubunto (and all Linux for that matter). I'm trying to install the drivers for my soundcard (X-Fi Xtreme Gamer). I tried the OSS way, then reverted back to ALSA. I have a red X on my speaker icon near the clock (is that called the system tray in Linux as well?). I downloaded XFiDrv_Linux_US-1.18.tar.gz from Creative's website, and unzipped it to my desktop. Then I typed "sudo" into terminal and dragged "installer" from the unzipped folder to terminal and hit enter. I got some user agreement and read me type stuff, answered Yes to all of it, then it installed. Here is everything after the Read Me bit:

```
Installation is in progress. Please wait...
tar: /home/jeff/XFiDrv_Linux_US-1.18.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
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
checking for current directory... /opt/Creative/XFiDrv_Linux_US-1.18/drivers
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-19-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.24-19-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-19-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
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
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-19-generic/kernel/sound
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for SMP... yes
checking for Video device support in kernel... yes
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
checking for video_get_drvdata... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for Procfs support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new unlocked/compat_ioctl... no
configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful
jeff@XPSDesktop:~$ 
```

I've searched about how to get my sound working (which lead me to try OSS) but I have come to the conclusion that I need to be walked through this as much as possible.

Any help would be much appreciated!

Thanks,

Jeff

---

### Post by lewisskinner on 2008-12-15
Any help here?  I have the X-Fi Xtreme as well, downloaded the XFiDrv_Linux_Public_US_1.00.tar.gz package but also got a failure

here is output.  **[COLOR="Red"]red bold text[/COLOR]** is my inputs (as directed by the creative site)

```
lewis@Arcadia:~/Desktop/XFiDrv_Linux_Public_US_1.00$ [COLOR="Red"]**sudo make**[/COLOR]
make -C /lib/modules/2.6.24-22-generic/build M=/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  LD      /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.o
/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
  CC      /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/lewis/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
lewis@Arcadia:~/Desktop/XFiDrv_Linux_Public_US_1.00$ [COLOR="Red"]**sudo make install**[/COLOR]
Copy module files...
Update module dependency relationships...
make: *** [install] Segmentation fault
lewis@Arcadia:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 

```

---

### Post by Bal_Zac on 2008-12-15
Are you using 8.04?  Because IIRC, the new open source driver from creative requires atleast the 2.6.27 kernel.  If you upgrade to 8.10, which has the 2.6.27 kernel, you can use it, and it works great with 8.10 by the way.

---

### Post by lewisskinner on 2008-12-16
Oh right! Wish someone had told me this before!

I'm on Hardy at the moment (I prefer LTS) running 2.6.24-22-rt (I use the studio), but would certainly consider Intrepid if my SB X-Fi would work!  I'm currently having to use Propellerheads Reason 4 on Windows Virista for my audio production[img]http://www.skyscrapercity.com/images/smilies/puke.gif[/img]

Can I get the 2.6.27 kernel on Hardy, or should I bite the bullet and upgrade to Intrepid?  Will it work on the low-latency kernel?

For Hardy, I've seen an OSS driver (but stereo only) or a workaround for ALSA (involves recompiling the kernel).  How is the 5.1 with IIRC, bal_zac?  I'm currently mid-way through option (b).  Wish me luck!:S

If I upgrade, what commands do I use to install this magical IIRC?

---

### Post by wd5gnr on 2008-12-16
Yes I upgraded to Intrepid for just this reason and it does work:
[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

All you really need is the new kernel I think, but the upgrade was moderately painless. Most of the pain was moving from kde4 as an "add on" to "real" kde4.

---

### Post by lewisskinner on 2008-12-16
> **wd5gnr said:**
> Yes I upgraded to Intrepid for just this reason and it does work:
[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

All you really need is the new kernel I think, but the upgrade was moderately painless. 

Thanks for your help

> **wd5gnr said:**
> Most of the pain was moving from kde4 as an "add on" to "real" kde4.
Care to elaborate?  I like kde, and have kde4 working fine on Hardy (at least I seem to have!)

---

### Post by wd5gnr on 2008-12-16
Well the new installation uses ~/.kde for KDE 4 settings (I guess KDE3 isn't an option). The KDE4 "remix" uses ~/.kde4. So when I rebooted I got a whole new desktop/menu/etc. I took a chance and backed up ~/.kde and then replaced it with ~/.kde4. No real problems with that. In addition, I had some packaging problems where I had some xxx and xxx-kde4 packages (remove the -kde4 packages) and also in some cases where I didn't get yyy because I already had yyy-kde4 (uninstall yyy-kde4 and install yyy). Don't know if those really caused any issues or not but all seems ok.

---

### Post by lewisskinner on 2008-12-19
OK, so I upgraded to Ubuntu Intrepid, kernel 2.6.27-9-generic (for now, I'm going to try the low-latency if I can get this to work)

How do I install the SB X-Fi Xtreme drivers?

---

### Post by wd5gnr on 2008-12-19
Instructions linked on post #5 above.

---

