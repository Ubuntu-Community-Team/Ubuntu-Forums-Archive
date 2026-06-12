---
title: "Installing Restricted ATI Driver Bombs My System :("
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by general.chaos on 2009-11-05
I've reinstalled 3x now. 

Each time I enable the driver via the GUI and reboot I am greeted with a black screen and nothing more.  It gets past GUB obviously, and then I see the black screen with the white Ubuntu logo, but the next screen never loads.  I have the system up and running again, but I'd really like to use some of the eye-candy that worked in 9.04.

My video card is: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
I'm running a clean install of 9.10 x64

Anyone else having an issue with this?  Advice?

---

### Post by lavinog on 2009-11-05
can you boot into recovery mode?
can you post your /etc/X11/xorg.conf

---

### Post by Bigtime_Scrub on 2009-11-06
I had the same problem. I installed the proprietary driver manually. Don't use what Ubuntu wants to use. I did and I couldn't log into X, I reinstalled, did it manually and it worked fine.

---

### Post by nikgare on 2009-11-06
Have a look in the xorg logs in /var/logs.
Is there anything their that looks bad?

---

### Post by general.chaos on 2009-11-06
> **lavinog said:**
> can you boot into recovery mode?
can you post your /etc/X11/xorg.conf

If I had an xorg.conf I'd post it.

--------------------------
chaos@ChaOS-GT:/etc$ cd X11
chaos@ChaOS-GT:/etc/X11$ ls
app-defaults             fonts    xinit       Xsession          XvMCConfig
cursors                  rgb.txt  xkb         Xsession.d        Xwrapper.config
default-display-manager  X        Xresources  Xsession.options


Thats all thats in there, and I didn't erase it.  This is a fresh install with some extra packages added.

Any advice?

---

### Post by masux594 on 2009-11-06
Hmm.. have u tried with a reconfigure af the xserver package?```
sudo dpkg-reconfigure xserver-xorg
```Sysc, A

---

### Post by general.chaos on 2009-11-06
> **masux594 said:**
> Hmm.. have u tried with a reconfigure af the xserver package?```
sudo dpkg-reconfigure xserver-xorg
```Sysc, A

Ran that command, still no xorg.conf

---

### Post by general.chaos on 2009-11-06
> **Bigtime_Scrub said:**
> I had the same problem. I installed the proprietary driver manually. Don't use what Ubuntu wants to use. I did and I couldn't log into X, I reinstalled, did it manually and it worked fine.

I tried the manual install, and the results were the same :(

I did notice it saying something about the x86 drivers being required to use the x64 ones.  Should I run the 32 bit ATI installer first, and then the x64 one?  Many thanks!

---

### Post by lavinog on 2009-11-06
you need a xorg.conf to use fglrx
aticonfig will create it for you:
```
sudo aticonfig --initial
```

---

### Post by general.chaos on 2009-11-06
> **lavinog said:**
> you need a xorg.conf to use fglrx
aticonfig will create it for you:
```
sudo aticonfig --initial
```

I ran aticonfig --initial -f per in the recovery console (per ati's instructions), but it didn't help :(

Still have the same issue.

---

### Post by general.chaos on 2009-11-06
ok, reinstalled again :/

Installed restricted driver again, but before I rebooted I ran the initial command listed above.  Here is the output:

Found fglrx primary device section
 Unable to find any supported Screen section

Help please!

xorg.conf says:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

---

### Post by lavinog on 2009-11-06
> **general.chaos said:**
> ok, reinstalled again :/

Installed restricted driver again, but before I rebooted I ran the initial command listed above.  Here is the output:

Found fglrx primary device section
 Unable to find any supported Screen section

Help please!

xorg.conf says:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
remove /etc/X11/xorg.conf
then use the aticonfig --initial command

---

### Post by general.chaos on 2009-11-06
output:
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

I rebooted and it came up, but I can't enable any effects yet :(
Also, when I look at the GUI for restricted hardware, it says that a different version of the driver is in use.

Apparently the driver Ubuntu hosts is different than the one on ATI's site for the same card.  

At least it boots now, but I'd really like to get this fixed


edit------------------------------

got it to run (there are 2 -'s), 

Output was: 
Could not find configuration file, so create an empty one
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0


Rebooting now, will post back results.

Edit 2---------------
no dice, black screen on reboot.

I've found that I can get it to boot the GUI again by deleting the xorg.conf from the recovery console.

Is there a different tool for re-creating that file?

---

### Post by lavinog on 2009-11-06
> **general.chaos said:**
> 
Apparently the driver Ubuntu hosts is different than the one on ATI's site for the same card.  


Yes, the version in the repos is a prerelease version.  Usually once you use the driver directly from the ati site, you should continue to use their driver.

can you post /var/log/Xorg.0.log

also post the output of 
```

dmesg|grep 'fglrx 8'

```
This is what I have for the ubuntu fglrx driver:
```

[    7.117737] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors

```

---

### Post by general.chaos on 2009-11-06
[    9.253442] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux chaos-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=b93c9c2e-a91d-4aec-bc75-fb252a34768d ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  6 16:52:58 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
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

(--) PCI:*(0:3:0:0) 1002:9589:1545:3330 ATI Technologies Inc RV630 [Radeon HD 2600 Series] rev 0, Mem @ 0xe0000000/268435456, 0xfdce0000/65536, I/O @ 0x0000bc00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
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
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
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
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
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
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
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
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
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
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(II) Primary Device is: PCI 03@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000fdce0000
(II) RADEON(0): MMIO registers at 0x00000000fdce0000: size 64KB
(II) RADEON(0): PCI bus 3 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon HD 2600 Pro" (ChipID = 0x9589)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1545 SubsystemID: 0x3330
	IOBaseAddress: 0xbc00
	Filename: S63G2E3D1.bi
	BIOS Bootup Message: 

26P512PCIE                

                                                  
(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 601000
(II) RADEON(0): Default Memory Clock: 405000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 601.000000, mclk: 405.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
(II) RADEON(0): Output DVI-1 has no monitor section
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: DVI-1
  Connector: DVI-I
  CRT2: INTERNAL_KLDSCP_DAC2
  DFP1: INTERNAL_KLDSCP_TMDS1
  DDC reg: 0x7e50
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP2: INTERNAL_LVTM1
  DDC reg: 0x7e40
(II) RADEON(0): I2C device "DVI-1:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
finished output detect: 1
finished all detect
before xf86InitialConfiguration
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): Panel infos found from DDC detailed: 1440x900
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output DVI-1 disconnected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 1440x900
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit e0000000 0 0
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): Dynamic Power Management Disabled
mc fb loc is 00ff00e0
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x20000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1536,8191)
(II) RADEON(0): Reserved area from (0,1440) to (1536,1442)
(II) RADEON(0): Largest offscreen area available: 1536 x 6749
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00873000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00879000
(II) RADEON(0): Largest offscreen area available: 1536 x 6741
(II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1440x900 - 1904 934 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 106500000
best_freq: 106500000
best_feedback_div: 71
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 9
(II) RADEON(0): crtc(0) Clock: mode 106500, PLL 106500
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x47(71), fracfbdiv 0, pdiv 9
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
(II) RADEON(0): Coherent Mode enabled
Output digital setup success
Output DFP2 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1440x900 - 1904 934 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 106500000
best_freq: 106500000
best_feedback_div: 71
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 9
(II) RADEON(0): crtc(0) Clock: mode 106500, PLL 106500
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x47(71), fracfbdiv 0, pdiv 9
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
(II) RADEON(0): Coherent Mode enabled
Output digital setup success
Output DFP2 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
(--) RandR disabled
(II) Setting vga for screen 0.
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
(EE) GLX error: Can not get required symbols.
(II) RADEON(0): Setting screen physical size to 410 x 257
(II) config/hal: Adding input device Microsoft Microsoft® Keyboard with Fingerprint Reader
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Microsoft Microsoft® Keyboard with Fingerprint Reader: always reports core events
(**) Microsoft Microsoft® Keyboard with Fingerprint Reader: Device: "/dev/input/event4"
(II) Microsoft Microsoft® Keyboard with Fingerprint Reader: Found keys
(II) Microsoft Microsoft® Keyboard with Fingerprint Reader: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Microsoft® Keyboard with Fingerprint Reader" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Dell Dell USB Optical Mouse
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event3"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(**) Dell Dell USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Dell USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Dell USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Dell USB Optical Mouse: (accel) set acceleration profile 0
(II) Dell Dell USB Optical Mouse: initialized for relative axes.
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 226  Serial#: 1212231993
(II) RADEON(0): Year: 2006  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.35
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.589
(II) RADEON(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVEL954145
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d260239314148
(II) RADEON(0): 	2710010380291a872ad7a5a2594a9624
(II) RADEON(0): 	145054bfef809500950f81808140714f
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	36009a011100001c000000fd00384b1e
(II) RADEON(0): 	510e000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	004856454c3935343134350a20200097
(II) RADEON(0): EDID vendor "SAM", prod id 550
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output DFP2 enable success
```

---

### Post by lavinog on 2009-11-06
you have fglrx installed, but xorg is loading the open source driver, which currently doesn't have 3d support for your card yet.
```

(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) **No screen section available. Using defaults.**
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"

```

There is something wrong with your xorg.conf file.

This is my /etc/X11/xorg.conf:
```


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```
This is the warning I get in Xorg.0.log:
```

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  6 09:05:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) **|-->Screen "Default Screen" (0)**
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	[b]Using the first device section listed.
(**) |   |-->Device "Default Device"[/b]
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.

```
Your log doesn't show that it is reading the default device section which is needed to specify fglrx.

Throughout my Xorg.0.log i have lines that start with:
```

(II) fglrx(0):
```
You have lines that start with:
```

(II) RADEON(0):

```

EDIT:
after deleting my xorg.conf and running aticonfig --initial my xorg became:
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```
This adds a layout for xorg to follow. (do not copy mine because the BUSID might be different on your machine)

Since you are getting a black screen.
see if you have a /etc/modprobe.d/blacklist-fglrx.conf
it should have:
```

# Warning: This file is autogenerated by fglrx-kernel-source. All changes to this file will be lost.
blacklist radeon

```
This file tells the kernel not to load the radeon driver.  The problem you are experiencing with the black screen is probably because both drivers are being loaded.

---

### Post by general.chaos on 2009-11-07
Apparently the same problem exists in 9.10 x86.

This tells me 9.10 was rushed, as this card and PC ALWAYS worked before 9.10

I've decided to just fall back to 9.04, because it actually works.
Thanks for all your help, I'm quite dissapointed with 9.10 due to this.


When I load FGLRX and not the Radeon drivers, I get the black screen.  What I posted is what allows me to see the GUI. When it its set up correctly (done automatically by aticonfig, it crashes.  This happens with both the Ubuntu provided, and the Ati provided version.  I certainly won't be recommending anyone I know go to 9.10 after all this.

---

### Post by lavinog on 2009-11-07
> **general.chaos said:**
> 
When I load FGLRX and not the Radeon drivers, I get the black screen. 
What I am saying is that I think you are loading both, and that is why you get the black screen.

---

### Post by punkybouy on 2009-11-07
Have you tried using ENVY to install the driver?

---

### Post by punkybouy on 2009-11-07
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English)


From AMD's website:
"32-Bit packages must be installed for 64-Bit Linux drivers to install or work."

---

### Post by lavinog on 2009-11-07
> **punkybouy said:**
> [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English)


From AMD's website:
"32-Bit packages must be installed for 64-Bit Linux drivers to install or work."

That should be irrelavent because the installer is supposed to handle it.
The envy installer should also not be needed since the ati installer supports ubuntu now.

---

### Post by Yellow Pasque on 2009-11-09
Try the latest open-source stack. It has decent 3D, enough to run Compiz and a lot of 3D apps, though no OpenGL 2.x yet

1. Purge fglrx: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
2. Get a recent kernel (headers and image packages, in this case, amd64 versions): [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc6/)
3. Boot into your new kernal and add the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

If you get it working, glxinfo should show:
```
OpenGL renderer string: **Mesa DRI R600** ...
```

---

### Post by patjcompton on 2009-11-10
I had a lot of the same issues as you with 9.04 using an ATI Radeon Mobility HD3650.

A couple weeks ago I got it to clear up mostly, but I could still not have my cake and eat it too when it came to both enabling the eye candy AND watching movies.

I upgraded to Karmic and it's been smooth sailing from the get-go.

I can totally understand a need to get Jaunty working well with your card...

But if you want to end the butt-pain, my sole advice would be to upgrade to 9.10.  I don't think you'll regret it.

---

### Post by freetolio on 2009-11-12
I used Temüjin's method above, and it is the only thing that worked for me after hopelessly fussing with the restricted fglrx and instaling ATI's driver directly.    I have a Radeon HD 2900 Pro on 9.10 x64.  I was previously getting black screens and/or a failed GDM start dropping down to a text login when I tried to install drivers.

I had to get the generic headers "all" in addition to the 64 bit ones to make the dependencies work, and I had to build something that required the sources though this might be abnormal due to some xorg package issues I was having.

Video (non-flash) is smooth as butter now at 1920x1080, and desktop effects work great.

---

