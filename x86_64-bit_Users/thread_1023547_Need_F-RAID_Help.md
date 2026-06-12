---
title: "Need F-RAID Help"
date: 2008-12-28
forum: x86 64-bit Users
---

### Post by cashmoney on 2008-12-28
OK So for 5 days I have been re-installing Ubuntu 8.10 many different ways trying to get FRAID to work with my Asus Crosshair MOBO and 2 250 Gb HDD's. (64-bit Architecture.  If I load the 32 bit cd I keep getting I/O errors and the live cd won't laod)  I have tested both HDD's and they keep passing the Drive tests.  Anywho here is my Demesg.  Also this is with stripped Raid (raid0) using dm raid.
Any help is appreciated.

```
[   10.752264] sda: rw=0, want=671099310, limit=488397168
[   10.752269] attempt to access beyond end of device
[   10.752271] sda: rw=0, want=671099308, limit=488397168
[   10.752273] attempt to access beyond end of device
[   10.752274] sda: rw=0, want=671099309, limit=488397168
[   10.752276] attempt to access beyond end of device
[   10.752278] sda: rw=0, want=671099310, limit=488397168
[   10.752282] attempt to access beyond end of device
[   10.752284] sda: rw=0, want=671099308, limit=488397168
[   10.752286] attempt to access beyond end of device
[   10.752287] sda: rw=0, want=671099309, limit=488397168
[   10.752289] attempt to access beyond end of device
[   10.752291] sda: rw=0, want=671099310, limit=488397168
[   10.752295] attempt to access beyond end of device
[   10.752296] sda: rw=0, want=671099308, limit=488397168
[   10.752298] attempt to access beyond end of device
[   10.752300] sda: rw=0, want=671099309, limit=488397168
[   10.752301] attempt to access beyond end of device
[   10.752303] sda: rw=0, want=671099310, limit=488397168
[   10.752307] attempt to access beyond end of device
[   10.752309] sda: rw=0, want=671099308, limit=488397168
[   10.752311] attempt to access beyond end of device
[   10.752312] sda: rw=0, want=671099309, limit=488397168
[   10.752314] attempt to access beyond end of device
[   10.752315] sda: rw=0, want=671099310, limit=488397168
[   10.752320] attempt to access beyond end of device
[   10.752321] sda: rw=0, want=671099308, limit=488397168
[   10.752323] attempt to access beyond end of device
[   10.752324] sda: rw=0, want=671099309, limit=488397168
[   10.752326] attempt to access beyond end of device
[   10.752328] sda: rw=0, want=671099310, limit=488397168
[   10.752334] attempt to access beyond end of device
[   10.752336] sda: rw=0, want=671099244, limit=488397168
[   10.752338] attempt to access beyond end of device
[   10.752339] sda: rw=0, want=671099245, limit=488397168
[   10.752341] attempt to access beyond end of device
[   10.752343] sda: rw=0, want=671099246, limit=488397168
[   10.752345] attempt to access beyond end of device
[   10.752346] sda: rw=0, want=671099247, limit=488397168
[   10.752348] attempt to access beyond end of device
[   10.752349] sda: rw=0, want=671099248, limit=488397168
[   10.752351] attempt to access beyond end of device
[   10.752353] sda: rw=0, want=671099249, limit=488397168
[   10.752355] attempt to access beyond end of device
[   10.752356] sda: rw=0, want=671099250, limit=488397168
[   10.752358] attempt to access beyond end of device
[   10.752359] sda: rw=0, want=671099251, limit=488397168
[   10.752365] attempt to access beyond end of device
[   10.752367] sda: rw=0, want=671099300, limit=488397168
[   10.752369] attempt to access beyond end of device
[   10.752370] sda: rw=0, want=671099301, limit=488397168
[   10.752372] attempt to access beyond end of device
[   10.752374] sda: rw=0, want=671099302, limit=488397168
[   10.752376] attempt to access beyond end of device
[   10.752377] sda: rw=0, want=671099303, limit=488397168
[   10.752379] attempt to access beyond end of device
[   10.752380] sda: rw=0, want=671099304, limit=488397168
[   10.752382] attempt to access beyond end of device
[   10.752384] sda: rw=0, want=671099305, limit=488397168
[   10.752386] attempt to access beyond end of device
[   10.752387] sda: rw=0, want=671099306, limit=488397168
[   10.752389] attempt to access beyond end of device
[   10.752391] sda: rw=0, want=671099307, limit=488397168
[   10.752395] attempt to access beyond end of device
[   10.752397] sda: rw=0, want=671099308, limit=488397168
[   10.752399] attempt to access beyond end of device
[   10.752400] sda: rw=0, want=671099309, limit=488397168
[   10.752402] attempt to access beyond end of device
[   10.752404] sda: rw=0, want=671099310, limit=488397168
[   10.752408] attempt to access beyond end of device
[   10.752409] sda: rw=0, want=671099308, limit=488397168
[   10.752411] attempt to access beyond end of device
[   10.752413] sda: rw=0, want=671099309, limit=488397168
[   10.752415] attempt to access beyond end of device
[   10.752416] sda: rw=0, want=671099310, limit=488397168
[   10.940414] PM: Starting manual resume from disk
[   10.940416] PM: Resume from partition 254:4
[   10.940418] PM: Checking hibernation image.
[   10.940581] PM: Resume from disk failed.
[   10.984657] kjournald starting.  Commit interval 5 seconds
[   10.984677] EXT3-fs: mounted filesystem with ordered data mode.
[   15.245050] udevd version 124 started
[   15.491914] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   15.516043] ACPI: Power Button (FF) [PWRF]
[   15.516144] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   15.548033] ACPI: Power Button (CM) [PWRB]
[   15.622231] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.630172] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.720111] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   15.887355] Found: SST 49LF080A
[   15.887364] ck804xrom @fff00000: Found 1 x8 devices at 0x0 in 8-bit bank
[   16.006803] number of JEDEC chips: 1
[   16.006806] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[   16.230857] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   16.230861] ACPI: I/O resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM01 [0x1c40-0x1c45]
[   16.230863] ACPI: Device needs an ACPI driver
[   16.230894] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   16.657308] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   16.657312] HDA Intel 0000:00:0e.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[   16.657327] HDA Intel 0000:00:0e.1: setting latency timer to 64
[   16.692805] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[   16.819131] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   16.947319] attempt to access beyond end of device
[   16.947324] sda: rw=0, want=671099314, limit=488397168
[   16.947327] __ratelimit: 80 callbacks suppressed
[   16.947329] Buffer I/O error on device sda3, logical block 0
[   16.947332] attempt to access beyond end of device
[   16.947334] sda: rw=0, want=671099318, limit=488397168
[   16.947335] Buffer I/O error on device sda3, logical block 1
[   16.947339] attempt to access beyond end of device
[   16.947340] sda: rw=0, want=671099322, limit=488397168
[   16.947342] Buffer I/O error on device sda3, logical block 2
[   16.947344] attempt to access beyond end of device
[   16.947346] sda: rw=0, want=671099326, limit=488397168
[   16.947347] Buffer I/O error on device sda3, logical block 3
[   16.947350] attempt to access beyond end of device
[   16.947352] sda: rw=0, want=671099330, limit=488397168
[   16.947353] Buffer I/O error on device sda3, logical block 4
[   16.947355] attempt to access beyond end of device
[   16.947357] sda: rw=0, want=671099334, limit=488397168
[   16.947358] Buffer I/O error on device sda3, logical block 5
[   16.947361] attempt to access beyond end of device
[   16.947363] sda: rw=0, want=671099338, limit=488397168
[   16.947364] Buffer I/O error on device sda3, logical block 6
[   16.947366] attempt to access beyond end of device
[   16.947368] sda: rw=0, want=671099342, limit=488397168
[   16.947369] Buffer I/O error on device sda3, logical block 7
[   16.947372] attempt to access beyond end of device
[   16.947373] sda: rw=0, want=671099314, limit=488397168
[   16.947375] Buffer I/O error on device sda3, logical block 0
[   16.947377] attempt to access beyond end of device
[   16.947378] sda: rw=0, want=671099318, limit=488397168
[   16.947380] Buffer I/O error on device sda3, logical block 1
[   16.950948] attempt to access beyond end of device
[   16.950953] sda: rw=0, want=687871178, limit=488397168
[   16.950958] attempt to access beyond end of device
[   16.950959] sda: rw=0, want=687871186, limit=488397168
[   16.950963] attempt to access beyond end of device
[   16.950964] sda: rw=0, want=687871194, limit=488397168
[   16.950967] attempt to access beyond end of device
[   16.950969] sda: rw=0, want=687871202, limit=488397168
[   16.950971] attempt to access beyond end of device
[   16.950973] sda: rw=0, want=687871178, limit=488397168
[   16.967361] attempt to access beyond end of device
[   16.967366] sda: rw=0, want=671099124, limit=488397168
[   16.967368] attempt to access beyond end of device
[   16.967370] sda: rw=0, want=671099125, limit=488397168
[   16.967372] attempt to access beyond end of device
[   16.967374] sda: rw=0, want=671099126, limit=488397168
[   16.967376] attempt to access beyond end of device
[   16.967377] sda: rw=0, want=671099127, limit=488397168
[   16.967379] attempt to access beyond end of device
[   16.967381] sda: rw=0, want=671099128, limit=488397168
[   16.967383] attempt to access beyond end of device
[   16.967384] sda: rw=0, want=671099129, limit=488397168
[   16.967386] attempt to access beyond end of device
[   16.967388] sda: rw=0, want=671099130, limit=488397168
[   16.967390] attempt to access beyond end of device
[   16.967391] sda: rw=0, want=671099131, limit=488397168
[   16.967394] attempt to access beyond end of device
[   16.967395] sda: rw=0, want=671099124, limit=488397168
[   16.967397] attempt to access beyond end of device
[   16.967399] sda: rw=0, want=671099125, limit=488397168
[   16.967401] attempt to access beyond end of device
[   16.967402] sda: rw=0, want=671099126, limit=488397168
[   16.967404] attempt to access beyond end of device
[   16.967406] sda: rw=0, want=671099127, limit=488397168
[   16.967408] attempt to access beyond end of device
[   16.967409] sda: rw=0, want=671099128, limit=488397168
[   16.967411] attempt to access beyond end of device
[   16.967413] sda: rw=0, want=671099129, limit=488397168
[   16.967415] attempt to access beyond end of device
[   16.967416] sda: rw=0, want=671099130, limit=488397168
[   16.967419] attempt to access beyond end of device
[   16.967420] sda: rw=0, want=671099131, limit=488397168
[   16.967442] attempt to access beyond end of device
[   16.967444] sda: rw=0, want=671099292, limit=488397168
[   16.967446] attempt to access beyond end of device
[   16.967448] sda: rw=0, want=671099293, limit=488397168
[   16.967450] attempt to access beyond end of device
[   16.967451] sda: rw=0, want=671099294, limit=488397168
[   16.967453] attempt to access beyond end of device
[   16.967455] sda: rw=0, want=671099295, limit=488397168
[   16.967457] attempt to access beyond end of device
[   16.967458] sda: rw=0, want=671099296, limit=488397168
[   16.967460] attempt to access beyond end of device
[   16.967462] sda: rw=0, want=671099297, limit=488397168
[   16.967464] attempt to access beyond end of device
[   16.967465] sda: rw=0, want=671099298, limit=488397168
[   16.967467] attempt to access beyond end of device
[   16.967468] sda: rw=0, want=671099299, limit=488397168
[   16.967471] attempt to access beyond end of device
[   16.967472] sda: rw=0, want=671099292, limit=488397168
[   16.967474] attempt to access beyond end of device
[   16.967476] sda: rw=0, want=671099293, limit=488397168
[   16.967478] attempt to access beyond end of device
[   16.967479] sda: rw=0, want=671099294, limit=488397168
[   16.967482] attempt to access beyond end of device
[   16.967483] sda: rw=0, want=671099295, limit=488397168
[   16.967485] attempt to access beyond end of device
[   16.967486] sda: rw=0, want=671099296, limit=488397168
[   16.967489] attempt to access beyond end of device
[   16.967490] sda: rw=0, want=671099297, limit=488397168
[   16.967492] attempt to access beyond end of device
[   16.967493] sda: rw=0, want=671099298, limit=488397168
[   16.967500] attempt to access beyond end of device
[   16.967502] sda: rw=0, want=671099299, limit=488397168
[   16.967683] attempt to access beyond end of device
[   16.967685] sda: rw=0, want=671099308, limit=488397168
[   16.967687] attempt to access beyond end of device
[   16.967722] sda: rw=0, want=671099309, limit=488397168
[   16.967768] attempt to access beyond end of device
[   16.967770] sda: rw=0, want=671099310, limit=488397168
[   16.967773] attempt to access beyond end of device
[   16.967774] sda: rw=0, want=671099308, limit=488397168
[   16.967776] attempt to access beyond end of device
[   16.967778] sda: rw=0, want=671099309, limit=488397168
[   16.967780] attempt to access beyond end of device
[   16.967781] sda: rw=0, want=671099310, limit=488397168
[   16.967789] attempt to access beyond end of device
[   16.967791] sda: rw=0, want=671099308, limit=488397168
[   16.967793] attempt to access beyond end of device
[   16.967794] sda: rw=0, want=671099309, limit=488397168
[   16.967796] attempt to access beyond end of device
[   16.967798] sda: rw=0, want=671099310, limit=488397168
[   16.967803] attempt to access beyond end of device
[   16.967804] sda: rw=0, want=671099308, limit=488397168
[   16.967806] attempt to access beyond end of device
[   16.967808] sda: rw=0, want=671099309, limit=488397168
[   16.967810] attempt to access beyond end of device
[   16.967811] sda: rw=0, want=671099310, limit=488397168
[   16.967815] attempt to access beyond end of device
[   16.967817] sda: rw=0, want=671099308, limit=488397168
[   16.967819] attempt to access beyond end of device
[   16.967820] sda: rw=0, want=671099309, limit=488397168
[   16.967822] attempt to access beyond end of device
[   16.967824] sda: rw=0, want=671099310, limit=488397168
[   16.967829] attempt to access beyond end of device
[   16.967830] sda: rw=0, want=671099308, limit=488397168
[   16.967832] attempt to access beyond end of device
[   16.967834] sda: rw=0, want=671099309, limit=488397168
[   16.967836] attempt to access beyond end of device
[   16.967837] sda: rw=0, want=671099310, limit=488397168
[   16.967842] attempt to access beyond end of device
[   16.967843] sda: rw=0, want=671099308, limit=488397168
[   16.967845] attempt to access beyond end of device
[   16.967847] sda: rw=0, want=671099309, limit=488397168
[   16.967849] attempt to access beyond end of device
[   16.967850] sda: rw=0, want=671099310, limit=488397168
[   16.967857] attempt to access beyond end of device
[   16.967859] sda: rw=0, want=671099244, limit=488397168
[   16.967861] attempt to access beyond end of device
[   16.967862] sda: rw=0, want=671099245, limit=488397168
[   16.967865] attempt to access beyond end of device
[   16.967866] sda: rw=0, want=671099246, limit=488397168
[   16.967868] attempt to access beyond end of device
[   16.967869] sda: rw=0, want=671099247, limit=488397168
[   16.967872] attempt to access beyond end of device
[   16.967873] sda: rw=0, want=671099248, limit=488397168
[   16.967875] attempt to access beyond end of device
[   16.967876] sda: rw=0, want=671099249, limit=488397168
[   16.967879] attempt to access beyond end of device
[   16.967880] sda: rw=0, want=671099250, limit=488397168
[   16.967882] attempt to access beyond end of device
[   16.967883] sda: rw=0, want=671099251, limit=488397168
[   16.967890] attempt to access beyond end of device
[   16.967892] sda: rw=0, want=671099300, limit=488397168
[   16.967894] attempt to access beyond end of device
[   16.967895] sda: rw=0, want=671099301, limit=488397168
[   16.967897] attempt to access beyond end of device
[   16.967899] sda: rw=0, want=671099302, limit=488397168
[   16.967901] attempt to access beyond end of device
[   16.967902] sda: rw=0, want=671099303, limit=488397168
[   16.967904] attempt to access beyond end of device
[   16.967906] sda: rw=0, want=671099304, limit=488397168
[   16.967908] attempt to access beyond end of device
[   16.967909] sda: rw=0, want=671099305, limit=488397168
[   16.967911] attempt to access beyond end of device
[   16.967913] sda: rw=0, want=671099306, limit=488397168
[   16.967915] attempt to access beyond end of device
[   16.967916] sda: rw=0, want=671099307, limit=488397168
[   16.967971] attempt to access beyond end of device
[   16.967973] sda: rw=0, want=671099308, limit=488397168
[   16.967975] attempt to access beyond end of device
[   16.967976] sda: rw=0, want=671099309, limit=488397168
[   16.967978] attempt to access beyond end of device
[   16.967980] sda: rw=0, want=671099310, limit=488397168
[   16.967984] attempt to access beyond end of device
[   16.967986] sda: rw=0, want=671099308, limit=488397168
[   16.967988] attempt to access beyond end of device
[   16.967989] sda: rw=0, want=671099309, limit=488397168
[   16.967991] attempt to access beyond end of device
[   16.967993] sda: rw=0, want=671099310, limit=488397168
[   18.256380] lp: driver loaded but no devices found
[   18.391974] Adding 8385920k swap on /dev/mapper/nvidia_cjcebfei3.  Priority:-1 extents:1 across:8385920k
[   18.927807] EXT3 FS on dm-1, internal journal
[   19.664145] kjournald starting.  Commit interval 5 seconds
[   19.664637] EXT3 FS on dm-2, internal journal
[   19.664643] EXT3-fs: mounted filesystem with ordered data mode.
[   20.093730] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.596128] ACPI: WMI: Mapper loaded
[   20.777539] powernow-k8: Found 1 AMD Athlon(tm) 64 FX-62 Dual Core Processor processors (2 cpu cores) (version 2.20.00)
[   20.777563] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   20.777583] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   21.446584] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.570854] ppdev: user-space parallel port driver
[   22.856049] attempt to access beyond end of device
[   22.856055] sda: rw=0, want=671099124, limit=488397168
[   22.856057] __ratelimit: 89 callbacks suppressed
[   22.856059] Buffer I/O error on device sda2, logical block 629153408
[   22.856064] attempt to access beyond end of device
[   22.856065] sda: rw=0, want=671099125, limit=488397168
[   22.856067] Buffer I/O error on device sda2, logical block 629153409
[   22.856069] attempt to access beyond end of device
[   22.856070] sda: rw=0, want=671099126, limit=488397168
[   22.856072] Buffer I/O error on device sda2, logical block 629153410
[   22.856074] attempt to access beyond end of device
[   22.856075] sda: rw=0, want=671099127, limit=488397168
[   22.856077] Buffer I/O error on device sda2, logical block 629153411
[   22.856079] attempt to access beyond end of device
[   22.856080] sda: rw=0, want=671099128, limit=488397168
[   22.856082] Buffer I/O error on device sda2, logical block 629153412
[   22.856084] attempt to access beyond end of device
[   22.856086] sda: rw=0, want=671099129, limit=488397168
[   22.856087] Buffer I/O error on device sda2, logical block 629153413
[   22.856089] attempt to access beyond end of device
[   22.856091] sda: rw=0, want=671099130, limit=488397168
[   22.856092] Buffer I/O error on device sda2, logical block 629153414
[   22.856094] attempt to access beyond end of device
[   22.856096] sda: rw=0, want=671099131, limit=488397168
[   22.856098] Buffer I/O error on device sda2, logical block 629153415
[   22.856101] attempt to access beyond end of device
[   22.856102] sda: rw=0, want=671099124, limit=488397168
[   22.856104] Buffer I/O error on device sda2, logical block 629153408
[   22.856106] attempt to access beyond end of device
[   22.856107] sda: rw=0, want=671099125, limit=488397168
[   22.856109] Buffer I/O error on device sda2, logical block 629153409
[   22.856111] attempt to access beyond end of device
[   22.856112] sda: rw=0, want=671099126, limit=488397168
[   22.856114] attempt to access beyond end of device
[   22.856116] sda: rw=0, want=671099127, limit=488397168
[   22.856118] attempt to access beyond end of device
[   22.856120] sda: rw=0, want=671099128, limit=488397168
[   22.856122] attempt to access beyond end of device
[   22.856123] sda: rw=0, want=671099129, limit=488397168
[   22.856126] attempt to access beyond end of device
[   22.856127] sda: rw=0, want=671099130, limit=488397168
[   22.856129] attempt to access beyond end of device
[   22.856131] sda: rw=0, want=671099131, limit=488397168
[   22.856145] attempt to access beyond end of device
[   22.856147] sda: rw=0, want=671099292, limit=488397168
[   22.856149] attempt to access beyond end of device
[   22.856151] sda: rw=0, want=671099293, limit=488397168
[   22.856153] attempt to access beyond end of device
[   22.856154] sda: rw=0, want=671099294, limit=488397168
[   22.856156] attempt to access beyond end of device
[   22.856158] sda: rw=0, want=671099295, limit=488397168
[   22.856160] attempt to access beyond end of device
[   22.856161] sda: rw=0, want=671099296, limit=488397168
[   22.856163] attempt to access beyond end of device
[   22.856165] sda: rw=0, want=671099297, limit=488397168
[   22.856167] attempt to access beyond end of device
[   22.856169] sda: rw=0, want=671099298, limit=488397168
[   22.856171] attempt to access beyond end of device
[   22.856172] sda: rw=0, want=671099299, limit=488397168
[   22.856175] attempt to access beyond end of device
[   22.856177] sda: rw=0, want=671099292, limit=488397168
[   22.856179] attempt to access beyond end of device
[   22.856180] sda: rw=0, want=671099293, limit=488397168
[   22.856182] attempt to access beyond end of device
[   22.856184] sda: rw=0, want=671099294, limit=488397168
[   22.856186] attempt to access beyond end of device
[   22.856188] sda: rw=0, want=671099295, limit=488397168
[   22.856190] attempt to access beyond end of device
[   22.856191] sda: rw=0, want=671099296, limit=488397168
[   22.856193] attempt to access beyond end of device
[   22.856195] sda: rw=0, want=671099297, limit=488397168
[   22.856197] attempt to access beyond end of device
[   22.856198] sda: rw=0, want=671099298, limit=488397168
[   22.856200] attempt to access beyond end of device
[   22.856202] sda: rw=0, want=671099299, limit=488397168
[   22.856253] attempt to access beyond end of device
[   22.856255] sda: rw=0, want=671099308, limit=488397168
[   22.856257] attempt to access beyond end of device
[   22.856258] sda: rw=0, want=671099309, limit=488397168
[   22.856260] attempt to access beyond end of device
[   22.856262] sda: rw=0, want=671099310, limit=488397168
[   22.856265] attempt to access beyond end of device
[   22.856266] sda: rw=0, want=671099308, limit=488397168
[   22.856268] attempt to access beyond end of device
[   22.856270] sda: rw=0, want=671099309, limit=488397168
[   22.856272] attempt to access beyond end of device
[   22.856274] sda: rw=0, want=671099310, limit=488397168
[   22.856281] attempt to access beyond end of device
[   22.856282] sda: rw=0, want=671099308, limit=488397168
[   22.856285] attempt to access beyond end of device
[   22.856287] sda: rw=0, want=671099309, limit=488397168
[   22.856289] attempt to access beyond end of device
[   22.856290] sda: rw=0, want=671099310, limit=488397168
[   22.856295] attempt to access beyond end of device
[   22.856296] sda: rw=0, want=671099308, limit=488397168
[   22.856298] attempt to access beyond end of device
[   22.856300] sda: rw=0, want=671099309, limit=488397168
[   22.856302] attempt to access beyond end of device
[   22.856304] sda: rw=0, want=671099310, limit=488397168
[   22.856308] attempt to access beyond end of device
[   22.856310] sda: rw=0, want=671099308, limit=488397168
[   22.856312] attempt to access beyond end of device
[   22.856314] sda: rw=0, want=671099309, limit=488397168
[   22.856316] attempt to access beyond end of device
[   22.856317] sda: rw=0, want=671099310, limit=488397168
[   22.856322] attempt to access beyond end of device
[   22.856324] sda: rw=0, want=671099308, limit=488397168
[   22.856326] attempt to access beyond end of device
[   22.856328] sda: rw=0, want=671099309, limit=488397168
[   22.856330] attempt to access beyond end of device
[   22.856331] sda: rw=0, want=671099310, limit=488397168
[   22.856336] attempt to access beyond end of device
[   22.856338] sda: rw=0, want=671099308, limit=488397168
[   22.856340] attempt to access beyond end of device
[   22.856341] sda: rw=0, want=671099309, limit=488397168
[   22.856343] attempt to access beyond end of device
[   22.856345] sda: rw=0, want=671099310, limit=488397168
[   22.856353] attempt to access beyond end of device
[   22.856355] sda: rw=0, want=671099244, limit=488397168
[   22.856357] attempt to access beyond end of device
[   22.856358] sda: rw=0, want=671099245, limit=488397168
[   22.856360] attempt to access beyond end of device
[   22.856362] sda: rw=0, want=671099246, limit=488397168
[   22.856364] attempt to access beyond end of device
[   22.856365] sda: rw=0, want=671099247, limit=488397168
[   22.856367] attempt to access beyond end of device
[   22.856369] sda: rw=0, want=671099248, limit=488397168
[   22.856371] attempt to access beyond end of device
[   22.856373] sda: rw=0, want=671099249, limit=488397168
[   22.856375] attempt to access beyond end of device
[   22.856376] sda: rw=0, want=671099250, limit=488397168
[   22.856378] attempt to access beyond end of device
[   22.856380] sda: rw=0, want=671099251, limit=488397168
[   22.856386] attempt to access beyond end of device
[   22.856388] sda: rw=0, want=671099300, limit=488397168
[   22.856390] attempt to access beyond end of device
[   22.856392] sda: rw=0, want=671099301, limit=488397168
[   22.856394] attempt to access beyond end of device
[   22.856395] sda: rw=0, want=671099302, limit=488397168
[   22.856397] attempt to access beyond end of device
[   22.856399] sda: rw=0, want=671099303, limit=488397168
[   22.856401] attempt to access beyond end of device
[   22.856403] sda: rw=0, want=671099304, limit=488397168
[   22.856405] attempt to access beyond end of device
[   22.856406] sda: rw=0, want=671099305, limit=488397168
[   22.856408] attempt to access beyond end of device
[   22.856410] sda: rw=0, want=671099306, limit=488397168
[   22.856412] attempt to access beyond end of device
[   22.856413] sda: rw=0, want=671099307, limit=488397168
[   22.856418] attempt to access beyond end of device
[   22.856420] sda: rw=0, want=671099308, limit=488397168
[   22.856422] attempt to access beyond end of device
[   22.856423] sda: rw=0, want=671099309, limit=488397168
[   22.856425] attempt to access beyond end of device
[   22.856427] sda: rw=0, want=671099310, limit=488397168
[   22.856432] attempt to access beyond end of device
[   22.856433] sda: rw=0, want=671099308, limit=488397168
[   22.856435] attempt to access beyond end of device
[   22.856437] sda: rw=0, want=671099309, limit=488397168
[   22.856439] attempt to access beyond end of device
[   22.856440] sda: rw=0, want=671099310, limit=488397168
[   22.871488] attempt to access beyond end of device
[   22.871492] sda: rw=0, want=671099314, limit=488397168
[   22.871496] attempt to access beyond end of device
[   22.871498] sda: rw=0, want=671099318, limit=488397168
[   22.871501] attempt to access beyond end of device
[   22.871503] sda: rw=0, want=671099322, limit=488397168
[   22.871505] attempt to access beyond end of device
[   22.871506] sda: rw=0, want=671099326, limit=488397168
[   22.871509] attempt to access beyond end of device
[   22.871511] sda: rw=0, want=671099330, limit=488397168
[   22.871513] attempt to access beyond end of device
[   22.871515] sda: rw=0, want=671099334, limit=488397168
[   22.871518] attempt to access beyond end of device
[   22.871519] sda: rw=0, want=671099338, limit=488397168
[   22.871522] attempt to access beyond end of device
[   22.871523] sda: rw=0, want=671099342, limit=488397168
[   22.871526] attempt to access beyond end of device
[   22.871527] sda: rw=0, want=671099314, limit=488397168
[   22.871529] attempt to access beyond end of device
[   22.871531] sda: rw=0, want=671099318, limit=488397168
[   22.875213] attempt to access beyond end of device
[   22.875218] sda: rw=0, want=687871178, limit=488397168
[   22.875222] attempt to access beyond end of device
[   22.875224] sda: rw=0, want=687871186, limit=488397168
[   22.875227] attempt to access beyond end of device
[   22.875228] sda: rw=0, want=687871194, limit=488397168
[   22.875231] attempt to access beyond end of device
[   22.875233] sda: rw=0, want=687871202, limit=488397168
[   22.875236] attempt to access beyond end of device
[   22.875237] sda: rw=0, want=687871178, limit=488397168
[   27.064841] eth1: no link during initialization.
[   27.284905] NET: Registered protocol family 17

```

---

### Post by cariboo on 2008-12-28
I assume you mean fakeraid. Have you followed the howto [here]("http://help.ubuntu.com/community/FakeRaidHowto")? I used this to set up raid on my server, I think it may have taken 20 minutes to set it up.

Jim

---

### Post by cashmoney on 2008-12-28
> **cariboo907 said:**
> I assume you mean fakeraid. Have you followed the howto [here]("http://help.ubuntu.com/community/FakeRaidHowto")? I used this to set up raid on my server, I think it may have taken 20 minutes to set it up.

Jim

Followed it to a 'T'  Also did the text based installer because the Text based is supported and still got the same message.  I installed gentoo and I don't get those dmesg errors and everything works all peachy so I don't know.  It is a weird one.

---

### Post by cariboo on 2008-12-28
Actually I had something similar happen with the same sort of error messages. My array was in a race condition, so basically I had a lot of errors on both disks, it took about 6 hours for fsck to finish repairing it, I lost about 30Gbs of data, that fortunately was backed up.

In my case it turned out that one of my ram sticks was bad, I pulled out the offending ram module, that repaired the problem.

Jim

---

