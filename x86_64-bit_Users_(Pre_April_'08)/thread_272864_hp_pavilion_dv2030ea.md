---
title: "hp pavilion dv2030ea"
date: 2006-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by tsr on 2006-10-07
[edit]
Ok, I rebooted my adslmodem and the connection went up, after some tweaking I got it to a reasonable state.

A lot has worked out of the box, some needed some tweaking (nvidia driver, wifi-driver) and some just don't work with the current software options: webcam - there is a another thread for that)

Case closed!

/tsr
[/edit]

Hi,

I'm having trouble installing the 64bit version of ubuntu 6.06 on my friends laptop.

The 32bit version seems to work fine, at least the network card is working fine (I am using that live CD now).

The screen resolution is a problem regardless of what version I try, but that is ok, the big concern is that with both the standard and the alternate .iso of the 64bit version the network card is not recognised.

I am not completely sure of the hardware configuration in this laptop, the hp site sais:

-Processor: AMD Turion™ 64 X2 Mobile-technology TL-52, level 2-cache 512 KB +512 KB.
-RAM: 1024 MB, DDR2 533 MHz (2 x 512 MB)
HD: 80 GB (EIDE-hårddisk, SATA, 5400 rpm)
Optical device: Lightscribe Super Multi DVD-brännare (+/-R +/-RW) with support for double layers.
Network: 10/100 Mbit/s nätverksstöd
Wireless: 802.11a/b/g WLAN
Screen:	14,1-inch WXGA High Definition BrightView widescreen
Screenresolution: 1280 x 800
Videocard: NVIDIA® GeForce™ Go 6150
Video-RAM: Up to 128 MB shared memory

The ubuntu device manager sais:
-Processor: something about a K8 - Athlon64/Opteron
-Optical device: HL-DT-ST DVDRAM GMA-4082N
-Ethernet controller: MPCI51, capabilities net, net.80203
(it sais something different about eth0 when using the standard 64bit version of the live CD)

I get some wierd error, something like IOCFLAGS (but longer) when trying to connect under 64bit. There where no /etc/resolv.conf file after installing the standard 64bit version, using the alternate had a /etc/resolv.conf but gave same error when trying to connect using the eth0 adapter (this is the wired adapter, I do not have use for the wireless just yet).

Any hints, pointers, etc, would be very much appreciated, thanks,
Tomas

---

