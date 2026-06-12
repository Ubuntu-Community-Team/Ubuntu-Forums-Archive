---
title: "ATI X64 I wish this worked"
date: 2005-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Robuis on 2005-04-26
Has any one out there had any success using the newest ati x64 drivers with this hardware configuration? 
MoBo Asus K8V SE 
Card Radeon 9550 256 megs ram. 

I have had some success using fedora core 3 i386 with the ati 32 bit drivers. However I have had no success using the 64 bit drivers with fedora, mandrake, and ubuntu. Out of all the distros that I have tried I like ubuntu the best, but should I just give up on seeing fgl_gears? It kida sux to have to settle for no 3D support. I can live with it. But why is this so hard to accomplish? 

Does any one have this hardware? Do you have the driver working? Should I look into another Gfx card?

---

### Post by GrumpySmurf on 2005-04-26
[QUOTE=Robuis]Has any one out there had any success using the newest ati x64 drivers with this hardware configuration? 
MoBo Asus K8V SE 
Card Radeon 9550 256 megs ram. 

I have had some success using fedora core 3 i386 with the ati 32 bit drivers. However I have had no success using the 64 bit drivers with fedora, mandrake, and ubuntu. Out of all the distros that I have tried I like ubuntu the best, but should I just give up on seeing fgl_gears? It kida sux to have to settle for no 3D support. I can live with it. But why is this so hard to accomplish? 

Does any one have this hardware? Do you have the driver working? Should I look into another Gfx card?[/QUOTE]
 Sanity check!

Have you read the procedures in the wiki?

HOWTO Install Binary Drivers.  Includes ATI.
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto/](http://www.ubuntulinux.org/wiki/BinaryDriverHowto/)

List of supported video card chipsets.
[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)

As long as ATI has a 64 bit driver available for kernel 2.6.x, it should work under any distribution with kernel 2.6.x.

---

### Post by Robuis on 2005-04-26
I tried this:
[http://www.ubuntuforums.org/showthread.php?t=22496](http://www.ubuntuforums.org/showthread.php?t=22496)
I changed the i386.rpm to x64.
still no success.

---

### Post by Robuis on 2005-04-26
Ok I tried the Wiki and this is what I get when I run fgl_gears
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32


Any thoughts?

---

### Post by Robuis on 2005-04-26
Ok after the Wiki still having issues, I installed the K8 kernel. this is the out put of my Xorg.0.log Looks like i'm getting closer. Come on fgl_gears!

This is the out put of the log <Less some info> 


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154247 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 x86_64 [ELF] 
Current Operating System: Linux Robuis 2.6.10-5-amd64-k8 #1 Tue Apr 5 12:10:43 UTC 2005 x86_64
Build Date: 05 April 2005
OS Kernel: Linux version 2.6.10-5-amd64-k8 (buildd@king) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:10:43 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 26 19:37:27 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]

(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x4153) rev 0, Mem @ 0xe0000000/28, 0xfce00000/16, I/O @ 0x9000/8, BIOS @ 0xfcd00000/17
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x4173) rev 0, Mem @ 0xd0000000/28, 0xfcc00000/16

(
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI Radeon/FireGL: The following chipsets are supported:
(II) Primary Device is: PCI 01:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9550 (RV350 4153) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfdf00000 - 0xfdf000ff (0x100) MX[B]
	[6] -1	0	0xfde00000 - 0xfde000ff (0x100) MX[B]
	[7] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[8] -1	0	0xfd900000 - 0xfd91ffff (0x20000) MX[B]
	[9] -1	0	0xfda00000 - 0xfda00fff (0x1000) MX[B]
	[10] -1	0	0xfd800000 - 0xfd8007ff (0x800) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfcc00000 - 0xfcc0ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfcd00000 - 0xfcd1ffff (0x20000) MX[B](B)
	[15] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[35] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[37] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x718ee0
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfdf00000 - 0xfdf000ff (0x100) MX[B]
	[6] -1	0	0xfde00000 - 0xfde000ff (0x100) MX[B]
	[7] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[8] -1	0	0xfd900000 - 0xfd91ffff (0x20000) MX[B]
	[9] -1	0	0xfda00000 - 0xfda00fff (0x1000) MX[B]
	[10] -1	0	0xfd800000 - 0xfd8007ff (0x800) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfcc00000 - 0xfcc0ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfcd00000 - 0xfcd1ffff (0x20000) MX[B](B)
	[15] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[35] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[38] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[40] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): Qbs disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9550 (RV350 4153)" (Chipset = 0x4153)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x2084)
(--) fglrx(0): board vendor info: original ATI grafics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfce00000
(--) fglrx(0): ROM-BIOS at 0xfcd00000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x0C
(--) fglrx(0): VideoRAM: 131072 kByte (64-bit SDR SDRAM)
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 2 with Monitor Type 0
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 3 with Monitor Type 1
(II) fglrx(0): Primary head:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) fglrx(0): Secondary head:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) fglrx(0): EDID data from the display on Secondary head ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 4db9  Serial#: 1346842937
(II) fglrx(0): Year: 1999  Week: 41
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) fglrx(0): Gamma: 2.28
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): GTF timings supported
(II) fglrx(0): redX: 0.638 redY: 0.325   greenX: 0.276 greenY: 0.596
(II) fglrx(0): blueX: 0.143 blueY: 0.066   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 720x400@88Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@87Hz (interlaced)
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): #5: hsize: 1024  vsize 768  refresh: 100  vid: 26721
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 157.5 MHz   Image Size:  352 x 264 mm
(II) fglrx(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 96 kHz, PixClock max 210 MHz
(II) fglrx(0): Monitor name: S/M 900SL
(II) fglrx(0): Serial No: H3NKA05149
(II) fglrx(0): 
(II) fglrx(0): DesktopSetup 0x0000
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Overlay disabled
(==) fglrx(0): Overlay disabled
(II) fglrx(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total 4 valid mode(s) found.
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Default mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) fglrx(0):  Default mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) fglrx(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) fglrx(0): *Default mode "800x600": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
(II) fglrx(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) fglrx(0): *Default mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(--) fglrx(0): Display dimensions: (360, 270) mm
(--) fglrx(0): DPI set to (72, 72)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x000007d2
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdf00000 - 0xfdf000ff (0x100) MX[B]
	[8] -1	0	0xfde00000 - 0xfde000ff (0x100) MX[B]
	[9] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[10] -1	0	0xfd900000 - 0xfd91ffff (0x20000) MX[B]
	[11] -1	0	0xfda00000 - 0xfda00fff (0x1000) MX[B]
	[12] -1	0	0xfd800000 - 0xfd8007ff (0x800) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfcc00000 - 0xfcc0ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfcd00000 - 0xfcd1ffff (0x20000) MX[B](B)
	[17] -1	0	0xfce00000 - 0xfce0ffff (0x10000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[29] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[30] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[32] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[36] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[38] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[39] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[40] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[41] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[43] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM area:     0xe0501000 (size=0x07aff000)
(II) fglrx(0): driver needs XFree86 version: 4.3.x
(WW) fglrx(0): could not detect XFree86 version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 768)
(II) fglrx(0): Largest offscreen area available: 1024 x 7419
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!


Any help would be great!

---

### Post by Robuis on 2005-04-27
I got it! 

For any one who needs help this is "the" place to look!
[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

I used option 2 comand line option, and did have to manualy edit my xorg.conf file. Props to magi Thanks.

Post if you would like to see my xorg.conf.
Im so pumped.

---

