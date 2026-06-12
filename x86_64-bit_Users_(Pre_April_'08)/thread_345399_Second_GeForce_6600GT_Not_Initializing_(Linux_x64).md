---
title: "Second GeForce 6600GT Not Initializing (Linux x64)"
date: 2007-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by MyDalRiley on 2007-01-24
Hello all!

I have been googling and searching the ubuntu / nvidia forums for help on this and have had no luck.

Hardware
Tyan K8WE
Dual AMD Opteron 246's (2.0 GHz)
2GB RAM

Software
Kubuntu 6.10 Edgy Eft
Kernel Linux 2.6.17-10 x64
Xorg 7.1.1
Nvidia 1.0.9746

Trying to get the two cards setup in SLI mode similar to windows (which works fine).

Xorg.0.log reports a) that there is no device section for the nVidia card at PCI:129:0:0 despite the fact that there is the proper DEVICE section in my xorg.conf file and b) Xorg.0.log then reports that the graphics card at 129:0:0 failed to initialize so SLI cannot start.

Another interesting fact: lspci shows the cards on 2:0:0 and 81:0:0 while xorg shows 2:0:0 and 129:0:0. What's up with that?

I have attached the xorg.conf and lspci output for my machine. If they didn't attach, I am posting the relevant sections below. I have also attached the relevant Xorg.0.log file detials.

Any help is greatly appreciated!

Thanks in advance!

Scott

===================

Here are the device sections from xorg.conf

Section "Device"
Identifier "Card0"
Driver "nvidia"
VendorName "nVidia Corporation"
BoardName "NV43 [GeForce 6600 GT]"
BusID "PCI:2:0:0"
Option "SLI" "Auto"
EndSection

Section "Device"
Identifier "Card1"
Driver "nvidia"
VendorName "nVidia Corporation"
BoardName "NV43 [GeForce 6600 GT]"
BusID "PCI:129:0:0"
EndSection

Relevant lspci data

02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
81:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

Here are relevant sections from the Xorg.0.log

(--) PCI:*(2:0:0) nVidia Corporation NV43 [GeForce 6600 GT] rev 162, Mem @ 0xc40
00000/26, 0xc8000000/27, 0xc1000000/24
(--) PCI: (129:0:0) nVidia Corporation NV43 [GeForce 6600 GT] rev 162, Mem @ 0x9
8000000/26, 0x90000000/27, 0x9c000000/24

(II) NVIDIA dlloader X Driver 1.0-9746 Fri Dec 15 10:21:43 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Assigning device section with no busID to primary device
(WW) NVIDIA: No matching Device section for instance (BusID PCI:129:0:0) found
(--) Chipset NVIDIA GPU found

II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "SLI" "Auto"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): NVIDIA SLI auto-select rendering option.
(WW) NVIDIA(0): DamageEvents are not currently compatible with SLI. Disabling
(WW) NVIDIA(0): DamageEvents.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:129:0:0.
(EE) NVIDIA(0): Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0): additional information.
(EE) NVIDIA(0): Failed to initialize one NVIDIA graphics device!
(WW) NVIDIA(0): Failed to initialize SLI! Reason: One GPU failed to
(WW) NVIDIA(0): initialize; Only one GPU will be used for this X screen.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.16.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:2:0:0:
(--) NVIDIA(0): Sharp LL-173C-B (CRT-0)

---

### Post by kuja on 2007-01-24
Hmm, I've got an idea, not sure if it will work though. Seeing as lspci says the busid is 81, why not change the xorg.conf file to match and see what happens? Also, is there any reason you're using the 97xx beta drives as opposed to the 9631(stable) or ?8762?(old stable)? Have you tried it with those?

---

### Post by MyDalRiley on 2007-01-24
> **kuja said:**
> Hmm, I've got an idea, not sure if it will work though. Seeing as lspci says the busid is 81, why not change the xorg.conf file to match and see what happens? Also, is there any reason you're using the 97xx beta drives as opposed to the 9631(stable) or ?8762?(old stable)? Have you tried it with those?

I have tried specifying PCI:81:0:0 and I get the same output in the Xorg log (no device section for the device at PCI:129:0:0 and I believe the same device failed to initialize error).

I downloaded the latest drivers from nVidia's site.  Doesn't say anything about being "beta".  Willing to try anything 

Version: 1.0-9746
Operating System: Linux x64 (AMD64/EM64T)
Release Date: December 21, 2006

The nVidia drivers from Automatix 2 were 1.7xxxx so I tried to install the latest from nvidia.  Tonight or tomorrow I will re-install and try the 1.0-9746 immediately after the install / package update so the install is still clean at that point.  Don't expect any changes, but....

Thanks for the reply!

Scott

---

### Post by asusguy175 on 2007-01-26
i don't have those exact cards (i have dual 7950s, and i wanted to know if i could get ubuntu working in SLi..... does ti work the same way? (please explain)

---

### Post by MyDalRiley on 2007-01-26
> **MyDalRiley said:**
> The nVidia drivers from Automatix 2 were 1.7xxxx so I tried to install the latest from nvidia.  Tonight or tomorrow I will re-install and try the 1.0-9746 immediately after the install / package update so the install is still clean at that point.  Don't expect any changes, but....



I did a clean install and am receiving the same errors in Xorg.0.log.  SLI is enabled and running in XP as confirmed by the nvidia sys tray monitor (it tells me so on every startup).

Am now at a loss as to what to try next.  

Anyone?

Scott

---

### Post by Ocxic on 2007-01-26
on my motherboard there are sets of jumpers i must reconfigure in order to get sli working, this could be the same for your mobo, check your instruction booklet

---

### Post by MyDalRiley on 2007-01-26
> **Ocxic said:**
> on my motherboard there are sets of jumpers i must reconfigure in order to get sli working, this could be the same for your mobo, check your instruction booklet

If the SLI features are working in XP, there should be no need for jumpers to be set on the Mobo, right?  Just checked the Mobo manual and there is no jumper related to the PCI-Express cards or nVidia SLI.

Will keep searching.....Thanks!

Scott

---

