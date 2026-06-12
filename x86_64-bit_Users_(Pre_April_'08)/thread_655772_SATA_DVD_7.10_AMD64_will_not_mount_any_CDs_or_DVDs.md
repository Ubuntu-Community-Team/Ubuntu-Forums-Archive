---
title: "SATA DVD 7.10 AMD64 will not mount any CDs or DVDs"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by averagejoe84 on 2008-01-01
Hello all I hope there is someone out there who can provide some assistance. I decided that to bring in the new year I would make the jump to x64. Sadly I have had little success. I downloaded the alternate install cd Burned it and began my install only to get stopped before it got going. I was presented with the following error.

> Your installation CD-ROM couldn't me mounted. This probably means that the cdrom was not in the drive. If so you can insert it and try again.

After doing a bit of research I determined that I could by pass this error simply by using a IDE cdrom drive I had laying around the house. From then on it was smooth sailing. Until the install was complete. I removed the IDE cdrom, and went along with my configuring of the system. When it came time to install my games I discovered that my SATA DVDROM and DVD burnner were still not able to mount any cds. When a cd was insterted It would attempt  to auto mount and then give me an error message saying it couldn't mount the cd. I tried numerous cds and DVDs but none will mount. I then Flashed my motherboard Bios in hope that might correct the problem as It did for others in the forums. not luck it seems to have worsend the problem, now when a cd is inserted to my cdrom drives the computer restarts. I hope there is some one out there who can help.Listed below is all of the information I could think to provide.

dmesg
> [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=67fdd8ff-c336-435f-b041-d67be5fab500 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6F40 checksum 0
[    0.000000] ACPI: RSDP 000F6F40, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT CFEE3100, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP CFEE9BC0, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT CFEE3280, 68C9 (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: HPET CFEE9DC0, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG CFEE9E40, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC CFEE9D00, 007C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1245184
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   851680
[    0.000000]     0:  1048576 ->  1245184
[    0.000000] On node 0 totalpages: 1048191
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1127 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 1030040
[    0.000000] Kernel command line: root=UUID=67fdd8ff-c336-435f-b041-d67be5fab500 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   21.571108] time.c: Detected 3015.453 MHz processor.
[   21.573764] Console: colour VGA+ 80x25
[   21.573776] Checking aperture...
[   21.573778] CPU 0: aperture @ 4000000 size 32 MB
[   21.573779] Aperture too small (32 MB)
[   21.578188] No AGP bridge found
[   21.578189] Your BIOS doesn't leave a aperture memory hole
[   21.578190] Please enable the IOMMU option in the BIOS setup
[   21.578191] This costs you 64 MB of RAM
[   21.595859] Mapping aperture over 65536 KB of RAM @ 4000000
[   21.620243] Memory: 4047164k/4980736k available (2274k kernel code, 145600k reserved, 1181k data, 296k init)
[   21.620274] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.697726] Calibrating delay using timer specific routine.. 6034.13 BogoMIPS (lpj=12068266)
[   21.697746] Security Framework v1.0.0 initialized
[   21.697751] SELinux:  Disabled at boot.
[   21.697933] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   21.699437] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   21.700223] Mount-cache hash table entries: 256
[   21.700314] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.700316] CPU: L2 Cache: 1024K (64 bytes/line)
[   21.700317] CPU 0/0 -> Node 0
[   21.700319] CPU: Physical Processor ID: 0
[   21.700320] CPU: Processor Core ID: 0
[   21.700332] SMP alternatives: switching to UP code
[   21.700489] Early unpacking initramfs... done
[   21.894107] ACPI: Core revision 20070126
[   21.894147] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.937839] Using local APIC timer interrupts.
[   21.970946] result 12564394
[   21.970947] Detected 12.564 MHz APIC timer.
[   21.973289] SMP alternatives: switching to SMP code
[   21.973345] Booting processor 1/2 APIC 0x1
[   21.983733] Initializing CPU#1
[   22.061432] Calibrating delay using timer specific routine.. 6030.97 BogoMIPS (lpj=12061958)
[   22.061437] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.061438] CPU: L2 Cache: 1024K (64 bytes/line)
[   22.061440] CPU 1/1 -> Node 0
[   22.061441] CPU: Physical Processor ID: 0
[   22.061442] CPU: Processor Core ID: 1
[   22.061520] AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03
[   22.065097] Brought up 2 CPUs
[   22.587441] migration_cost=206
[   22.587242] NET: Registered protocol family 16
[   22.587301] ACPI: bus type pci registered
[   22.587305] PCI: Using configuration type 1
[   22.588245] ACPI: EC: Look up EC in DSDT
[   22.592660] ACPI: Interpreter enabled
[   22.592662] ACPI: (supports S0 S1 S3 S4 S5)
[   22.592674] ACPI: Using IOAPIC for interrupt routing
[   22.598719] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.598725] PCI: Probing PCI hardware (bus 00)
[   22.599067] PCI: Transparent bridge - 0000:00:09.0
[   22.599263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.599469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.623910] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.624029] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.624161] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.624277] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.624393] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.624510] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.624628] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.624744] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.624859] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.624975] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.625093] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.625209] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.625325] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.625448] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.625570] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.625691] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.625820] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   22.625944] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   22.626068] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   22.626192] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   22.626275] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   22.626404] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   22.626532] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   22.626659] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.626786] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   22.626914] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   22.627041] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.627168] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   22.627295] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.627429] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.627562] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   22.627694] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   22.627758] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.627765] pnp: PnP ACPI init
[   22.627771] ACPI: bus type pnp registered
[   22.630885] pnp: PnP ACPI: found 14 devices
[   22.630887] ACPI: ACPI bus type pnp unregistered
[   22.630922] PCI: Using ACPI for IRQ routing
[   22.630924] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.630969] NET: Registered protocol family 8
[   22.630970] NET: Registered protocol family 20
[   22.631008] PCI-DMA: Disabling AGP.
[   22.631339] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   22.631343] PCI-DMA: using GART IOMMU.
[   22.631351] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   22.631471] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[   22.631474] hpet0: 3 32-bit timers, 25000000 Hz
[   22.632587] pnp: 00:01: ioport range 0x4000-0x407f has been reserved
[   22.632589] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
[   22.632591] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
[   22.632593] pnp: 00:01: ioport range 0x4480-0x44ff has been reserved
[   22.632595] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
[   22.632597] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
[   22.632608] pnp: 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.632612] pnp: 00:0d: iomem range 0xcce00-0xcffff has been reserved
[   22.632614] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[   22.632616] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   22.632618] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   22.632835] PCI: Bridge: 0000:00:09.0
[   22.632836]   IO window: b000-bfff
[   22.632838]   MEM window: fdf00000-fdffffff
[   22.632840]   PREFETCH window: disabled.
[   22.632842] PCI: Bridge: 0000:00:0b.0
[   22.632842]   IO window: disabled.
[   22.632844]   MEM window: disabled.
[   22.632845]   PREFETCH window: disabled.
[   22.632847] PCI: Bridge: 0000:00:0c.0
[   22.632848]   IO window: disabled.
[   22.632849]   MEM window: disabled.
[   22.632850]   PREFETCH window: disabled.
[   22.632852] PCI: Bridge: 0000:00:0d.0
[   22.632853]   IO window: disabled.
[   22.632854]   MEM window: disabled.
[   22.632856]   PREFETCH window: disabled.
[   22.632858] PCI: Bridge: 0000:00:0e.0
[   22.632859]   IO window: a000-afff
[   22.632861]   MEM window: f8000000-fbffffff
[   22.632863]   PREFETCH window: d0000000-dfffffff
[   22.632868] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.632874] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.632878] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.632882] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   22.632886] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.632894] NET: Registered protocol family 2
[   22.636444] Time: hpet clocksource has been installed.
[   22.692075] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.692971] TCP established hash table entries: 524288 (order: 11, 12582912 bytes)
[   22.697093] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.697541] TCP: Hash tables configured (established 524288 bind 65536)
[   22.697543] TCP reno registered
[   22.712053] checking if image is initramfs... it is
[   23.192419] Freeing initrd memory: 7193k freed
[   23.196000] audit: initializing netlink socket (disabled)
[   23.196011] audit(1199233229.604:1): initialized
[   23.197333] VFS: Disk quotas dquot_6.5.1
[   23.197367] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.197422] io scheduler noop registered
[   23.197423] io scheduler anticipatory registered
[   23.197424] io scheduler deadline registered
[   23.197481] io scheduler cfq registered (default)
[   23.227809] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   23.227817] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.227821] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   23.227826] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.227830] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   23.227836] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.227840] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   23.227845] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.227851] Boot video device is 0000:05:00.0
[   23.227942] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.227955] assign_interrupt_mode Found MSI capability
[   23.227957] Allocate Port Service[0000:00:0b.0:pcie00]
[   23.228001] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.228013] assign_interrupt_mode Found MSI capability
[   23.228014] Allocate Port Service[0000:00:0c.0:pcie00]
[   23.228050] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.228062] assign_interrupt_mode Found MSI capability
[   23.228064] Allocate Port Service[0000:00:0d.0:pcie00]
[   23.228097] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.228109] assign_interrupt_mode Found MSI capability
[   23.228110] Allocate Port Service[0000:00:0e.0:pcie00]
[   23.242761] Real Time Clock Driver v1.12ac
[   23.242896] hpet_resources: 0xfefff000 is busy
[   23.242920] Linux agpgart interface v0.102 (c) Dave Jones
[   23.242922] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.242994] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.243376] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.243852] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.244004] input: Macintosh mouse button emulation as /class/input/input0
[   23.244048] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   23.244050] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   23.244393] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.244396] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.244466] mice: PS/2 mouse device common for all mice
[   23.244544] TCP cubic registered
[   23.244584] NET: Registered protocol family 1
[   23.244716] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.244721] Freeing unused kernel memory: 296k freed
[   23.319336] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.365754] AppArmor: AppArmor initialized<5>audit(1199233230.780:2):  type=1505 info="AppArmor initialized" pid=1259
[   24.377276] fuse init (API version 7.8)
[   24.380177] Failure registering capabilities with primary security module.
[   24.413071] ACPI: Fan [FAN] (on)
[   24.445534] ACPI: Thermal Zone [THRM] (40 C)
[   24.794924] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.794928] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.795264] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   24.795276] NFORCE-CK804: chipset revision 242
[   24.795278] NFORCE-CK804: not 100% native mode: will probe irqs later
[   24.795282] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   24.795285] NFORCE-CK804: neither IDE port enabled (BIOS)
[   24.800621] SCSI subsystem initialized
[   24.806210] libata version 2.21 loaded.
[   24.812544] usbcore: registered new interface driver usbfs
[   24.812566] usbcore: registered new interface driver hub
[   24.812585] usbcore: registered new device driver usb
[   24.813071] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.813318] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   24.813324] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   24.813643] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.813649] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   24.813783] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   24.813798] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[   24.874666] usb usb1: configuration #1 chosen from 1 choice
[   24.874685] hub 1-0:1.0: USB hub found
[   24.874692] hub 1-0:1.0: 8 ports detected
[   24.875460] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   24.888635] Floppy drive(s): fd0 is 1.44M
[   24.911687] FDC 0 is a post-1991 82077
[   24.981019] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   24.981027] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   24.981645] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   24.981650] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   24.981878] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   24.981899] ehci_hcd 0000:00:02.1: debug port 1
[   24.981901] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   24.981909] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
[   24.981914] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.982149] usb usb2: configuration #1 chosen from 1 choice
[   24.982251] hub 2-0:1.0: USB hub found
[   24.982256] hub 2-0:1.0: 8 ports detected
[   25.088783] sata_nv 0000:00:07.0: version 3.4
[   25.089058] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   25.089064] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   25.089067] sata_nv 0000:00:07.0: Using ADMA mode
[   25.089317] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   25.089741] scsi0 : sata_nv
[   25.089876] scsi1 : sata_nv
[   25.089921] ata1: SATA max UDMA/133 cmd 0xffffc2000142c480 ctl 0xffffc2000142c4a0 bmdma 0x000000000001dc00 irq 21
[   25.089924] ata2: SATA max UDMA/133 cmd 0xffffc2000142c580 ctl 0xffffc2000142c5a0 bmdma 0x000000000001dc08 irq 21
[   25.563042] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   25.631264] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   25.730824] ata1.00: ATAPI: ASUS    DVD-E616A3T, 1.10, max UDMA/100
[   25.855955] usb 1-1: configuration #1 chosen from 1 choice
[   25.863829] usbcore: registered new interface driver hiddev
[   25.875115] input: Logitech USB Receiver as /class/input/input2
[   25.875211] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1
[   25.875221] usbcore: registered new interface driver usbhid
[   25.875224] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.910524] ata1.00: configured for UDMA/100
[   26.225890] ata2: SATA link down (SStatus 0 SControl 300)
[   26.227182] scsi 0:0:0:0: CD-ROM            ASUS     DVD-E616A3T      1.10 PQ: 0 ANSI: 5
[   26.227189] ata1: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   26.227523] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   26.227529] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   26.227532] sata_nv 0000:00:08.0: Using ADMA mode
[   26.227740] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   26.227820] scsi2 : sata_nv
[   26.227869] scsi3 : sata_nv
[   26.227921] ata3: SATA max UDMA/133 cmd 0xffffc2000142e480 ctl 0xffffc2000142e4a0 bmdma 0x000000000001c800 irq 20
[   26.227925] ata4: SATA max UDMA/133 cmd 0xffffc2000142e580 ctl 0xffffc2000142e5a0 bmdma 0x000000000001c808 irq 20
[   26.701071] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.713589] ata3.00: ATA-6: ST380817AS, 3.42, max UDMA/133
[   26.713591] ata3.00: 156301488 sectors, multi 1: LBA48 NCQ (depth 31/32)
[   26.737523] ata3.00: configured for UDMA/133
[   27.208192] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.375971] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-H62N, CL00, max UDMA/100
[   27.555660] ata4.00: configured for UDMA/100
[   27.556062] scsi 2:0:0:0: Direct-Access     ATA      ST380817AS       3.42 PQ: 0 ANSI: 5
[   27.556067] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   27.559643] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H62N  CL00 PQ: 0 ANSI: 5
[   27.559646] ata4: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   27.560103] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   27.560108] ACPI: PCI Interrupt 0000:01:01.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   27.613150] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   27.618898] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   27.618900] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   27.618903] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   27.618909] forcedeth: using HIGHDMA
[   27.624931] sr0: scsi3-mmc drive: 0x/0x caddy
[   27.624936] Uniform CD-ROM driver Revision: 3.20
[   27.625062] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   27.625473] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   27.625482] sd 2:0:0:0: [sda] Write Protect is off
[   27.625484] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.625493] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.625525] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   27.625531] sd 2:0:0:0: [sda] Write Protect is off
[   27.625532] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.625541] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.625543]  sda:sr1: scsi3-mmc drive: 0x/0x caddy
[   27.628986] sr 3:0:0:0: Attached scsi CD-ROM sr1
[   27.631373] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   27.631387] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   27.631400] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   27.643307]  sda1 sda2 < sda5 >
[   27.659387] sd 2:0:0:0: [sda] Attached SCSI disk
[   27.890174] Attempting manual resume
[   27.890177] swsusp: Resume From Partition 8:5
[   27.890178] PM: Checking swsusp image.
[   27.890341] PM: Resume from disk failed.
[   27.900855] EXT3-fs: INFO: recovery required on readonly filesystem.
[   27.900858] EXT3-fs: write access will be enabled during recovery.
[   28.143148] eth0: forcedeth.c: subsystem: 01043:812a bound to 0000:00:0a.0
[   28.893685] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000158acbe]
[   29.009809] kjournald starting.  Commit interval 5 seconds
[   29.009821] EXT3-fs: sda1: orphan cleanup on readonly fs
[   29.009826] ext3_orphan_cleanup: deleting unreferenced inode 3588342
[   29.009853] EXT3-fs: sda1: 1 orphan inode deleted
[   29.009855] EXT3-fs: recovery complete.
[   29.029832] EXT3-fs: mounted filesystem with ordered data mode.
[   35.234582] gameport: EMU10K1 is pci0000:01:06.1/gameport0, io 0xb400, speed 1202kHz
[   35.277812] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   35.277827] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   35.288265] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.290496] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.321629] input: PC Speaker as /class/input/input3
[   35.419950] usbcore: registered new interface driver lmpcm_usb
[   35.419955] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   35.445816] parport_pc 00:0a: reported by Plug and Play ACPI
[   35.445838] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   35.461109] nvidia: module license 'NVIDIA' taints kernel.
[   35.714230] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   35.714239] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   35.714245] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   35.714377] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   35.991629] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   35.991637] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   36.502850] loop: module loaded
[   36.524092] lp0: using parport0 (interrupt-driven).
[   36.626139] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   36.844125] EXT3 FS on sda1, internal journal
[   37.565127] No dock devices found.
[   37.663589] input: Power Button (FF) as /class/input/input4
[   37.663749] ACPI: Power Button (FF) [PWRF]
[   37.680762] input: Power Button (CM) as /class/input/input5
[   37.680790] ACPI: Power Button (CM) [PWRB]
[   37.830182] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ processors (version 2.00.00)
[   37.829811] powernow-k8: MP systems not supported by PSB BIOS structure
[   37.846160] powernow-k8: MP systems not supported by PSB BIOS structure
[   39.079499] ppdev: user-space parallel port driver
[   39.246752] audit(1199233245.794:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4957 profile="/usr/sbin/cupsd"
[   39.457856] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   39.457860] vboxdrv: Successfully done.
[   39.741428] Failure registering capabilities with primary security module.
[   39.927330] Bluetooth: Core ver 2.11
[   39.927372] NET: Registered protocol family 31
[   39.927374] Bluetooth: HCI device and connection manager initialized
[   39.927376] Bluetooth: HCI socket layer initialized
[   39.931116] Bluetooth: L2CAP ver 2.8
[   39.931119] Bluetooth: L2CAP socket layer initialized
[   39.953791] Bluetooth: RFCOMM socket layer initialized
[   39.953804] Bluetooth: RFCOMM TTY layer initialized
[   39.953805] Bluetooth: RFCOMM ver 1.8
[   44.077680] NET: Registered protocol family 17
[   72.529445] NET: Registered protocol family 10
[   72.529548] lo: Disabled Privacy Extensions
[   83.383333] eth0: no IPv6 routers present

The Error from a manual mount
> jprenger@ubuntu:~$ mount /dev/scd1
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Dmesg out put after mount command
> jprenger@ubuntu:~$ dmesg | tail -51
[   83.383333] eth0: no IPv6 routers present
[  321.128066] attempt to access beyond end of device
[  321.128072] sr1: rw=0, want=4784545824, limit=11127488
[  321.128161] attempt to access beyond end of device
[  321.128163] sr1: rw=0, want=4784544800, limit=11127488
[  321.128244] attempt to access beyond end of device
[  321.128246] sr1: rw=0, want=4784544576, limit=11127488
[  321.128326] attempt to access beyond end of device
[  321.128328] sr1: rw=0, want=4784545816, limit=11127488
[  321.128400] attempt to access beyond end of device
[  321.128402] sr1: rw=0, want=4784544792, limit=11127488
[  321.128483] attempt to access beyond end of device
[  321.128485] sr1: rw=0, want=4784544568, limit=11127488
[  321.128566] attempt to access beyond end of device
[  321.128568] sr1: rw=0, want=4784545224, limit=11127488
[  321.128649] attempt to access beyond end of device
[  321.128651] sr1: rw=0, want=4784544200, limit=11127488
[  321.128730] attempt to access beyond end of device
[  321.128732] sr1: rw=0, want=4784543976, limit=11127488
[  321.128804] attempt to access beyond end of device
[  321.128806] sr1: rw=0, want=4784545216, limit=11127488
[  321.128879] attempt to access beyond end of device
[  321.128881] sr1: rw=0, want=4784544192, limit=11127488
[  321.128960] attempt to access beyond end of device
[  321.128962] sr1: rw=0, want=4784543968, limit=11127488
[  321.129036] attempt to access beyond end of device
[  321.129038] sr1: rw=0, want=3925781204, limit=11127488
[  321.129117] attempt to access beyond end of device
[  321.129119] sr1: rw=0, want=3925780180, limit=11127488
[  321.129192] attempt to access beyond end of device
[  321.129194] sr1: rw=0, want=3925779956, limit=11127488
[  321.129273] attempt to access beyond end of device
[  321.129275] sr1: rw=0, want=3925781196, limit=11127488
[  321.129355] attempt to access beyond end of device
[  321.129357] sr1: rw=0, want=3925780172, limit=11127488
[  321.129429] attempt to access beyond end of device
[  321.129431] sr1: rw=0, want=3925779948, limit=11127488
[  321.129512] attempt to access beyond end of device
[  321.129514] sr1: rw=0, want=3925780604, limit=11127488
[  321.129594] attempt to access beyond end of device
[  321.129596] sr1: rw=0, want=3925779580, limit=11127488
[  321.129675] attempt to access beyond end of device
[  321.129677] sr1: rw=0, want=3925779356, limit=11127488
[  321.129760] attempt to access beyond end of device
[  321.129762] sr1: rw=0, want=3925780596, limit=11127488
[  321.129840] attempt to access beyond end of device
[  321.129842] sr1: rw=0, want=3925779572, limit=11127488
[  321.129921] attempt to access beyond end of device
[  321.129923] sr1: rw=0, want=3925779348, limit=11127488
[  321.216656] UDF-fs: No partition found (1)
[  321.323522] Unable to identify CD-ROM format.


My Fstab

> jprenger@ubuntu:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=67fdd8ff-c336-435f-b041-d67be5fab500 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=180f2ba2-412e-4d41-9e8d-85c2e79b861a none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


My system hardware
> jprenger@ubuntu:~$ sudo lshw
[sudo] password for jprenger:
ubuntu                    
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=603CE624-6E99-DB11-8EE3-001D6020B3E1
  *-core
       description: Motherboard
       product: M2N-E SLI
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
       slot: FLOPPY
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS M2N-E SLI ACPI BIOS Revision 1102 (09/11/2007)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          slot: Socket AM2
          size: 3GHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 4GB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: DIMM_A1
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: DIMM_B1
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: DIMM_A2
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: DIMM_B2
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-cdrom
             description: SCSI CD-ROM
             product: DVD-E616A3T
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.10
             capabilities: removable audio
             configuration: ansiversion=5 status=open
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: SCSI Disk
             product: ST380817AS
             vendor: ATA
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.42
             serial: 5MR3PH7Z
             size: 74GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                capacity: 71GB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 3153MB
                capacity: 3153MB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3153MB
                   capabilities: nofs
        *-cdrom
             description: SCSI CD-ROM
             product: DVDRAM GSA-H62N
             vendor: HL-DT-ST
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: CL00
             capabilities: removable audio
             configuration: ansiversion=5 status=ready
           *-disc
                physical id: 0
                logical name: /dev/cdrom1
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:01:01.0
             version: c0
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: 6.1
             bus info: pci@0000:01:06.1
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: f3
          serial: 00:1d:60:20:b3:e1
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.0.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: G80 [GeForce 8800 GTS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp


My Kernel

> jprenger@ubuntu:~$ uname -r
2.6.22-14-generic

Thank you in advance

Joe

---

### Post by alexdin on 2008-01-08
Hello Joe.

Your situation is practically identitial with mine. I bought a new PC two weeks ago. It consists of:

ASUS M2N4-SLI motherboard,
AMD Athlon 64 X2 Dual Core Processor 5600+,
Two DDR2 800Mz 2Gb memory modules,
NVIDIA 8500 GT video adapter,
Samsung SATA HDD,
Optiarc SATA DVD-RW

I failed to install Slamd64 linux from my SATA DVD drive and I did it using my old IDE CD.
When I try to read any discs using DVD drive my system hangs or reboots. Investigating the problem I tried several 2.6 kernels with different compile and boot options and I found that all works perfectly on 32 bit kernel compiled for i386 architecture. But problems arise with 64 bit kernel compiled for x86_64. Problem on x86_64 disapperes when I limit the ammount of memory by using mem=2G boot parameter. Particulaly all works perfectly even when I put mem=4G (the ammount I have). But when I put mem=4G, system reports that i have only 3+. I've tested my memory - it's OK.  I found that when I limit memory to 4G or less the system don't use this memory range:

BIOS-e820: 0000000100000000 - 0000000130000000 (usable)

and DVD works. And when system uses this range DVD don't work. Why it is so - I don't know yet. May be this is kernel bug or motherboard bug? I'm searching for answer too...

---

### Post by crjackson on 2008-01-09
> **alexdin said:**
> Hello Joe.

Your situation is practically identitial with mine. I bought a new PC two weeks ago. It consists of:

ASUS M2N4-SLI motherboard,
AMD Athlon 64 X2 Dual Core Processor 5600+,
Two DDR2 800Mz 2Gb memory modules,
NVIDIA 8500 GT video adapter,
Samsung SATA HDD,
Optiarc SATA DVD-RW

I failed to install Slamd64 linux from my SATA DVD drive and I did it using my old IDE CD.
When I try to read any discs using DVD drive my system hangs or reboots. Investigating the problem I tried several 2.6 kernels with different compile and boot options and I found that all works perfectly on 32 bit kernel compiled for i386 architecture. But problems arise with 64 bit kernel compiled for x86_64. Problem on x86_64 disapperes when I limit the ammount of memory by using mem=2G boot parameter. Particulaly all works perfectly even when I put mem=4G (the ammount I have). But when I put mem=4G, system reports that i have only 3+. I've tested my memory - it's OK.  I found that when I limit memory to 4G or less the system don't use this memory range:

BIOS-e820: 0000000100000000 - 0000000130000000 (usable)

and DVD works. And when system uses this range DVD don't work. Why it is so - I don't know yet. May be this is kernel bug or motherboard bug? I'm searching for answer too...

I hope you filed a bug report on launch pad...

---

### Post by alexdin on 2008-01-10
Yes, I've just sent the bug report to linux-kernel@. This bug was already reported to them and they made a patch. It is there in the current unstable 2.6.24-rc7. But it does not work either. I compiled this new 2.6.24-rc7, booted my PC and found that nothing changed. :(

One more workaround (beside memory limiting) is to disable ADMA by putting sata_nv.adma=0 as a boot parameter (if sata_nv was compiled-in the kernel and not as a module).

---

### Post by Yellow Pasque on 2008-01-10
averagejoe84, please use [ code ] instead of [ quote ].

It would make your post much easier to read.

---

### Post by alexdin on 2008-02-04
Robert Hancock posted a patch for 2.6.24 kernel that seems to solve this problem. I've tested it on my hardware and it seems to work OK. You could help to kernel developers by testing this patch on your hardware too and reporting if it doesn't work in your case.

The patch:  [https://bugzilla.redhat.com/attachment.cgi?id=293360](https://bugzilla.redhat.com/attachment.cgi?id=293360)
The thread on linux-kernel mail list: [http://www.gossamer-threads.com/lists/linux/kernel/862744?do=post_view_threaded](http://www.gossamer-threads.com/lists/linux/kernel/862744?do=post_view_threaded)

---

