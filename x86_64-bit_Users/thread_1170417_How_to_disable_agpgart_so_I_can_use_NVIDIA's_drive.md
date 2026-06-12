---
title: "How to disable agpgart so I can use NVIDIA's driver?"
date: 2009-05-26
forum: x86 64-bit Users
---

### Post by stodge on 2009-05-26
I'm trying to reconfigure Linux to disable the default agpgart module so I can use NVIDIA's driver. I believe this is the reason why my computer runs Ubuntu so slowly.

I followed these instructions:

[http://linuxtechie.wordpress.com/tag/nvidia/](http://linuxtechie.wordpress.com/tag/nvidia/)

And added the following to /etc/modprobe.d/blacklist

blacklist agpgart

I changed xorg.conf to include:

Option  "Nvagp" "1"

And rebooted.

But it's not working. I see the following in dmesg:

[    0.004000] AGP bridge at 00:00:00
[    0.004000] Aperture from AGP @ f0000000 old size 32 MB
[    0.004000] Aperture from AGP @ f0000000 size 32 MB (APSIZE 0)
[    0.467626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.540121] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    0.540126] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.544815] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    1.244148] Linux agpgart interface v0.103
[   24.617831] NVRM: not using NVAGP, an AGPGART backend is loaded!

My hardware:

MSI NEO2 K8N
2Gb
NVIDIA 6600GT
200Gb SATA

Any suggestions?

Thanks

---

### Post by stodge on 2009-05-26
I forgot to include the AGP status:


cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

---

### Post by Slim Odds on 2009-05-26
I use this in my /boot/grub/menu.lst

```
# defoptions=quiet splash [COLOR=Sienna]iommu=noagp,noaperture[/COLOR] 
```

---

