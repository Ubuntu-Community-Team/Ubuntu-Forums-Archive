---
title: "Sound Blaster XFi driver installer not working"
date: 2009-02-03
forum: x86 64-bit Users
---

### Post by ieduarte73 on 2009-02-03
Hello,

I have a Dell Dimension XPS 710 which has a SB XFi audio adapter, I found a driver (beta) for 32/64-bit, but when I try to run the installer I get an error 2, and the installation doesn't go through (I am using Ubuntu Intrepid Kernel 2.6.27.11-generic).

This is the installer output:

====================================================================

  Sound Blaster X-Fi Linux 32/64-bit Beta Driver Readme File

  April 2008

====================================================================

The purpose of this document is to describe how the X-Fi Linux device 
driver is built, packaged, and released.



Quick install

=============


1) You must have the fully configured source for the Linux kernel and 
   ALSA which you
 want to use for this device driver. Partial installed 
   kernels (e.g. From distribution makers) may be unusable for this 
   action.
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
checking for directory with kernel source... /lib/modules/2.6.27-11-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.27-11-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.27-11-generic
checking for GCC version... ./configure: eval: line 3527: syntax error near unexpected token `)'
./configure: eval: line 3527: `my_compiler_version=4.3.2-1ubuntu12)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2

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
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.27-11-generic/kernel/sound
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

Any ideas ?

---

### Post by rv65 on 2009-02-04
Don't use that driver since it's obsolete. Creative updated their Linux X-fi driver. You can do sudo make uninstall and install the latest one. The latest one is now Open Source. You could blacklist ALSA and go with OSS. The latest creative X-Fi driver for Linux came out in November of last year. Then again I tried that driver and it doesn't work for 8.04 so it won't work with 8.10. 

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

This is the link to get the newest driver for the X-fi. 

I hope you can get your X-Fi working. I just gave up with the creative stuff and went to OSS. I haven't tried that one yet so I don't know if it works. Hope this helps.

---

### Post by rv65 on 2009-02-06
One limitation of Linux X-Fi is that you can't get surround sound to work. I believe there is a work around which might work but I just use stereo.

---

