---
title: "Getting graphics card memory range"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by soxs on 2008-08-09
Hi
I need to know where the mapping of my memory starts, but I am not going to loose my system stability by passing wrong values to /proc/mtrr.
SO here is the output from lspci --v, but I seem to be unable to read out the correct lines, and as this is my main system, I will not do try&error.

lspci -vv
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870 (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Unknown device 2244
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at fe7f0000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at 9000 [size=256]
	Expansion ROM at fe7c0000 [disabled] [size=128K]
	Capabilities: <access denied>
```

cat /proc/mtab
```
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 256MB: write-back, count=1

```

The reason I want to add a line for my graphics card, is caused by the bug, it only aknowledges 50% of the videoram, which sucks,especially when it comes to playing texture intense games like ETQW (using megatextures > 200 MiB).

see here for more info: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/247887](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/247887)

---

### Post by soxs on 2008-08-10
Ok, I got it being 0xd0000000, but I need to know how to make it persistant in mtrr.
Using nano I can save, but 1s later after reoping it got reset.

I tried:
```
sudo echo "base=0xd0000000 size=0x20000000 type=write-combining" >| /proc/mtrr
```
but this only throws an error at me:
```
echo: WriteError: Invalid argument
```

EDIT:
I tried 0x**e**0000000 as base address and it worked.. seems that only powers of 2 are allowed as base address (though 0xc0000000 isn't a power of 2 ???), but how can I then set it according to 0x**d**0000000

Anyone..

---

### Post by soxs on 2008-08-10
Add:
fglrx related loading stuff from /var/log/Xorg.0.log:
```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x7f7d70
(II) fglrx(0): === [atiddxPreInit] === begin
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "1"
(**) fglrx(0): Option "OpenGLOverlay" "0"
(**) fglrx(0): Option "VideoOverlay" "1"
(**) fglrx(0): Option "UseInternalAGPGART" "1"
(**) fglrx(0): Option "TexturedVideo" "1"
(**) fglrx(0): Option "TexturedVideoSync" "1"
(**) fglrx(0): Option "Textured2D" "1"
(**) fglrx(0): Option "TexturedXrender" "1"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3870" (Chipset = 0x9501)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x2244)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe7f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.79
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV670
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x20000000)
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR4
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information. 
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 24 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)

# BUNCH OF MODELINES REMOVED

(==) fglrx(0): NoAccel = NO
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.50.3
(II) fglrx(0):     Date: Jun  2 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01040000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3328)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2304
(**) fglrx(0): Option "BackingStore" "1"
(**) fglrx(0): Backing store enabled
(II) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) fglrx(0): GLESX enableFlags = 30
(**) fglrx(0): Option "XaaNoOffscreenPixmaps" "1"
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): GLESX is enabled
(WW) fglrx(0): Option "MergedFB" is not used
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Finished Initialize PPLIB!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) fglrx(0): Enable the clock gating!

```


EDIT:
Setting the boot parameter vram:512 didn't help either

EDIT:
further info:
[http://www.rage3d.com/board/showthread.php?t=33821469](http://www.rage3d.com/board/showthread.php?t=33821469)
up-to-date-one:
[http://phoronix.com/forums/showthread.php?t=6648](http://phoronix.com/forums/showthread.php?t=6648)

---

### Post by markbuntu on 2008-08-10
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR4

 The card is telling fglrx it 0nly has 262mb ram

If you want to increase the system ram the card uses, you need to increase the GART size.  I think you can do that with aticonfig but I am not sure. There is some threads around that talk about that. You should do a search for them.

---

### Post by Yellow Pasque on 2008-08-11
I was on freenode IRC, #radeonhd and one of the devs said this wasn't a problem. The driver adresses half the RAM, but the card uses all of the RAM internally.

---

### Post by soxs on 2008-08-11
> **Temüjin said:**
> I was on freenode IRC, #radeonhd and one of the devs said this wasn't a problem. The driver adresses half the RAM, but the card uses all of the RAM internally.

I heard this sometime ago, but it simply is too mystical to just belive,though I get serious lag wehn playing etqw with ulta effects, using an 3870 Radeon HD (factory OCed) with fglrx 8.7 or 8.6 (whereas both only show 311Mhz ?? wheres it should be bigger at least 5 times than that, obtaining the values from catalys control center). This only happens when V-RAM is limited as ETQW is texture heavy in any respect... so, I am little frustrated. I tried so much things but NOTHINg, really NOTHING helped my out of missery.
As it seems I will have to stick with what you said.
But one question is still open...
Why is the RadeonHD 3000 series the only serie getting this problem???

---

