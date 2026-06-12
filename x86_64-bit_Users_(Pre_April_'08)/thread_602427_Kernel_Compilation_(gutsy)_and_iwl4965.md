---
title: "Kernel Compilation (gutsy) and iwl4965"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by sheled on 2007-11-04
Good Afternoon all.

I've installed Gutsy (AMD64 ARCH) on my Toshiba Satallite A200 Laptop about 2 weeks ago.
HWspecs:
Intel T5300, Intel Integrated Graphics (945), SATA HD, Integrated bluetooth, Pro Wireless 4965AG Wifi And RTL8101E Pci Express Ethernet, Etc.

since i am a customization freak i took a shot of compiling a new kernel. after a lot of blood, sweat and tears i've managed to compile an optimized initrd, and much more effective one.
PROBLEM IS - the original generic kernel comes with the ubuntu HW drivers. after installing numerous version of different kernels (all from synaptics), with supposedly ubuntu patches - i've come up with nothing.
the device drivers that show up in the 'make menuconfig' are standard and none of my ""Special"" hardware (eg. iwl4965) is listed.
i've searched for about 2 days on how to inject these drivers into the kernel - nothing.
these drivers do show up after i download the linux-ubuntu-modules, but i have no idea on how to integrate them into the newly compiled kernel.
currently im running the generic kernel, since i have no networking support in the newly compiled one.

any ideas?

---

