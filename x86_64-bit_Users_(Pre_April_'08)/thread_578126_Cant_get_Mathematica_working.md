---
title: "Cant get Mathematica working"
date: 2007-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ptscott4 on 2007-10-16
Hi, I'm a linux newbie and am having trouble installing Mathematica 6.0.1 on my AMD64 Ubuntu  7.04 desktop.

I start the installation with a "sudo sh ./MathInstaller" and everything seems to go fine. After, when I enter "mathematica", it just gives me a "mathematica: command not found" 
and if i try to run /usr/local/Wolfram/Mathematica/6.0/Executables/mathematica directly, Ubuntu crashes and I find myself back at the login screen.

The installation worked using the same CD on my Kubuntu 7.04 standard laptop.

Any ideas?

---

### Post by jpkotta on 2007-10-17
The first problem is easy.  Mathematica puts its start script in /usr/local/bin/ which is the proper place (/usr/local/ is for software that is not in the distribution).  However, I don't think Ubuntu puts this in the PATH, so add the following to your ~/.bashrc:
```
export PATH=$PATH:/usr/local/bin
```

The second problem, not so much.  We will need more details.  It sounds like X is crashing, not the whole system.  Are you using a compositing manager?  I had trouble with 5.1 by just enabling the Composite extension in X, though Mathematica didn't crash, nor did X.  Log in, make it crash, and post the file /var/log/Xorg.log.0.

---

### Post by ptscott4 on 2007-10-17
thanks for the reply
oddly, the scripts aren't actually in /usr/local/bin even though the installer said thats where it was putting them.

but here's the file

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux paul-desktop 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64
Build Date: 04 April 2007
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 17 01:28:28 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "BenQ FP93GX"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/X11R6/lib/X11/fonts/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/X11R6/lib/X11/fonts/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.1
    X.Org XInput driver : 0.7
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 105b,0ca4 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 105b,0ca4 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 105b,0ca4 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 105b,0ca4 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 105b,0ca4 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 105b,0cac rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 105b,0ca4 rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 105b,0ca4 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 105b,0ca4 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 105b,0ca4 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 05:00:0: chip 1002,71c2 card 1002,2342 rev 00 class 03,00,00 hdr 80
(II) PCI: 05:00:1: chip 1002,71e2 card 1002,2343 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [1] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [2] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [3] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfde00000 - 0xfdefffff (0x100000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xfdf00000 - 0xfdffffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x00009000 - 0x000090ff (0x100) IX[b]
    [1] -1    0    0x00009400 - 0x000094ff (0x100) IX[b]
    [2] -1    0    0x00009800 - 0x000098ff (0x100) IX[b]
    [3] -1    0    0x00009c00 - 0x00009cff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xfdd00000 - 0xfddfffff (0x100000) MX[b]
(II) Bus 2 prefetchable memory range:
    [0] -1    0    0xfdc00000 - 0xfdcfffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
    [0] -1    0    0x00008000 - 0x000080ff (0x100) IX[b]
    [1] -1    0    0x00008400 - 0x000084ff (0x100) IX[b]
    [2] -1    0    0x00008800 - 0x000088ff (0x100) IX[b]
    [3] -1    0    0x00008c00 - 0x00008cff (0x100) IX[b]
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xfdb00000 - 0xfdbfffff (0x100000) MX[b]
(II) Bus 3 prefetchable memory range:
    [0] -1    0    0xfda00000 - 0xfdafffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
    [0] -1    0    0x00007000 - 0x000070ff (0x100) IX[b]
    [1] -1    0    0x00007400 - 0x000074ff (0x100) IX[b]
    [2] -1    0    0x00007800 - 0x000078ff (0x100) IX[b]
    [3] -1    0    0x00007c00 - 0x00007cff (0x100) IX[b]
(II) Bus 4 non-prefetchable memory range:
    [0] -1    0    0xfd900000 - 0xfd9fffff (0x100000) MX[b]
(II) Bus 4 prefetchable memory range:
    [0] -1    0    0xfd800000 - 0xfd8fffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 5 I/O range:
    [0] -1    0    0x00006000 - 0x000060ff (0x100) IX[b]
    [1] -1    0    0x00006400 - 0x000064ff (0x100) IX[b]
    [2] -1    0    0x00006800 - 0x000068ff (0x100) IX[b]
    [3] -1    0    0x00006c00 - 0x00006cff (0x100) IX[b]
(II) Bus 5 non-prefetchable memory range:
    [0] -1    0    0xfd700000 - 0xfd7fffff (0x100000) MX[b]
(II) Bus 5 prefetchable memory range:
    [0] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[b]
(--) PCI:*(5:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xd0000000/28, 0xfd7f0000/16, I/O @ 0x6c00/8
(--) PCI: (5:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xfd7e0000/16
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
    [0] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[b]
    [1] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[b]
    [2] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
    [3] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
    [4] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[b]
    [5] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
    [6] -1    0    0xfd7f0000 - 0xfd7fffff (0x10000) MX[b](B)
    [7] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [8] -1    0    0x0000b400 - 0x0000b407 (0x8) IX[b]
    [9] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [10] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[b]
    [11] -1    0    0x00000960 - 0x00000967 (0x8) IX[b]
    [12] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[b]
    [13] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[b]
    [14] -1    0    0x0000cc00 - 0x0000cc0f (0x10) IX[b]
    [15] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[b]
    [16] -1    0    0x00000970 - 0x00000977 (0x8) IX[b]
    [17] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[b]
    [18] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[b]
    [19] -1    0    0x0000e000 - 0x0000e00f (0x10) IX[b]
    [20] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [21] -1    0    0x0000f000 - 0x0000f0ff (0x100) IX[b]
    [22] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[b]
    [23] -1    0    0x0000f800 - 0x0000f83f (0x40) IX[b]
    [24] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[b]
    [25] -1    0    0x00006c00 - 0x00006cff (0x100) IX[b](B)
(II) Inactive PCI resource ranges:
    [0] -1    0    0xfd7e0000 - 0xfd7effff (0x10000) MX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[b]
    [1] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[b]
    [2] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
    [3] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
    [4] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[b]
    [5] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
    [6] -1    0    0xfd7f0000 - 0xfd7fffff (0x10000) MX[b](B)
    [7] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [8] -1    0    0x0000b400 - 0x0000b407 (0x8) IX[b]
    [9] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [10] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[b]
    [11] -1    0    0x00000960 - 0x00000967 (0x8) IX[b]
    [12] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[b]
    [13] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[b]
    [14] -1    0    0x0000cc00 - 0x0000cc0f (0x10) IX[b]
    [15] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[b]
    [16] -1    0    0x00000970 - 0x00000977 (0x8) IX[b]
    [17] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[b]
    [18] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[b]
    [19] -1    0    0x0000e000 - 0x0000e00f (0x10) IX[b]
    [20] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [21] -1    0    0x0000f000 - 0x0000f0ff (0x100) IX[b]
    [22] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[b]
    [23] -1    0    0x0000f800 - 0x0000f83f (0x40) IX[b]
    [24] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[b]
    [25] -1    0    0x00006c00 - 0x00006cff (0x100) IX[b](B)
(II) Inactive PCI resource ranges after removing overlaps:
    [0] -1    0    0xfd7e0000 - 0xfd7effff (0x10000) MX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[b]
    [5] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[b]
    [6] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
    [7] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
    [8] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[b]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
    [10] -1    0    0xfd7f0000 - 0xfd7fffff (0x10000) MX[b](B)
    [11] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [12] -1    0    0xfd7e0000 - 0xfd7effff (0x10000) MX[b](B)
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [15] -1    0    0x0000b400 - 0x0000b407 (0x8) IX[b]
    [16] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [17] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[b]
    [18] -1    0    0x00000960 - 0x00000967 (0x8) IX[b]
    [19] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[b]
    [20] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[b]
    [21] -1    0    0x0000cc00 - 0x0000cc0f (0x10) IX[b]
    [22] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[b]
    [23] -1    0    0x00000970 - 0x00000977 (0x8) IX[b]
    [24] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[b]
    [25] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[b]
    [26] -1    0    0x0000e000 - 0x0000e00f (0x10) IX[b]
    [27] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [28] -1    0    0x0000f000 - 0x0000f0ff (0x100) IX[b]
    [29] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[b]
    [30] -1    0    0x0000f800 - 0x0000f83f (0x40) IX[b]
    [31] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[b]
    [32] -1    0    0x00006c00 - 0x00006cff (0x100) IX[b](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.2.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 05:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[b]
    [5] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[b]
    [6] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
    [7] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
    [8] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[b]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
    [10] -1    0    0xfd7f0000 - 0xfd7fffff (0x10000) MX[b](B)
    [11] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [12] -1    0    0xfd7e0000 - 0xfd7effff (0x10000) MX[b](B)
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [15] -1    0    0x0000b400 - 0x0000b407 (0x8) IX[b]
    [16] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [17] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[b]
    [18] -1    0    0x00000960 - 0x00000967 (0x8) IX[b]
    [19] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[b]
    [20] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[b]
    [21] -1    0    0x0000cc00 - 0x0000cc0f (0x10) IX[b]
    [22] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[b]
    [23] -1    0    0x00000970 - 0x00000977 (0x8) IX[b]
    [24] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[b]
    [25] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[b]
    [26] -1    0    0x0000e000 - 0x0000e00f (0x10) IX[b]
    [27] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [28] -1    0    0x0000f000 - 0x0000f0ff (0x100) IX[b]
    [29] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[b]
    [30] -1    0    0x0000f800 - 0x0000f83f (0x40) IX[b]
    [31] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[b]
    [32] -1    0    0x00006c00 - 0x00006cff (0x100) IX[b](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[b]
    [5] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[b]
    [6] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
    [7] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
    [8] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[b]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
    [10] -1    0    0xfd7f0000 - 0xfd7fffff (0x10000) MX[b](B)
    [11] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [12] -1    0    0xfd7e0000 - 0xfd7effff (0x10000) MX[b](B)
    [13] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [14] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [15] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [18] -1    0    0x0000b400 - 0x0000b407 (0x8) IX[b]
    [19] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [20] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[b]
    [21] -1    0    0x00000960 - 0x00000967 (0x8) IX[b]
    [22] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[b]
    [23] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[b]
    [24] -1    0    0x0000cc00 - 0x0000cc0f (0x10) IX[b]
    [25] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[b]
    [26] -1    0    0x00000970 - 0x00000977 (0x8) IX[b]
    [27] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[b]
    [28] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[b]
    [29] -1    0    0x0000e000 - 0x0000e00f (0x10) IX[b]
    [30] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [31] -1    0    0x0000f000 - 0x0000f0ff (0x100) IX[b]
    [32] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[b]
    [33] -1    0    0x0000f800 - 0x0000f83f (0x40) IX[b]
    [34] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[b]
    [35] -1    0    0x00006c00 - 0x00006cff (0x100) IX[b](B)
    [36] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [37] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.12
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: RV530
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: BNQ  Model: 76d5  Serial#: 5471
(II) VESA(0): Year: 2006  Week: 11
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
(II) VESA(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): 1152x870@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) VESA(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) VESA(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) VESA(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) VESA(0): Monitor name: BenQ FP93GX
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff0009d1d5765f150000
(II) VESA(0):     0b10010380261e78eac5c6a3574a9c23
(II) VESA(0):     124f54bdef80714f81908180818c0101
(II) VESA(0):     010101010101302a009851002a403070
(II) VESA(0):     1300782d1100001ed50980a0205e6310
(II) VESA(0):     10605208782d1100001a000000fd0038
(II) VESA(0):     4c1f530e000a202020202020000000fc
(II) VESA(0):     0042656e51204650393347580a2000fd
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) VESA(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) VESA(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) VESA(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  140.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  133.00  1280 1368 1504 1728  1024 1027 1034 1070 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "640x350"   25.17  640 656 752 800  350 387 389 449 -hsync +vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 63
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 63
    LinNumberOfImagePages: 63
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 101 (640x480)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 103 (800x600)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 832
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 31
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 832
    BnkNumberOfImagePages: 31
    LinNumberOfImagePages: 31
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 105 (1024x768)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 18
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 18
    LinNumberOfImagePages: 18
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 107 (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 109 (132x25)
    ModeAttributes: 0xf
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xb000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 264
    XResolution: 132
    YResolution: 25
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 264
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 10a (132x43)
    ModeAttributes: 0xf
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xb000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 264
    XResolution: 132
    YResolution: 43
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 264
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 130 (132x44)
    ModeAttributes: 0xf
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xb000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 264
    XResolution: 132
    YResolution: 44
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 264
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 110 (640x480)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 111 (640x480)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 24
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 24
    LinNumberOfImagePages: 24
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 112 (640x480)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 12
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 12
    LinNumberOfImagePages: 12
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 113 (800x600)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 114 (800x600)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 16
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 16
    LinNumberOfImagePages: 16
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 115 (800x600)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 116 (1024x768)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 9
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 9
    LinNumberOfImagePages: 9
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 117 (1024x768)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 9
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 9
    LinNumberOfImagePages: 9
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 118 (1024x768)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 4
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 4
    LinNumberOfImagePages: 4
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 119 (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 11a (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 11b (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 10d (320x200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 127
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 127
    LinNumberOfImagePages: 127
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 10e (320x200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 127
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 127
    LinNumberOfImagePages: 127
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 10f (320x200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 63
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 63
    LinNumberOfImagePages: 63
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 120 (320x200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 63
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 63
    LinNumberOfImagePages: 63
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 193 (320x240)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 320
    XResolution: 320
    YResolution: 240
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 127
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 320
    BnkNumberOfImagePages: 127
    LinNumberOfImagePages: 127
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 194 (320x240)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 240
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 195 (320x240)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 240
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 84
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 84
    LinNumberOfImagePages: 84
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 196 (320x240)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 320
    YResolution: 240
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1b3 (512x384)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 512
    XResolution: 512
    YResolution: 384
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 63
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 512
    BnkNumberOfImagePages: 63
    LinNumberOfImagePages: 63
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1b4 (512x384)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1024
    XResolution: 512
    YResolution: 384
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 35
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 35
    LinNumberOfImagePages: 35
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1b5 (512x384)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1024
    XResolution: 512
    YResolution: 384
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 35
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 35
    LinNumberOfImagePages: 35
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 1b6 (512x384)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2048
    XResolution: 512
    YResolution: 384
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 18
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 18
    LinNumberOfImagePages: 18
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1c3 (640x350)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 350
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 63
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 63
    LinNumberOfImagePages: 63
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1c4 (640x350)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 350
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 35
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 35
    LinNumberOfImagePages: 35
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1c5 (640x350)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 350
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 35
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 35
    LinNumberOfImagePages: 35
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 1c6 (640x350)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 350
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 17
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 17
    LinNumberOfImagePages: 17
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 183 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 63
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 63
    LinNumberOfImagePages: 63
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 184 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 31
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 31
    LinNumberOfImagePages: 31
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 185 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 31
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 31
    LinNumberOfImagePages: 31
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*(II) VESA(0): Not using built-in mode "640x400" (vrefresh out of range)
Mode: 186 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 15
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 15
    LinNumberOfImagePages: 15
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 133 (720x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 768
    XResolution: 720
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 50
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 768
    BnkNumberOfImagePages: 50
    LinNumberOfImagePages: 50
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 134 (720x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1472
    XResolution: 720
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 27
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1472
    BnkNumberOfImagePages: 27
    LinNumberOfImagePages: 27
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 135 (720x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1472
    XResolution: 720
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 27
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1472
    BnkNumberOfImagePages: 27
    LinNumberOfImagePages: 27
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 136 (720x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2944
    XResolution: 720
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 13
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2944
    BnkNumberOfImagePages: 13
    LinNumberOfImagePages: 13
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 153 (1152x864)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1152
    XResolution: 1152
    YResolution: 864
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 15
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1152
    BnkNumberOfImagePages: 15
    LinNumberOfImagePages: 15
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 154 (1152x864)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2304
    XResolution: 1152
    YResolution: 864
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2304
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 155 (1152x864)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2304
    XResolution: 1152
    YResolution: 864
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2304
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 156 (1152x864)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 4608
    XResolution: 1152
    YResolution: 864
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 3
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 4608
    BnkNumberOfImagePages: 3
    LinNumberOfImagePages: 3
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 163 (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 11
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 11
    LinNumberOfImagePages: 11
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 164 (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 165 (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 166 (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 121 (640x480)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 12
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 12
    LinNumberOfImagePages: 12
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 122 (800x600)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 123 (1024x768)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 4
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 4
    LinNumberOfImagePages: 4
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 124 (1280x1024)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 143 (1400x1050)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1408
    XResolution: 1400
    YResolution: 1050
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 10
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1408
    BnkNumberOfImagePages: 10
    LinNumberOfImagePages: 10
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 144 (1400x1050)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2816
    XResolution: 1400
    YResolution: 1050
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 4
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2816
    BnkNumberOfImagePages: 4
    LinNumberOfImagePages: 4
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 145 (1400x1050)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2816
    XResolution: 1400
    YResolution: 1050
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 4
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2816
    BnkNumberOfImagePages: 4
    LinNumberOfImagePages: 4
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*Mode: 146 (1400x1050)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 5632
    XResolution: 1400
    YResolution: 1050
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 5632
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 173 (1600x1200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 7
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 7
    LinNumberOfImagePages: 7
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 174 (1600x1200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 3
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 3
    LinNumberOfImagePages: 3
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 175 (1600x1200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 3
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 3
    LinNumberOfImagePages: 3
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
Mode: 176 (1600x1200)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 6400
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 6400
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 183 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 63
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 63
    LinNumberOfImagePages: 63
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 184 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 31
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 31
    LinNumberOfImagePages: 31
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 185 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 31
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 31
    LinNumberOfImagePages: 31
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*(II) VESA(0): Not using built-in mode "640x400" (vrefresh out of range)
Mode: 186 (640x400)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 15
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 15
    LinNumberOfImagePages: 15
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1d3 (1856x1392)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1856
    XResolution: 1856
    YResolution: 1392
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 5
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1856
    BnkNumberOfImagePages: 5
    LinNumberOfImagePages: 5
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1d4 (1856x1392)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3712
    XResolution: 1856
    YResolution: 1392
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3712
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1d5 (1856x1392)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3712
    XResolution: 1856
    YResolution: 1392
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3712
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*(II) VESA(0): Not using built-in mode "1856x1392" (hsync out of range)
Mode: 1d6 (1856x1392)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 7424
    XResolution: 1856
    YResolution: 1392
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 7424
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1e3 (1920x1440)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 1920
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 4
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1920
    BnkNumberOfImagePages: 4
    LinNumberOfImagePages: 4
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1e4 (1920x1440)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 5
    RedFieldPosition: 10
    GreenMaskSize: 5
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 5
    LinRedFieldPosition: 10
    LinGreenMaskSize: 5
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
Mode: 1e5 (1920x1440)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 3840
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3840
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000
*(II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
Mode: 1e6 (1920x1440)
    ModeAttributes: 0xbb
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc0004f93
    BytesPerScanline: 7680
    XResolution: 1920
    YResolution: 1440
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 7680
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 400000000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): BenQ FP93GX: Using hsync range of 31.00-83.00 kHz
(II) VESA(0): BenQ FP93GX: Using vrefresh range of 56.00-76.00 Hz
(II) VESA(0): Not using mode "832x624" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual size)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1152x864"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "720x400"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0): Display dimensions: (380, 300) mm
(**) VESA(0): DPI set to (85, 86)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1152x864" (156)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 70Hz refresh for mode "720x400" (136)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (166)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (124)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (122)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (121)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[b]
    [5] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[b]
    [6] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
    [7] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
    [8] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[b]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
    [10] -1    0    0xfd7f0000 - 0xfd7fffff (0x10000) MX[b](B)
    [11] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [12] -1    0    0xfd7e0000 - 0xfd7effff (0x10000) MX[b](B)
    [13] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [14] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [15] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [18] -1    0    0x0000b400 - 0x0000b407 (0x8) IX[b]
    [19] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [20] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[b]
    [21] -1    0    0x00000960 - 0x00000967 (0x8) IX[b]
    [22] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[b]
    [23] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[b]
    [24] -1    0    0x0000cc00 - 0x0000cc0f (0x10) IX[b]
    [25] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[b]
    [26] -1    0    0x00000970 - 0x00000977 (0x8) IX[b]
    [27] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[b]
    [28] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[b]
    [29] -1    0    0x0000e000 - 0x0000e00f (0x10) IX[b]
    [30] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [31] -1    0    0x0000f000 - 0x0000f0ff (0x100) IX[b]
    [32] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[b]
    [33] -1    0    0x0000f800 - 0x0000f83f (0x40) IX[b]
    [34] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[b]
    [35] -1    0    0x00006c00 - 0x00006cff (0x100) IX[b](B)
    [36] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [37] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.12
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: RV530
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xd0000000,0x1000000)
(II) VESA(0): virtual address = 0x2b05b2e82000,
    physical address = 0xd0000000, size = 16777216
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
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
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

---

### Post by jpkotta on 2007-10-20
It looks like X just plain crashed and couldn't send a distress signal to the log.  Like I said, you may want to disable Composite (edit /etc/X11/xorg.conf) just to see if that is the cause.  Other than that, try reinstalling Mathematica or asking Wolfram for ideas.

---

