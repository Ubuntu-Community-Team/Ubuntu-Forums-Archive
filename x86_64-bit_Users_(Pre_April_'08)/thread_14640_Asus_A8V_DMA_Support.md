---
title: "Asus A8V DMA Support?"
date: 2005-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by FluffyElmo on 2005-02-08
I have an Asus A8V (K8T800) and after installing Ubuntu 64 I'm having an issue with disk support. Copying files between drives is extremely slow and uses ~40-80%CPU. 

Upon investigation, all drives are set to 16bit and DMA is disabled. Enabling them via hdparm doesn't work with available kernel (generic and k8), explicitly enabling 32bit DMA support in the BIOS doesn't help either.  

Everything else works perfectly, so I'd like to solve this if possible. Any help appreciated...I've listed more information below if it's any help.

Processor: Athlon64 3400+
Motherboard: Asus A8V Deluxe
Memory: 1 gig dual channel
Hard Drive: 120 Maxtor SATA, 2 40gb Matrox IDE 
DVD: NEC 3500A IDE

The results of hdparm:

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 14946/255/63, sectors = 122942324736, start = 0

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 41110142976, start = 0

/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 41110142976, start = 0

/dev/hdc: 
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

---

### Post by FluffyElmo on 2005-02-08
Oh, and I'm running fully updated Hoary, kernel version 2.6.8.10-4.

Thanks

---

### Post by AndersAA on 2005-02-09
hm, chances are you'd need a kernel patch or something.

---

### Post by FluffyElmo on 2005-02-09
I was afraid it might come to that. I'll look into how to build a kernel when I get home this evening.

I've also noticed an error at boot where it can't get the system time. Wondering if maybe it's just not reading the BIOS values and is trying failsafes.

---

### Post by AndersAA on 2005-02-09
[QUOTE=FluffyElmo]I was afraid it might come to that. I'll look into how to build a kernel when I get home this evening.

I've also noticed an error at boot where it can't get the system time. Wondering if maybe it's just not reading the BIOS values and is trying failsafes.[/QUOTE]

I get that error too, and it's not critical.

---

### Post by FluffyElmo on 2005-02-19
Solved, finally...and it was so simple it's almost embarrassing. With an unmodified Ubuntu kernel, simply add 'via82cxxx' to /etc/modules before the generic ide modules.

```
sudo nano /etc/modules

...
via82cxxx
ide-cd
ide-disk
ide-generic
...
``` 

After a reboot, this enabled 32-bit IO and DMA on both hard disks and 32bit IO on the DVD burner. I can enable DMA (and other settings) on the dvd burner using hdparm. 

Hopefully this will save someone else with this problem some time...I spent more time learning how to build custom kernels, and building them, than I ever wished to  :?

---

