---
title: "[SOLVED] having trouble getting sound thru x-fi 9000 audio"
date: 2008-12-25
forum: x86 64-bit Users
---

### Post by Rrasyrogenees on 2008-12-25
tyia... having tried ubuntu maybe a year ago and had problems because there wasn't a driver for the sound card i have but i have looked now and the sites i read said that that driver is available.  :biggrin:

that being said... now i cannot figure out which driver i need and how to install it:confused:... being still a noob to ubuntu (using xp and thank god not vista).  let me know what info i need to give to help this along because i can't remember past a week ago about what i did a year ago (but never did get sound).

---

### Post by Rrasyrogenees on 2008-12-25
i added a few more applications and now i seem to have a working devise manager... i am still :confused: but now i know for a fact that the computer recognizes the x-fi 9000 audio board... it is listed under PCI Bridge as an Audio Controller... still no sound yet.

---

### Post by Rrasyrogenees on 2008-12-25
now i have done a little more research and found the driver... but when i look to the kernel to see where to put it...

rrasyrogenees@ubuntu:~$ sudo apt-cache search kernel-source
[sudo] password for rrasyrogenees: 
xserver-xorg-input-wacom - X.Org X server -- Wacom input driver
fglrx-kernel-source - Kernel module source for the ATI graphics accelerators
nvidia-173-kernel-source - NVIDIA binary kernel module source
nvidia-177-kernel-source - NVIDIA binary kernel module source
nvidia-71-kernel-source - NVIDIA binary kernel module source
nvidia-glx-173 - NVIDIA binary Xorg driver
nvidia-glx-177 - NVIDIA binary Xorg driver
nvidia-glx-71 - NVIDIA binary Xorg driver
cpad-common - common files to support the Synaptics cPad driver kernel modules
cpad-kernel-source - source for the Synaptics cPad driver
oprofile - system-wide profiler for Linux systems
nvidia-96-kernel-source - NVIDIA binary kernel module source
nvidia-glx-96 - NVIDIA binary Xorg driver
rrasyrogenees@ubuntu:~$ 

... i don't see the x-fi listed... hmmm

this is the Read ME file for the driver...
====================================================================


  Sound Blaster X-Fi Linux 32/64-bit Driver Source Release Readme File

  September 2008


====================================================================


The purpose of this document is to describe how to build and install the 
X-Fi Linux device driver.






Quick install


=============

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install



Uninstall

=========

In terminal,

1) Goto source directory

2) Execute make command as root

   make uninstall





Copyright (c) 2008 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================

---

### Post by Rrasyrogenees on 2008-12-25
and i am back with more good news... (sarcasm this time)

rrasyrogenees@ubuntu:~$ cat /proc/asound/cards
 1 [U0x46d0x8ce    ]: USB-Audio - USB Device 0x46d:0x8ce
                      USB Device 0x46d:0x8ce at usb-0000:00:02.1-9, high speed
rrasyrogenees@ubuntu:~$ 


no x-fi showing in here but it shows in the device manager on the pci slot

---

### Post by Rrasyrogenees on 2008-12-25
now i found where my soundcard is thru the devic manager and the linus syssf_path is 

rrasyrogenees@ubuntu:~$ mount /sys/devices/pci0000:00/0000:00:09.0/0000:01:08.0mount: can't find /sys/devices/pci0000:00/0000:00:09.0/0000:01:08.0 in /etc/fstab or /etc/mtab
rrasyrogenees@ubuntu:~$ 

 but still does not recognise it... am i missing a step or four to do what i am trying to do?  do i need to install the driver first or what?

---

### Post by Rrasyrogenees on 2008-12-25
one more thing i found and i know i am getting close but i am having trouble with basics...

ctxfi-objs := xfi.o ctatc.o ctvmem.o ctpcm.o ctmixer.o ctresource.o ctsrc.o ctamixer.o ctdaio.o ctimap.o cthardware.o cthw20k2.o cthw20k1.o
        
obj-m += ctxfi.o

ifeq ($(DEBUG), y)
CFLAGS += -g -DDEBUG
endif

KERNELDIR 	?= /lib/modules/$(shell uname -r)/build
PWD		:= $(shell pwd)

all:
	$(MAKE) -C $(KERNELDIR) M=$(PWD)

clean:
	rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions

PHONY := install uninstall

MODDIR = $(PWD)
MODPATH	= /lib/modules/`uname -r`/kernel/drivers/ssound
MODULES = ctxfi.ko

install:
	@echo "Copy module files..."
	@rm -rf $(MODPATH)
	@mkdir $(MODPATH)
	@cd $(MODDIR)/; cp -f $(MODULES) $(MODPATH)/
	@echo "Update module dependency relationships..."
	@/sbin/depmod
	@/sbin/modprobe ctxfi

users := $(word 3, $(shell /sbin/lsmod | grep ^ctxfi | head -n 1))
uninstall:
	@if [ "$(users)" = "0" ]; then \
		echo "Unload ctxfi..."; \
		/sbin/modprobe -r ctxfi; \
	fi
	@echo "Remove module files..."
	@rm -rf $(MODPATH)
	@echo "Update module dependency relationships..."
	@/sbin/depmod

.PHONY: $(PHONY)

---

### Post by Rrasyrogenees on 2008-12-27
I FINALLY FOUND MY ANSWER... i found a thread that gave all i needed to get my soundcard working... now i cannot remember the thread but it had "creative x-fi" in the title

---

