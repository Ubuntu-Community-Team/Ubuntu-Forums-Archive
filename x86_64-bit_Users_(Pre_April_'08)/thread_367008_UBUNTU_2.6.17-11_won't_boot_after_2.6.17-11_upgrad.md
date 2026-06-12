---
title: "UBUNTU 2.6.17-11 won't boot after 2.6.17-11 upgrade"
date: 2007-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ulefr01 on 2007-02-21
I saw splash screen  and bar does not move but hangs.
Restart wth selecting 2.6.17-10 kernel works fine but it works not with this new kernel.
Restarting recovery gets a kernel panic
ACPI Exception , acpi_processor_0693 AE_NOT_FOUND Processor Device is not present ..
Intel Pentium D Dual Core 830 Medion MD 8808 3.0 GHZ
NVidia GeForce 6700 XL
Any help ?

---

### Post by ulefr01 on 2007-03-03
Any news ?

---

### Post by ulefr01 on 2007-05-28
solved by mkinitrd.yaird 2.6.17-11-generic -o initrd.img-2.6.17-11-generic
the update-initramfs or mkinitramfs makes a bad initrd.img ...
Same problems occured for all higher kernels.

---

