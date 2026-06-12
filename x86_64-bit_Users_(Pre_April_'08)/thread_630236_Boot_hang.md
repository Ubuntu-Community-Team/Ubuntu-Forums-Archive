---
title: "Boot hang"
date: 2007-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ljkwesi on 2007-12-03
Hello,

I have recently upgraded my system from Feisty Fawn to Gusty Gibbon, making the switch from 32 bits to 64 bits at the same occasion, and I have to admit it is disappointing... Booting is extremly slow, and even though I have searched through forums and google, I haven't been able to get a definitive answer... While Feisty also had boothang issues, they were easily fixed by ide=nodma (yes, my hard disks are old), but it has no effect on the Gutsy boot.

Through Ctrl+Alt+F1, I get this message :
> [35.868458] PCI : Cannot allocate resource region 0 of device 0000:00:00.0

I used lspci -v in terminal, and I get this :
> mister@kingston:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at <ignored> (32-bit, prefetchable)
        Capabilities: <access denied>

What should I do ? Solutions in other forums speak of disabling acpi and so on, but it seems to me this is unrelated. Besides I already tried, it only made booting worse. Others speak of upgrading the BIOS, but I'm really reluctant to do it (I really feel uneasy flashing my BIOS...) Any ideas for a lost soul in the sea of Linux problems ?

Thanks in advance.

PS. My system config is :
AMD Athlon 64 3000+ on MSI K8N-Neo2 Platinum board
1024Mb RAM
ATI Radeon Graphics Card (128Mb)

---

### Post by ljkwesi on 2007-12-03
Ok, so you can disregard the first post... After disabing the *quiet splash* boot options, I found that the boot hang issue was still related to dma timeout problems. Under Feisty, I fixed the issue with *ide=nodma* but it seems to have no effect whatsoever under Gutsy... Any clues ?

---

