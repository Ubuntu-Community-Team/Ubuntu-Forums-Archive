---
title: "Wine not recognising NVIDIA GT640"
date: 2012-10-16
forum: Wine
---

### Post by TheSqueak on 2012-10-16
Wine Version: wine-1.5.15
Kubuntu 12.04
Nvidia driver: 304.51

lspci output:
```
07:00.0 VGA compatible controller: NVIDIA Corporation Device 0fc1 (rev a1) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 83f3
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at c000 [size=128]
        [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nouveau, nvidiafb
```



I have a GeForce GT640 with 2Gb of RAM installed in my desktop, but Wine for some reason refuses to recognise the card, with the result that i'm having major issues trying to get any games to work.

According to the output from Steam, Wine thinks i'm running a GeForce 8300GS with a whole 128MB of VRAM.



Is this a known problem with a fix somewhere, or do I need to log a wine bug?

---

