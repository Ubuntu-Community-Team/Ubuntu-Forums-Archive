---
title: "Problem with X-Fi Drivers"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by xampion on 2008-05-28
Hi, I have ubuntu 8.04 64 bits edition, my sound card is Creative X-Fi Platinum.
When I try to install the drivers make me an error. I use the tool that the drivers includes.


```
Installation is in progress. Please wait...
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
checking for directory with kernel source... /lib/modules/2.6.24-16-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.24-16-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-16-generic
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
checking for directory to store kernel modules... /lib/modules/2.6.24-16-generic/kernel/sound
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

```

---

### Post by soxs on 2008-05-28
If you were going to to compile the closed source beta driver,.. either you forget it and retunr your Xfi card to the store you bought it , or you are fine with limited oss sound opportunities aswell random crashes and alike events. If you will stick with your card, you need to set certain options to configure and make (atm search seems to be broken, so you will have to search the forum yourself.)

---

### Post by Yellow Pasque on 2008-05-28
I'd recommend finding a more Linux-friendly card. If not, you can get 2.1 analog sound with OSS4 (see my sig). Note that OSS does not randomly crash as soxs said.

---

### Post by soxs on 2008-05-28
It's not because of oss, but because of the fact that the Xfi driver is still in beta-stage.

---

### Post by pixel :-) on 2008-05-28
you used sudo?

---

### Post by Yellow Pasque on 2008-05-28
> **pixel :-) said:**
> you used sudo?
The ALSA X-fi drivers do not currently work in Hardy. He/she should run sudo make uninstall and follow the OSS4 guid in my sig.

---

### Post by go_beep_yourself on 2008-10-08
> **Temüjin said:**
> I'd recommend finding a more Linux-friendly card. If not, you can get 2.1 analog sound with OSS4 (see my sig). Note that OSS does not randomly crash as soxs said.

2.1 only and no hardware mixer? I'm really thinking this purchase was a waste, payed $100 to downgrade and mad :mad: Are there any plans to get full surround sound, at least 5.1?

---

### Post by Stenrad on 2008-10-13
Hi there!

I have a similar card to yours - XiFi Gamer Extreme - and followed the following guide:-

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675")

Hope that helps!

All the best,

Stenrad.

---

