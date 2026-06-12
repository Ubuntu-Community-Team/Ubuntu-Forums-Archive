---
title: "from 17&quot; monitor to 24&quot; monitor"
date: 2009-05-20
forum: x86 64-bit Users
---

### Post by daniel74 on 2009-05-20
Hello,
 
I have an AMD 64 pcu and installed ubuntu9.4 64 bit using a 17" monitor and all worked fine.
 
Then I connected a 24" widescreen monitor and now it does switch off the monitor after showing the ubuntu logo ob booting.
 
I can still enter in recovery mode and see ubuntu starts. but also after reading lots of posts, i could not get to get it running.
 
then i decided to re-install ubuntu again on the 24" monitor - which surprise that also now the installing process from CD aborts switching off my monitor....
 
Any help much appreciated.
regards,
Daniel

---

### Post by daniel74 on 2009-05-20
Hello again,
 
now I connected the pc to the analog signal of the monitor and it works !
I do not understand why it does not work on the digital signal ?
 
Also still remaining 1 problem: the max resolution of ubuntu display is 1360x768 pixels, why my monitor needs 1920x1200 pixels
 
is there a way to change this ?

---

### Post by Yellow Pasque on 2009-05-20
What video card and driver are you using? You should also post /var/log/Xorg.0.log

---

### Post by daniel74 on 2009-05-21
Hello,

I do not know the video card driver, where can I look this up ?

I have a Xorg.0.log and a Xorg.0.log.old

Here I post the Xorg.0.log taking this, when I have connected to the analog cable.


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux aspire 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 21 08:34:59 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:5:0) ATI Technologies Inc RS690 [Radeon X1200 Series] rev 0, Mem @ 0xd0000000/268435456, 0xfdee0000/65536, 0xfdd00000/1048576, I/O @ 0x0000ce00/256
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 6.12.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
    ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
    ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
    ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
    ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
    ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
    ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI Mobility Radeon 4500 Series, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
    ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
    ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
    ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
    ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
    ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
    ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
    ATI Radeon HD Graphics, ATI Radeon Graphics,
    ATI Mobility Radeon HD Graphics, ATI Mobility Radeon Graphics,
    ATI Radeon Graphics
(II) Primary Device is: PCI 01@00:05:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [24] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [25] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [26] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) RADEON(0): TOTO SAYS 00000000fdee0000
(II) RADEON(0): MMIO registers at 0x00000000fdee0000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791e)
(WW) RADEON(0): R500 support is under development. Please report any issues to [EMAIL="xorg-driver-ati@lists.x.org"]xorg-driver-ati@lists.x.org[/EMAIL]
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
    SubsystemVendorID: 0x105b SubsystemID: 0x0e0b
    IOBaseAddress: 0xce00
    Filename: br26131.bin 
    BIOS Bootup Message:  
ATI Radeon X1250 for Acer/Poodle                                             

(II) RADEON(0): Framebuffer space used by Firmware (kb): 16
(II) RADEON(0): Start of VRAM area used by Firmware: 0xfffc000
(II) RADEON(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffc000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 400000
(II) RADEON(0): Default Memory Clock: 200000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 14320
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
(==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 400.000000, mclk: 200.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=13 min=64800 max=120000; xclk=40000
encoder: 0x15
encoder: 0x19
encoder: 0xf
(II) RADEON(0): Output HDMI-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "HDMI-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: HDMI-0
  Connector: HDMI-A
  DFP2: INTERNAL_DDI
  DDC reg: 0x7e40
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-D
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP3: INTERNAL_LVTM1
  DDC reg: 0x7e40
(II) RADEON(0): I2C device "HDMI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output HDMI-0 disconnected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Using fuzzy aspect match for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 1152x864
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.4.0
    ABI class: X.Org Video Driver, version 5.0
(!!) RADEON(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [24] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [25] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [26] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 262144 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x0074e000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00752000
(II) RADEON(0): Will use 7480 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 7480 kb for back buffer at offset 0x00756000
(II) RADEON(0): Will use 7480 kb for depth buffer at offset 0x00ea4000
(II) RADEON(0): Will use 119808 kb for textures at offset 0x015f2000
(II) RADEON(0): Will use 119864 kb for X Server offscreen at offset 0x08af2000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 32768 kB allocated with handle 0x102ae200
(II) RADEON(0): [pci] ring handle = 0x2efff000
(II) RADEON(0): [pci] Ring mapped at 0x7f68aafc7000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0x1f000000
(II) RADEON(0): [pci] Ring read ptr mapped at 0x7f68ab0e9000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0x2f000000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0x7f68963e2000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0x2f001000
(II) RADEON(0): [pci] GART Texture map mapped at 0x7f6894762000
(II) RADEON(0): [drm] register handle = 0xfdee0000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7000 0x7fff7000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 18
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x7fff7000 is: 0x7fff7000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0x81ff8000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7000 0x7fff7000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x81ff8000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 1
(II) EXA(0): Offscreen pixmap area of 122740736 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video
Output DFP2 disable success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1152x864 - 1520 895 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7000 0x7fff7000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x81ff8000
freq: 81620000
best_freq: 81624000
best_feedback_div: 228
best_ref_div: 5
best_post_div: 8
(II) RADEON(0): crtc(0) Clock: mode 81620, PLL 81620
(II) RADEON(0): crtc(0) PLL  : refdiv 5, fbdiv 0xE4(228), pdiv 8
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output DFP2 disable success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Lock CRTC 0 success
Unlock CRTC 0 success
(WW) RADEON(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 304 x 228
(II) config/hal: Adding input device NOVATEK USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) NOVATEK USB Keyboard: always reports core events
(**) NOVATEK USB Keyboard: Device: "/dev/input/event4"
(II) NOVATEK USB Keyboard: Found keys
(II) NOVATEK USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) NOVATEK USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) NOVATEK USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "pt"
(**) NOVATEK USB Keyboard: xkb_layout: "pt"
(II) config/hal: Adding input device NOVATEK USB Keyboard
(**) NOVATEK USB Keyboard: always reports core events
(**) NOVATEK USB Keyboard: Device: "/dev/input/event5"
(II) NOVATEK USB Keyboard: Found 16 mouse buttons
(II) NOVATEK USB Keyboard: Found keys
(II) NOVATEK USB Keyboard: Configuring as keyboard
(**) NOVATEK USB Keyboard: YAxisMapping: buttons 4 and 5
(**) NOVATEK USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) NOVATEK USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) NOVATEK USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "pt"
(**) NOVATEK USB Keyboard: xkb_layout: "pt"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB Optical Mouse: Found 8 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
Output DFP2 disable success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1360x768 - 1776 798 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7000 0x7fff7000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x81ff8000
freq: 84750000
best_freq: 84751020
best_feedback_div: 580
best_ref_div: 7
best_post_div: 14
(II) RADEON(0): crtc(0) Clock: mode 84750, PLL 84750
(II) RADEON(0): crtc(0) PLL  : refdiv 7, fbdiv 0x244(580), pdiv 14
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output DFP2 disable success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Total number of valid Screen mode(s) added: 0

---

### Post by tigermath on 2009-05-21
Hi,
    I've installed Ubuntu 9.04 just today. My monitor is not detected and display rsolution stick to 800*600. It showed no other option.
What should I do?

---

### Post by Yellow Pasque on 2009-05-21
@tigermath: a lot of people are having this problem with the new Xserver
[https://bugs.launchpad.net/ubuntu/+bug/378532/comments/2](https://bugs.launchpad.net/ubuntu/+bug/378532/comments/2)

@daniel74: Are you using the HDMI connector?

---

### Post by PGHammer on 2009-05-21
> **Temüjin said:**
> @tigermath: a lot of people are having this problem with the new Xserver
[https://bugs.launchpad.net/ubuntu/+bug/378532/comments/2](https://bugs.launchpad.net/ubuntu/+bug/378532/comments/2)

@daniel74: Are you using the HDMI connector?

After using an old non-PnP 19" analog CRT for the past year, I had to replace it with a 23" LCD (Acer H233H.bmid, TN panel).  Whereas Jaunty had issues getting the resolution right (only openSuSE could have the right resolution and refresh rate, but I had to semi-cheat in SaX to do it) with the CRT, the Acer (connected via the DVI input) has the same resolution in Jaunty that it does in Windows (down to the refresh rate).

So not just my Windows are widescreen, even my *beans* are widescreen....

---

### Post by daniel74 on 2009-05-22
Hello, no I am not using the HDMI connector.
Any idea what I can do ? I am totally desperate and think I must switch to Windows OS again... what a pitty I thought UBUNTU was cleverer, but it fails already on a simple install task....

---

### Post by nikem on 2009-05-31
I have exactly same problem. When I connect my old 17" crt it works.But 22" syncmaster doesn't work. It is weird.
Thank you.

---

