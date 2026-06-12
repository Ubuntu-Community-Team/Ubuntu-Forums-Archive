---
title: "nForce 3 AGP help"
date: 2005-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by acariquara on 2005-09-20
cat /proc/drivers/nvidia/agp/status 0

--> disabled

At boot time I got this error

[  120.145505] agpgart: Detected AGP bridge 0
[  120.146018] agpgart: Aperture conflicts with PCI mapping.
[  120.146034] agpgart: Aperture from AGP @ f8000000 size 4096 MB
[  120.146038] agpgart: Aperture too small (0 MB)
[  120.146047] agpgart: No usable aperture found.
[  120.146058] agpgart: Consider rebooting with iommu=memaper=2 to get a good aperture.

also later I got this one:

[  175.201868] NVRM: not using NVAGP, kernel was compiled with GART_IOMMU support!!
[  177.773834] NVRM: not using NVAGP, kernel was compiled with GART_IOMMU support!!

I already tried to add iommu=memaper=2 to grub parameters but that did not help.

Mobo Gigabyte GA-K8NS (nForce3 ultra 250)
GeForce2 MX200

---

### Post by DancingSun on 2005-09-20
Not sure if I remembered this correctly or not, since I'm on a PCI-E board now.  But I believe there's a BIOS setting on AGP aperture, you might want to see if that's causing you any problems.

BTW, when did this problem manifested?  Did you change anything on your system?

---

### Post by acariquara on 2005-09-20
No, it happens as soon as I install it. I tried everything inside the BIOS, no change... Older mobos have "agp aperture size" or something like this but this specific one does not have it.

I could get it to work by recompiling the kernel and remove IOMMU support but that borked my installation (getting nvidia video drivers to work again was a pain in the neck)

---

### Post by DancingSun on 2005-09-20
[QUOTE=acariquara]No, it happens as soon as I install it. I tried everything inside the BIOS, no change... Older mobos have "agp aperture size" or something like this but this specific one does not have it.

I could get it to work by recompiling the kernel and remove IOMMU support but that borked my installation (getting nvidia video drivers to work again was a pain in the neck)[/QUOTE]
Hehe, so, you found out my previous motherboard was *old* heh?  It was a Socket-A Abit mobo, lol.

Does the Ubuntu LiveCD work?

---

### Post by acariquara on 2005-09-21
I haven't tried LiveCD but I just reinstalled Breezy from 20092005 daily build, same thing happens at first boot.

Booting with iommu=memaper=2 does not help.

---

