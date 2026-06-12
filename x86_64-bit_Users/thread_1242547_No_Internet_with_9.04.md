---
title: "No Internet with 9.04"
date: 2009-08-17
forum: x86 64-bit Users
---

### Post by noob707 on 2009-08-17
I am Dual booting vista 32-bit and Ubuntu 64-bit. I can not access the inetrnet wirelessly or wired on my laptop in Ubuntu. I forgot what i command i ran but it said that wireless was UNCLAIMED and wired was DISABLED. My wireless card works fine under Windows. Anyone way i can enable WIRED and get a driver for my WIRELESS CARD.

Thanks.

BTW, Ubuntu is sweet.

---

### Post by Nburnes on 2009-08-17
Could you tell us your machine model and specs?

---

### Post by noob707 on 2009-08-17
Asus F50 SF

Intel Core 2 Duo 2.53 GHz 1066FSB

4GBs DDR2 800 MHz RAM

Nvidia GT 1GB RAM Graphics

And i don't know the mobo.

Wireless Card is an Atheros AR9285.

Should i install MADWIFI?

---

### Post by sanderj on 2009-08-17
I would start by live-booting the Ubuntu CD with the ethernet wire connected.

If Internet does not work, get the output of:

[LIST]
[*]ifconfig
[*]dmesg
[*]sudo lspci
[/LIST]

Just checking: you're not behind a firewall or proxy or something like that?

---

### Post by noob707 on 2009-08-17
i will live-boot and run those commands as you requested.

i am not behind a proxy or a firewall(New to Ubuntu).

---

### Post by noob707 on 2009-08-17
So i did what you said it didn't work. Still no internet. I am gonan copy and paste everything from the terminal. Here it is.



































































































































































ed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2533.409 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 52428800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3979512k/5242880k available (4760k kernel code, 1049316k absent, 213072k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5066.81 BogoMIPS (lpj=10133636)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.008364] ACPI: Checking initramfs for custom DSDT
[    0.448056] Setting APIC routing to flat
[    0.448372] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.490022] CPU0: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.492001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5066.84 BogoMIPS (lpj=10133686)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.576830] CPU1: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.576857] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.580052] Brought up 2 CPUs
[    0.580055] Total of 2 processors activated (10133.66 BogoMIPS).
[    0.580092] CPU0 attaching sched-domain:
[    0.580095]  domain 0: span 0-1 level MC
[    0.580097]   groups: 0 1
[    0.580103] CPU1 attaching sched-domain:
[    0.580105]  domain 0: span 0-1 level MC
[    0.580107]   groups: 1 0
[    0.580187] net_namespace: 1400 bytes
[    0.580187] Booting paravirtualized kernel on bare hardware
[    0.580340] Time:  7:43:29  Date: 08/18/09
[    0.580340] regulator: core version 0.5
[    0.580340] NET: Registered protocol family 16
[    0.580340] ACPI: bus type pci registered
[    0.580340] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.580340] PCI: Not using MMCONFIG.
[    0.580340] PCI: Using configuration type 1 for base access
[    0.581125] ACPI: EC: EC description table is found, configuring boot EC
[    0.597992] ACPI: Interpreter enabled
[    0.597996] ACPI: (supports S0 S3 S4 S5)
[    0.598023] ACPI: Using IOAPIC for interrupt routing
[    0.598152] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.601932] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.614055] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.621143] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.621145] ACPI: EC: driver started in poll mode
[    0.621323] ACPI: No dock devices found.
[    0.621422] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.621534] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.621538] pci 0000:00:01.0: PME# disabled
[    0.621649] pci 0000:00:02.5: reg 20 io port: [0xfff0-0xffff]
[    0.621669] pci 0000:00:02.5: PME# supported from D3cold
[    0.621673] pci 0000:00:02.5: PME# disabled
[    0.621698] pci 0000:00:03.0: reg 10 32bit mmio: [0xf9fff000-0xf9ffffff]
[    0.621747] pci 0000:00:03.1: reg 10 32bit mmio: [0xf9ffe000-0xf9ffefff]
[    0.621809] pci 0000:00:03.3: reg 10 32bit mmio: [0xf9ffd000-0xf9ffdfff]
[    0.621846] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.621850] pci 0000:00:03.3: PME# disabled
[    0.621886] pci 0000:00:04.0: reg 10 32bit mmio: [0xf9ffcc00-0xf9ffcc7f]
[    0.621893] pci 0000:00:04.0: reg 14 io port: [0xcc00-0xcc7f]
[    0.621925] pci 0000:00:04.0: supports D1 D2
[    0.621927] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.621931] pci 0000:00:04.0: PME# disabled
[    0.621963] pci 0000:00:05.0: reg 10 io port: [0xc800-0xc807]
[    0.621970] pci 0000:00:05.0: reg 14 io port: [0xc400-0xc403]
[    0.621976] pci 0000:00:05.0: reg 18 io port: [0xc000-0xc007]
[    0.621983] pci 0000:00:05.0: reg 1c io port: [0xbc00-0xbc03]
[    0.621989] pci 0000:00:05.0: reg 20 io port: [0xb800-0xb80f]
[    0.621996] pci 0000:00:05.0: reg 24 io port: [0xb400-0xb47f]
[    0.622011] pci 0000:00:05.0: PME# supported from D3cold
[    0.622015] pci 0000:00:05.0: PME# disabled
[    0.622071] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.622075] pci 0000:00:06.0: PME# disabled
[    0.622138] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.622142] pci 0000:00:07.0: PME# disabled
[    0.622190] pci 0000:00:0f.0: reg 10 32bit mmio: [0xf9ff4000-0xf9ff7fff]
[    0.622228] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.622232] pci 0000:00:0f.0: PME# disabled
[    0.622305] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.622319] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.622334] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.622342] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.622350] pci 0000:01:00.0: reg 30 32bit mmio: [0xfde80000-0xfdefffff]
[    0.622416] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.622420] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfdefffff]
[    0.622427] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.622493] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdff0000-0xfdffffff]
[    0.622547] pci 0000:02:00.0: supports D1
[    0.622549] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.622554] pci 0000:02:00.0: PME# disabled
[    0.622625] pci 0000:00:06.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.622684] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.622689] pci 0000:00:07.0: bridge 32bit mmio: [0xfe000000-0xfebfffff]
[    0.622696] pci 0000:00:07.0: bridge 64bit mmio pref: [0xf6000000-0xf8ffffff]
[    0.622713] bus 00 -> node 0
[    0.622723] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.623105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.632709] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.632914] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.633118] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 10 11 12 14 15)
[    0.633319] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.633923] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.634125] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.634326] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.634527] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.634799] ACPI: WMI: Mapper loaded
[    0.634847] SCSI subsystem initialized
[    0.634847] libata version 3.00 loaded.
[    0.634847] usbcore: registered new interface driver usbfs
[    0.634847] usbcore: registered new interface driver hub
[    0.634847] usbcore: registered new device driver usb
[    0.634847] PCI: Using ACPI for IRQ routing
[    0.648011] Bluetooth: Core ver 2.13
[    0.648025] NET: Registered protocol family 31
[    0.648025] Bluetooth: HCI device and connection manager initialized
[    0.648025] Bluetooth: HCI socket layer initialized
[    0.648025] NET: Registered protocol family 8
[    0.648025] NET: Registered protocol family 20
[    0.648035] NetLabel: Initializing
[    0.648037] NetLabel:  domain hash size = 128
[    0.648038] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.648054] NetLabel:  unlabeled traffic allowed by default
[    0.648082] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.648087] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.652070] AppArmor: AppArmor Filesystem Enabled
[    0.656009] Switched to high resolution mode on CPU 0
[    0.656899] Switched to high resolution mode on CPU 1
[    0.664012] pnp: PnP ACPI init
[    0.664021] ACPI: bus type pnp registered
[    0.666830] pnp: PnP ACPI: found 12 devices
[    0.666832] ACPI: ACPI bus type pnp unregistered
[    0.666845] system 00:06: ioport range 0x290-0x297 has been reserved
[    0.666848] system 00:06: ioport range 0xc00-0xc05 has been reserved
[    0.666850] system 00:06: ioport range 0xd00-0xd05 has been reserved
[    0.666853] system 00:06: ioport range 0x480-0x48f has been reserved
[    0.666855] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.666858] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.666860] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.666863] system 00:06: ioport range 0xc00-0xc7f could not be reserved
[    0.666866] system 00:06: ioport range 0x2000-0x20fe has been reserved
[    0.666869] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
[    0.666871] system 00:06: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.666874] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
[    0.666877] system 00:06: iomem range 0xfed10000-0xfed3ffff has been reserved
[    0.666883] system 00:09: ioport range 0x250-0x253 has been reserved
[    0.666886] system 00:09: ioport range 0x256-0x25f has been reserved
[    0.666888] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.666891] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.666897] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.666903] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.666906] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.666908] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.666911] system 00:0b: iomem range 0x100000-0xbfffffff could not be reserved
[    0.666914] system 00:0b: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.671608] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.671611] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.671617] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfdefffff
[    0.671621] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.671628] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.671630] pci 0000:00:06.0:   IO window: disabled
[    0.671635] pci 0000:00:06.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.671639] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.671646] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.671649] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.671654] pci 0000:00:07.0:   MEM window: 0xfe000000-0xfebfffff
[    0.671658] pci 0000:00:07.0:   PREFETCH window: 0x000000f6000000-0x000000f8ffffff
[    0.671674] pci 0000:00:01.0: setting latency timer to 64
[    0.671683] pci 0000:00:06.0: setting latency timer to 64
[    0.671692] pci 0000:00:07.0: setting latency timer to 64
[    0.671696] bus: 00 index 0 io port: [0x00-0xffff]
[    0.671698] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.671700] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.671702] bus: 01 index 1 mmio: [0xfa000000-0xfdefffff]
[    0.671704] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.671706] bus: 01 index 3 mmio: [0x0-0x0]
[    0.671708] bus: 02 index 0 mmio: [0x0-0x0]
[    0.671710] bus: 02 index 1 mmio: [0xfdf00000-0xfdffffff]
[    0.671712] bus: 02 index 2 mmio: [0x0-0x0]
[    0.671713] bus: 02 index 3 mmio: [0x0-0x0]
[    0.671715] bus: 03 index 0 io port: [0xe000-0xefff]
[    0.671717] bus: 03 index 1 mmio: [0xfe000000-0xfebfffff]
[    0.671719] bus: 03 index 2 mmio: [0xf6000000-0xf8ffffff]
[    0.671721] bus: 03 index 3 mmio: [0x0-0x0]
[    0.671729] NET: Registered protocol family 2
[    0.704061] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.704683] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.709375] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.710866] TCP: Hash tables configured (established 262144 bind 65536)
[    0.710870] TCP reno registered
[    0.720177] NET: Registered protocol family 1
[    0.720358] checking if image is initramfs... it is
[    1.590550] Freeing initrd memory: 7976k freed
[    1.597942] Simple Boot Flag at 0x71 set to 0x1
[    1.598455] audit: initializing netlink socket (disabled)
[    1.598500] type=2000 audit(1250581409.596:1): initialized
[    1.609010] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.610528] VFS: Disk quotas dquot_6.5.1
[    1.610600] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.611238] fuse init (API version 7.10)
[    1.611327] msgmni has been set to 7789
[    1.611546] alg: No test for stdrng (krng)
[    1.611557] io scheduler noop registered
[    1.611559] io scheduler anticipatory registered
[    1.611562] io scheduler deadline registered
[    1.611610] io scheduler cfq registered (default)
[    1.672053] pci 0000:01:00.0: Boot video device
[    1.674549] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.674587] pcieport-driver 0000:00:01.0: found MSI capability
[    1.674621] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.674633] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.674704] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.674755] pcieport-driver 0000:00:06.0: found MSI capability
[    1.674783] pcieport-driver 0000:00:06.0: irq 2302 for MSI/MSI-X
[    1.674796] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.674869] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.674920] pcieport-driver 0000:00:07.0: found MSI capability
[    1.674948] pcieport-driver 0000:00:07.0: irq 2301 for MSI/MSI-X
[    1.674961] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.674979] pci_express 0000:00:07.0:pcie02: allocate port service
[    1.675056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.675330] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.675539] ACPI: AC Adapter [AC0] (off-line)
[    1.675975] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.710690] ACPI: Battery Slot [BAT0] (battery present)
[    1.710766] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.710769] ACPI: Power Button (FF) [PWRF]
[    1.710830] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.710833] ACPI: Power Button (CM) [PWRB]
[    1.710883] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.710889] ACPI: Sleep Button (CM) [SLPB]
[    1.710940] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.721123] ACPI: Lid Switch [LID]
[    1.721917] ACPI: SSDT BFFCE390, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.722587] ACPI: SSDT BFFCE630, 06D9 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.723234] Monitor-Mwait will be used to enter C-1 state
[    1.723238] Monitor-Mwait will be used to enter C-2 state
[    1.723240] Monitor-Mwait will be used to enter C-3 state
[    1.723257] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.723286] processor ACPI_CPU:00: registered as cooling_device0
[    1.723289] ACPI: Processor [P001] (supports 8 throttling states)
[    1.723746] ACPI: SSDT BFFCE2C0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    1.724213] ACPI: SSDT BFFCE5A0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    1.725555] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.725574] processor ACPI_CPU:01: registered as cooling_device1
[    1.725578] ACPI: Processor [P002] (supports 8 throttling states)
[    1.729748] thermal LNXTHERM:01: registered as thermal_zone0
[    1.730938] ACPI: Thermal Zone [THRM] (55 C)
[    1.773276] Linux agpgart interface v0.103
[    1.773286] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.774385] brd: module loaded
[    1.774729] loop: module loaded
[    1.774797] Fixed MDIO Bus: probed
[    1.774803] PPP generic driver version 2.4.2
[    1.774868] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.774897] Driver 'sd' needs updating - please use bus_type methods
[    1.774907] Driver 'sr' needs updating - please use bus_type methods
[    1.775060] sata_sis 0000:00:05.0: version 1.0
[    1.775078] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.775083] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.775194] scsi0 : sata_sis
[    1.775282] scsi1 : sata_sis
[    1.776024] ata1: PATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xb800 irq 17
[    1.776027] ata2: PATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb808 irq 17
[    1.965998] ata1.00: ATA-8: ST9320421AS, SD14, max UDMA/133
[    1.966000] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.025996] ata1.00: configured for UDMA/133
[    2.188214] ata2.00: ATAPI: MATSHITADVD-RAM UJ880AS, 1.00, max UDMA/33
[    2.204228] ata2.00: configured for UDMA/33
[    2.205118] scsi 0:0:0:0: Direct-Access     ATA      ST9320421AS      SD14 PQ: 0 ANSI: 5
[    2.205222] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.205240] sd 0:0:0:0: [sda] Write Protect is off
[    2.205243] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.205271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.205348] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.205364] sd 0:0:0:0: [sda] Write Protect is off
[    2.205367] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.205394] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.205398]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    2.349925] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.349968] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.352442] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ880AS  1.00 PQ: 0 ANSI: 5
[    2.354656] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.354659] Uniform CD-ROM driver Revision: 3.20
[    2.354744] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.354791] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.355186] pata_sis 0000:00:02.5: version 0.5.2
[    2.355287] scsi2 : pata_sis
[    2.355352] scsi3 : pata_sis
[    2.356013] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
[    2.356015] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
[    2.508077] ata4: port disabled. ignoring.
[    2.508188] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.508207] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.508224] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    2.508285] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    2.508331] ehci_hcd 0000:00:03.3: irq 22, io mem 0xf9ffd000
[    2.521007] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    2.521090] usb usb1: configuration #1 chosen from 1 choice
[    2.521119] hub 1-0:1.0: USB hub found
[    2.521129] hub 1-0:1.0: 8 ports detected
[    2.521239] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.521254] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.521264] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.521312] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    2.521331] ohci_hcd 0000:00:03.0: irq 20, io mem 0xf9fff000
[    2.578051] usb usb2: configuration #1 chosen from 1 choice
[    2.578080] hub 2-0:1.0: USB hub found
[    2.578088] hub 2-0:1.0: 4 ports detected
[    2.578175] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.578186] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    2.578235] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    2.578251] ohci_hcd 0000:00:03.1: irq 21, io mem 0xf9ffe000
[    2.634057] usb usb3: configuration #1 chosen from 1 choice
[    2.634085] hub 3-0:1.0: USB hub found
[    2.634092] hub 3-0:1.0: 4 ports detected
[    2.634179] uhci_hcd: USB Universal Host Controller Interface driver
[    2.634231] usbcore: registered new interface driver libusual
[    2.634263] usbcore: registered new interface driver usbserial
[    2.634273] USB Serial support registered for generic
[    2.634290] usbcore: registered new interface driver usbserial_generic
[    2.634292] usbserial: USB Serial Driver core
[    2.634340] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.636289] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.638448] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.638454] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.638456] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.638458] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.638461] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.649037] mice: PS/2 mouse device common for all mice
[    2.709056] rtc_cmos 00:08: RTC can wake from S4
[    2.709093] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.709114] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[    2.709177] device-mapper: uevent: version 1.0.3
[    2.709265] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.709341] device-mapper: multipath: version 1.0.5 loaded
[    2.709344] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.709520] cpuidle: using governor ladder
[    2.709639] cpuidle: using governor menu
[    2.710080] TCP cubic registered
[    2.710153] NET: Registered protocol family 10
[    2.710579] lo: Disabled Privacy Extensions
[    2.710895] NET: Registered protocol family 17
[    2.710915] Bluetooth: L2CAP ver 2.11
[    2.710917] Bluetooth: L2CAP socket layer initialized
[    2.710920] Bluetooth: SCO (Voice Link) ver 0.6
[    2.710921] Bluetooth: SCO socket layer initialized
[    2.710949] Marking TSC unstable due to TSC halts in idle
[    2.710958] Bluetooth: RFCOMM socket layer initialized
[    2.710963] Bluetooth: RFCOMM TTY layer initialized
[    2.710965] Bluetooth: RFCOMM ver 1.10
[    2.711566] registered taskstats version 1
[    2.711643]   Magic number: 5:788:723
[    2.711653] block loop3: hash matches
[    2.711747] rtc_cmos 00:08: setting system clock to 2009-08-18 07:43:32 UTC (1250581412)
[    2.711749] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.711750] EDD information not available.
[    2.711778] Freeing unused kernel memory: 536k freed
[    2.712020] Write protecting the kernel read-only data: 6708k
[    2.749090] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.849049] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    3.026220] usb 1-5: configuration #1 chosen from 1 choice
[    3.445045] usb 3-3: new full speed USB device using ohci_hcd and address 2
[    3.668191] usb 3-3: configuration #1 chosen from 1 choice
[    6.173808] ISO 9660 Extensions: Microsoft Joliet Level 3
[    6.222678] ISO 9660 Extensions: RRIP_1991A
[    6.540209] aufs 20080922
[    6.811628] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   72.077021] udev: starting version 141
[   74.308227] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   74.308326] usbcore: registered new interface driver btusb
[   74.832803] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   74.918730] asus-laptop: Asus Laptop Support version 0.42
[   74.923539] asus-laptop:   F50Sf model detected
[   74.929474] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
[   74.986495] acpi device:19: registered as cooling_device2
[   74.986647] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/input/input7
[   75.013103] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   75.180033] sis190 Gigabit Ethernet driver 1.2 loaded.
[   75.180064] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   75.180079] sis190 0000:00:04.0: setting latency timer to 64
[   75.180117] 0000:00:04.0: Read MAC address from EEPROM
[   75.180118] 0000:00:04.0: Error EEPROM read 0.
[   75.180120] 0000:00:04.0: Read MAC address from APC.
[   75.212048] 0000:00:04.0: Unknown PHY transceiver at address 0.
[   75.234035] Linux video capture interface: v2.00
[   75.343443] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (064e:a116)
[   75.344993] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.0/input/input8
[   75.357448] usbcore: registered new interface driver uvcvideo
[   75.357464] USB Video Class driver (v0.1.0)
[   75.393689] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   75.740070] 0000:00:04.0: Using transceiver at address 1 as default.
[   75.773332] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at ffffc200101f0c00 (IRQ: 19), 00:26:18:6c:7d:94
[   75.773334] eth0: RGMII mode.
[   75.773340] eth0: Enabling Auto-negotiation.
[   75.804126] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   75.804235] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   75.837846] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   76.000040] Clocksource tsc unstable (delta = -143602655 ns)
[   76.284479] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   76.322960] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   78.816546] Adding 4433900k swap on /dev/sda7.  Priority:-1 extents:1 across:4433900k
[   87.205446] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   87.205449] Bluetooth: BNEP filters: protocol multicast
[   87.426821] Bridge firewalling registered
[   95.287185] mtrr: base(0xfb000000) is not aligned on a size(0xe00000) boundary
[   96.115214] lp: driver loaded but no devices found
[   96.697543] ppdev: user-space parallel port driver
[   99.215940] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  107.670910] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation Device 0654 (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
ubuntu@ubuntu:~$ 


Please help.
Also, the sound is not working i think, so we can fix that later.

---

### Post by sanderj on 2009-08-17
I think the relevant parts are:

```
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)

[ 99.215940] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

Googling for "Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)", I see these bugs:


[https://bugs.launchpad.net/ubuntu/+bug/345374](https://bugs.launchpad.net/ubuntu/+bug/345374)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330594](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330594)

These seem 64-bit bugs. Have you tried the 32-bit: does ethernet work there? If so, confirm those bugs as 64-bit bugs on Launchpad (and subscribe to them). You could then try Ubuntu 9.10 Karmic Alpha 4 to see if they are solved there.
As a workaround on 9.04 64-bit, you could try the "workaround change MTU to 1492" method.

HTH

---

### Post by noob707 on 2009-08-17
What i did is a edited the Wired eth0 conection and set the MTU to 1492 and made it connect automatically but that didn't help and still no internet.

I gonna try to update to KArmic Alpha 4 and see if that helps, so i will message back when i get Karmic up and running.

To upgrade without internet, i need to download the Alternate CD right?

---

### Post by sanderj on 2009-08-17
> **noob707 said:**
> 
I gonna try to update to KArmic Alpha 4 and see if that helps, so i will message back when i get Karmic up and running.

To upgrade without internet, i need to download the Alternate CD right?

Yes, indeed. Download here [http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/) , and the boot the Karmic Alpha 4 live CD. Do NOT upgrade an existing installation; boot & run Karmic Alpha 4 freshly from the Live CD. Only that way you can avoid any previous - possibly incorrect - configuration settings.

A few more questions:
- what kind of internet connection do you have? You do have an ADSL or Cable router that does DHCP and NAT, I hope? 
- you have not yet posted ifconfig, so please do that.
- Ubuntu is not offering a proprietary driver in the upper right corner, is it?

---

### Post by noob707 on 2009-08-17
crap, i did an upgrade and my internet now works fine but i have lockups whenever i try to update from terminal or update manager.

---

### Post by sanderj on 2009-08-17
> **noob707 said:**
> crap, i did an upgrade and my internet now works fine but i have lockups whenever i try to update from terminal or update manager.

And what if you live-boot the 64-bit Karmic Alpha 4? Does Internet work? If so, do you experience lockups when updating the live session?

Have you already confirmed & subscribed to the two bug reports I mentioned?

---

### Post by noob707 on 2009-08-17
so, i tried the update manager from the live boot and it still lockuped my laptop. i posted this on launchpad and hopefully it will get fixed.

---

