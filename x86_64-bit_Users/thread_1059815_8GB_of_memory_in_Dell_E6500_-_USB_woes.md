---
title: "8GB of memory in Dell E6500 - USB woes"
date: 2009-02-04
forum: x86 64-bit Users
---

### Post by ncubede on 2009-02-04
I got a new Dell E6500 with 8G of RAM and a Core2Duo CPU, so installed Ubuntu Intrepid x86_64 and it looked good for the first few minutes. Then things started to be strange: when the display went to sleep, the laptop locked up, so I disabled that, but every hour or so the UHCI reported:

Feb  3 15:57:09 stephan-laptop kernel: [  949.346666] uhci_hcd 0000:00:1d.0: host controller process error, something bad happened!
Feb  3 15:57:09 stephan-laptop kernel: [  949.346693] uhci_hcd 0000:00:1d.0: host controller halted, very bad!
Feb  3 15:57:09 stephan-laptop kernel: [  949.346723] uhci_hcd 0000:00:1d.0: HC died; cleaning up

After a bit of reading, this looked like a DMA32 bug, so I upgraded the kernel to intrepid-proposed: 2.6.27-11-generic, still bad.

As a last resort, I added mem=4000m to the kernel parameters and things are looking a lot more stable now. Throwing away half my memory does not make me happy, though.  I start to think it may be better to go back to x86 with PAE.

Is this a known issue someplace?  I'd have expected the kernel to take care of only allocating 32bit DMA addresses, especially if the hw only supports 32bit addresses.

---

### Post by ncubede on 2009-02-04
HW BOM:
Dell Latitude E6500
Intel Core 2 Duo P9500 (2.53GHz,1066MHz,6MB)
256MB Nvidia Quadro NVS 160M Graphic Card
15.4in Widescreen WUXGA (1920X1200)
Memory : 8192MB (2x4096) 800MHz DDR2 Dual Channel
Wireless : Intel WiFi Link 5300 (802.11 a/b/g/n 3X3)

Please note, that I even disabled all WIFI+Bluetooth in the BIOS and only had a single mouse attached (various, actually) and still had the same issue.

---

### Post by ncubede on 2009-04-01
In the end the only thing that really made the system completely stable was the BIOS upgrade E6500 A18, which made the system rock solid at last.
Apparently there are known USB and overheating issues with the E6500 series, which are only resolved with this BIOS version.  I'd say this BIOS is 
a must have for the E6500.

---

