---
title: "USB: ehci before ohci ? howto ..."
date: 2009-11-04
forum: x86 64-bit Users
---

### Post by johenkel on 2009-11-04
Hi there.
I got a Compaq SR1817CL, AMD64, 512MB RAM.
I had Linux Mint 7 running and just installed Ubuntu 9.10.

The usb does not seem to be working. If I insert a usb drive it does not get mounted.
However, lsusb shows:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If I stick the usb hd in, /var/log/messages shows :
[ 1021.690049] usb 1-8: new high speed USB device using ehci_hcd and address 10

So clearly, it is there.
I read in a different article, that I might need to start ehci_hcd before ohci_hcd, but how do I do that ?

Any ideas how I can get my usb working ?
Help greatly appreciated !!!!

johenkel

Couldn't attach dmesg file. So I include it below:
[
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=fb2f67a0-1621-4af0-9ddd-45f082d1439e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bef3000 - 000000001bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1bef0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CFFFF uncachable
[    0.000000]   D0000-D7FFF write-back
[    0.000000]   D8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFF0000000 write-back
[    0.000000]   1 base 0010000000 mask FFF8000000 write-back
[    0.000000]   2 base 0018000000 mask FFFC000000 write-back
[    0.000000]   3 base 001BF00000 mask FFFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  modified: 000000001bef0000 - 000000001bef3000 (ACPI NVS)
[    0.000000]  modified: 000000001bef3000 - 000000001bf00000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000001bef0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 001be00000 page 2M
[    0.000000]  001be00000 - 001bef0000 page 4k
[    0.000000] kernel direct mapping tables up to 1bef0000 @ 10000-13000
[    0.000000] RAMDISK: 147f3000 - 14f738a2
[    0.000000] ACPI: RSDP 00000000000f7b00 00014 (v00 HP-CPC)
[    0.000000] ACPI: RSDT 000000001bef3040 00038 (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 000000001bef30c0 00074 (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 000000001bef3180 04D8C (v01 HP-CPC AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 000000001bef0000 00040
[    0.000000] ACPI: SSDT 000000001bef8040 000D6 (v01 HP-CPC POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: SRAT 000000001bef8180 00090 (v01 HP-CPC HAMMER   00000001 AMD  00000001)
[    0.000000] ACPI: MCFG 000000001bef8280 0003C (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 000000001bef7f80 00068 (v01 HP-CPC AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-20000000
[    0.000000] NUMA: Allocated memnodemap from 11000 - 11440
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-000000001bef0000
[    0.000000]   NODE_DATA [0000000000011440 - 000000000001643f]
[    0.000000]   bootmap [0000000000017000 -  000000000001a7df] pages 4
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 001bef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [00147f3000 - 0014f738a2]          RAMDISK ==> [00147f3000 - 0014f738a2]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e324c]              BRK ==> [00019e3000 - 00019e324c]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [0000011000 - 0000011440]       MEMNODEMAP ==> [0000011000 - 0000011440]
[    0.000000] found SMP MP-table at [ffff8800000f5f00] f5f00
[    0.000000]  [ffffea0000000000-ffffea00007fffff] PMD -> [ffff880001e00000-ffff8800025fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001bef0
[    0.000000] On node 0 totalpages: 114303
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 100 pages reserved
[    0.000000]   DMA zone: 3827 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1509 pages used for memmap
[    0.000000]   DMA32 zone: 108811 pages, LIFO batch:31
[    0.000000] SB4X0 revision 0x82
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1bf00000 (gap: 1bf00000:c4100000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019eb000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 112638
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=fb2f67a0-1621-4af0-9ddd-45f082d1439e ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 388000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 430864k/457664k available (5313k kernel code, 452k absent, 26348k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1989.671 MHz processor.
[    0.000015] spurious 8259A interrupt: IRQ7.
[    0.000787] Console: colour VGA+ 80x25
[    0.000790] console [tty0] enabled
[    0.004391] allocated 5242880 bytes of page_cgroup
[    0.004394] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3979.34 BogoMIPS (lpj=19896710)
[    0.010044] Security Framework initialized
[    0.010072] AppArmor: AppArmor initialized
[    0.010136] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.010536] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.010735] Mount-cache hash table entries: 256
[    0.010904] Initializing cgroup subsys ns
[    0.010909] Initializing cgroup subsys cpuacct
[    0.010913] Initializing cgroup subsys memory
[    0.010923] Initializing cgroup subsys freezer
[    0.010925] Initializing cgroup subsys net_cls
[    0.010938] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010941] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010944] CPU 0/0x0 -> Node 0
[    0.010947] tseg: 001bf00000
[    0.010951] mce: CPU supports 5 MCE banks
[    0.010962] Performance Counters: AMD PMU driver.
[    0.010968] ... version:                 0
[    0.010969] ... bit width:               48
[    0.010971] ... generic counters:        4
[    0.010973] ... value mask:              0000ffffffffffff
[    0.010975] ... max period:              00007fffffffffff
[    0.010977] ... fixed-purpose counters:  0
[    0.010979] ... counter mask:            000000000000000f
[    0.010993] SMP alternatives: switching to UP code
[    0.020028] ACPI: Core revision 20090521
[    0.030084] Setting APIC routing to flat
[    0.030422] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.137893] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 02
[    0.140000] Brought up 1 CPUs
[    0.140000] Total of 1 processors activated (3979.34 BogoMIPS).
[    0.140000] CPU0 attaching NULL sched-domain.
[    0.140000] Booting paravirtualized kernel on bare hardware
[    0.140000] regulator: core version 0.5
[    0.140000] Time: 20:13:50  Date: 11/04/09
[    0.140000] NET: Registered protocol family 16
[    0.140000] node 0 link 0: io port [d000, ffff]
[    0.140000] TOM: 0000000020000000 aka 512M
[    0.140000] node 0 link 0: mmio [a0000, bffff]
[    0.140000] node 0 link 0: mmio [d8000000, dfffffff]
[    0.140000] node 0 link 0: mmio [20000000, d7ffffff]
[    0.140000] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.140000] node 0 link 0: mmio [e0000000, e02fffff]
[    0.140000] bus: [00,02] on node 0 link 0
[    0.140000] bus: 00 index 0 io port: [0, ffff]
[    0.140000] bus: 00 index 1 mmio: [a0000, bffff]
[    0.140000] bus: 00 index 2 mmio: [20000000, efffffff]
[    0.140000] bus: 00 index 3 mmio: [f0000000, fcffffffff]
[    0.140000] ACPI: bus type pci registered
[    0.140000] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.140000] PCI: MCFG area at e0000000 reserved in E820
[    0.140000] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.140000] PCI: Using configuration type 1 for base access
[    0.140000] bio: create slab <bio-0> at 0
[    0.140000] ACPI: EC: Look up EC in DSDT
[    0.142457] ACPI: Interpreter enabled
[    0.142461] ACPI: (supports S0 S1 S3 S4 S5)
[    0.142486] ACPI: Using IOAPIC for interrupt routing
[    0.146340] ACPI: No dock devices found.
[    0.146463] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.146610] pci 0000:00:12.0: reg 10 io port: [0xff00-0xff07]
[    0.146618] pci 0000:00:12.0: reg 14 io port: [0xfe00-0xfe03]
[    0.146627] pci 0000:00:12.0: reg 18 io port: [0xfd00-0xfd07]
[    0.146635] pci 0000:00:12.0: reg 1c io port: [0xfc00-0xfc03]
[    0.146643] pci 0000:00:12.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.146652] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f1ff]
[    0.146660] pci 0000:00:12.0: reg 30 32bit mmio: [0xfdf80000-0xfdffffff]
[    0.146692] pci 0000:00:12.0: supports D1 D2
[    0.146739] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.146840] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.146951] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.147017] pci 0000:00:13.2: supports D1 D2
[    0.147020] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.147025] pci 0000:00:13.2: PME# disabled
[    0.147077] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.147086] pci 0000:00:14.0: reg 14 32bit mmio: [0xfe02b000-0xfe02b3ff]
[    0.147120] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.147184] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.147192] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.147201] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.147209] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.147217] pci 0000:00:14.1: reg 20 io port: [0xf900-0xf90f]
[    0.147398] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe02a000-0xfe02a0ff]
[    0.147557] pci 0000:01:05.0: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.147561] pci 0000:01:05.0: reg 14 io port: [0xee00-0xeeff]
[    0.147565] pci 0000:01:05.0: reg 18 32bit mmio: [0xfddf0000-0xfddfffff]
[    0.147574] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.147582] pci 0000:01:05.0: supports D1 D2
[    0.147598] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.147601] pci 0000:00:01.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.147605] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd8000000-0xdfffffff]
[    0.147663] pci 0000:02:03.0: reg 10 io port: [0xde00-0xdeff]
[    0.147673] pci 0000:02:03.0: reg 14 32bit mmio: [0xfdcff000-0xfdcff0ff]
[    0.147741] pci 0000:02:03.0: supports D1 D2
[    0.147743] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.147749] pci 0000:02:03.0: PME# disabled
[    0.147813] pci 0000:02:09.0: reg 10 io port: [0xdc00-0xdcff]
[    0.147890] pci 0000:02:09.0: PME# supported from D3hot D3cold
[    0.147896] pci 0000:02:09.0: PME# disabled
[    0.147949] pci 0000:00:14.4: transparent bridge
[    0.147958] pci 0000:00:14.4: bridge io port: [0xd000-0xdfff]
[    0.147963] pci 0000:00:14.4: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.147969] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfde00000-0xfdefffff]
[    0.147984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.148176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.148331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.160827] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.160935] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.161041] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.161147] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.161253] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.161360] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11)
[    0.161465] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.161571] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.161756] SCSI subsystem initialized
[    0.161831] libata version 3.00 loaded.
[    0.161904] usbcore: registered new interface driver usbfs
[    0.161923] usbcore: registered new interface driver hub
[    0.161945] usbcore: registered new device driver usb
[    0.162058] ACPI: WMI: Mapper loaded
[    0.162060] PCI: Using ACPI for IRQ routing
[    0.162212] Bluetooth: Core ver 2.15
[    0.162243] NET: Registered protocol family 31
[    0.162245] Bluetooth: HCI device and connection manager initialized
[    0.162248] Bluetooth: HCI socket layer initialized
[    0.162250] NetLabel: Initializing
[    0.162252] NetLabel:  domain hash size = 128
[    0.162253] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.162267] NetLabel:  unlabeled traffic allowed by default
[    0.164130] pnp: PnP ACPI init
[    0.164154] ACPI: bus type pnp registered
[    0.166665] pnp: PnP ACPI: found 12 devices
[    0.166667] ACPI: ACPI bus type pnp unregistered
[    0.166678] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.166681] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.166684] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.166687] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.166690] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.166693] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.166696] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.166699] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.166702] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.166705] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.166708] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.166715] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.166718] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.166724] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.166729] system 00:0b: iomem range 0xd0000-0xd3fff has been reserved
[    0.166732] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    0.166735] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.166739] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.166742] system 00:0b: iomem range 0x1bf00000-0x1bffffff could not be reserved
[    0.166745] system 00:0b: iomem range 0x1bef0000-0x1befffff could not be reserved
[    0.166748] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.166751] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.166755] system 00:0b: iomem range 0x100000-0x1beeffff could not be reserved
[    0.166758] system 00:0b: iomem range 0x1c000000-0x1fffffff has been reserved
[    0.166761] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.166764] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.166768] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.171464] AppArmor: AppArmor Filesystem Enabled
[    0.171493] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.171496] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.171500] pci 0000:00:01.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.171504] pci 0000:00:01.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
[    0.171509] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.171513] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.171519] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff
[    0.171525] pci 0000:00:14.4:   PREFETCH window: 0xfde00000-0xfdefffff
[    0.171544] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.171547] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.171550] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.171552] pci_bus 0000:01: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.171555] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
[    0.171558] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.171561] pci_bus 0000:02: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.171564] pci_bus 0000:02: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.171567] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.171569] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.171610] NET: Registered protocol family 2
[    0.171709] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.172012] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.172166] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.172313] TCP: Hash tables configured (established 16384 bind 16384)
[    0.172315] TCP reno registered
[    0.172419] NET: Registered protocol family 1
[    0.172501] Trying to unpack rootfs image as initramfs...
[    0.180031] Switched to high resolution mode on CPU 0
[    0.371039] Freeing initrd memory: 7682k freed
[    0.376666] Scanning for low memory corruption every 60 seconds
[    0.376820] audit: initializing netlink socket (disabled)
[    0.376838] type=2000 audit(1257365630.370:1): initialized
[    0.386217] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.387589] VFS: Disk quotas dquot_6.5.2
[    0.387643] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.388258] fuse init (API version 7.12)
[    0.388336] msgmni has been set to 856
[    0.388556] alg: No test for stdrng (krng)
[    0.388567] io scheduler noop registered
[    0.388570] io scheduler anticipatory registered
[    0.388572] io scheduler deadline registered
[    0.388613] io scheduler cfq registered (default)
[    0.388622] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.460050] pci 0000:01:05.0: Boot video device
[    0.460174] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.460195] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.460307] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.460311] ACPI: Power Button [PWRF]
[    0.460360] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.460363] ACPI: Power Button [PWRB]
[    0.460410] fan PNP0C0B:00: registered as cooling_device0
[    0.460415] ACPI: Fan [FAN] (on)
[    0.460660] processor LNXCPU:00: registered as cooling_device1
[    0.460664] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.463974] thermal LNXTHERM:01: registered as thermal_zone0
[    0.463981] ACPI: Thermal Zone [THRM] (40 C)
[    0.465025] Linux agpgart interface v0.103
[    0.465037] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.466119] brd: module loaded
[    0.466528] loop: module loaded
[    0.466604] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.466857] sata_sil 0000:00:12.0: version 2.4
[    0.466903]   alloc irq_desc for 22 on node 0
[    0.466905]   alloc kstat_irqs on node 0
[    0.466913] sata_sil 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.467001] scsi0 : sata_sil
[    0.467107] scsi1 : sata_sil
[    0.467401] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    0.467406] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    0.467626]   alloc irq_desc for 16 on node 0
[    0.467628]   alloc kstat_irqs on node 0
[    0.467633] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.467748] scsi2 : pata_atiixp
[    0.467797] scsi3 : pata_atiixp
[    0.468864] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    0.468867] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    0.469415] Fixed MDIO Bus: probed
[    0.469451] PPP generic driver version 2.4.2
[    0.469560] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.469612]   alloc irq_desc for 19 on node 0
[    0.469614]   alloc kstat_irqs on node 0
[    0.469621] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.469640] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.469702] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.469771] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[    0.480023] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.480112] usb usb1: configuration #1 chosen from 1 choice
[    0.480139] hub 1-0:1.0: USB hub found
[    0.480147] hub 1-0:1.0: 8 ports detected
[    0.480237] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.480272] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.480286] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.480321] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.480339] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[    0.544074] usb usb2: configuration #1 chosen from 1 choice
[    0.544096] hub 2-0:1.0: USB hub found
[    0.544107] hub 2-0:1.0: 4 ports detected
[    0.544182] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.544195] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.544222] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.544238] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[    0.604073] usb usb3: configuration #1 chosen from 1 choice
[    0.604094] hub 3-0:1.0: USB hub found
[    0.604106] hub 3-0:1.0: 4 ports detected
[    0.604166] uhci_hcd: USB Universal Host Controller Interface driver
[    0.604286] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.606841] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.606846] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.606907] mice: PS/2 mouse device common for all mice
[    0.606996] rtc_cmos 00:03: RTC can wake from S4
[    0.607036] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.607063] rtc0: alarms up to one month, 242 bytes nvram
[    0.607156] device-mapper: uevent: version 1.0.3
[    0.607243] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.607315] device-mapper: multipath: version 1.1.0 loaded
[    0.607319] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.607449] cpuidle: using governor ladder
[    0.607451] cpuidle: using governor menu
[    0.607883] TCP cubic registered
[    0.608009] NET: Registered protocol family 10
[    0.608455] lo: Disabled Privacy Extensions
[    0.608734] NET: Registered protocol family 17
[    0.608755] Bluetooth: L2CAP ver 2.13
[    0.608757] Bluetooth: L2CAP socket layer initialized
[    0.608759] Bluetooth: SCO (Voice Link) ver 0.6
[    0.608761] Bluetooth: SCO socket layer initialized
[    0.608796] Bluetooth: RFCOMM TTY layer initialized
[    0.608799] Bluetooth: RFCOMM socket layer initialized
[    0.608801] Bluetooth: RFCOMM ver 1.11
[    0.608818] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[    0.608864] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[    0.608866] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8
[    0.608868] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[    0.608980] PM: Resume from disk failed.
[    0.608993] registered taskstats version 1
[    0.609106]   Magic number: 1:620:244
[    0.609199] rtc_cmos 00:03: setting system clock to 2009-11-04 20:13:51 UTC (1257365631)
[    0.609202] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.609204] EDD information not available.
[    0.634496] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.800020] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    0.810054] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    0.830317] ata1.00: ATA-7: WDC WD2000JS-60NCB1, 10.02E02, max UDMA/100
[    0.830321] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.850329] ata1.00: configured for UDMA/100
[    0.850432] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JS-60N 10.0 PQ: 0 ANSI: 5
[    0.850549] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.850583] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    0.850632] sd 0:0:0:0: [sda] Write Protect is off
[    0.850634] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.850655] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.850764]  sda: sda1 sda2 < sda5 >
[    0.885966] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.200042] ata2: SATA link down (SStatus 0 SControl 310)
[    1.400585] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-H552D, HP06, max UDMA/33
[    1.460584] ata4.00: configured for UDMA/33
[    1.462241] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552D HP06 PQ: 0 ANSI: 5
[    1.471445] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.471448] Uniform CD-ROM driver Revision: 3.20
[    1.471519] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.471561] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.471585] Freeing unused kernel memory: 660k freed
[    1.471965] Write protecting the kernel read-only data: 7580k
[    1.766835] [drm] Initialized drm 1.1.0 20060810
[    1.786598] [drm] radeon default to kernel modesetting DISABLED.
[    1.786737]   alloc irq_desc for 17 on node 0
[    1.786739]   alloc kstat_irqs on node 0
[    1.786748] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.786943] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    1.791344] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.791842] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.794628] 8139too Fast Ethernet driver 0.9.28
[    1.795075]   alloc irq_desc for 21 on node 0
[    1.795078]   alloc kstat_irqs on node 0
[    1.795086] 8139too 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.796697] eth0: RealTek RTL8139 at 0xde00, 00:17:31:04:f2:51, IRQ 21
[    2.558205] PM: Starting manual resume from disk
[    2.558210] PM: Resume from partition 8:5
[    2.558212] PM: Checking hibernation image.
[    2.558404] PM: Resume from disk failed.
[    2.598197] EXT4-fs (sda1): barriers enabled
[    2.624684] kjournald2 starting: pid 350, dev sda1:8, commit interval 5 seconds
[    2.624699] EXT4-fs (sda1): delayed allocation enabled
[    2.624702] EXT4-fs: file extents enabled
[    2.654851] EXT4-fs: mballoc enabled
[    2.654877] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.305554] type=1505 audit(1257365634.190:2): operation="profile_load" pid=373 name=/usr/share/gdm/guest-session/Xsession
[    3.434246] type=1505 audit(1257365634.320:3): operation="profile_load" pid=374 name=/sbin/dhclient3
[    3.434323] type=1505 audit(1257365634.320:4): operation="profile_load" pid=374 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.434380] type=1505 audit(1257365634.320:5): operation="profile_load" pid=374 name=/usr/lib/connman/scripts/dhclient-script
[    5.912048] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    5.912055] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.132044] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    6.132051] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.344958] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    6.344964] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.552046] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    6.552053] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.772043] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    6.772050] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.772053] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[    6.832047] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    6.832053] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.052046] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    7.052053] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.264959] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    7.264966] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.472048] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    7.472054] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.692043] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    7.692050] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.692052] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[    7.752046] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    7.752053] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.972047] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    7.972053] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.184962] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    8.184968] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.392045] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    8.392051] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.612045] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    8.612051] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.612053] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[    8.672050] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    8.672056] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.892044] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    8.892051] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.104961] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    9.104967] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.312051] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    9.312060] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.532047] ehci_hcd 0000:00:13.2: port 6 reset error -110
[    9.532054] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.532056] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[    9.532069] hub 1-0:1.0: unable to enumerate USB device on port 6
[    9.690040] usb 1-7: new high speed USB device using ehci_hcd and address 6
[    9.822050] ehci_hcd 0000:00:13.2: port 7 reset error -110
[    9.822057] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.032040] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   10.032048] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.252039] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   10.252045] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.464950] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   10.464957] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.672043] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   10.672050] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.672053] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[   10.742040] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   10.742047] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.952044] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   10.952051] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.172050] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   11.172057] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.384967] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   11.384973] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.592050] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   11.592058] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.592061] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[   11.662042] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   11.662050] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.872044] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   11.872051] hub 1-0:1.0: hub_port_status failed (err = -32)
[   12.092037] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   12.092044] hub 1-0:1.0: hub_port_status failed (err = -32)
[   12.304949] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   12.304955] hub 1-0:1.0: hub_port_status failed (err = -32)
[   12.512041] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   12.512049] hub 1-0:1.0: hub_port_status failed (err = -32)
[   12.512052] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[   12.582041] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   12.582048] hub 1-0:1.0: hub_port_status failed (err = -32)
[   12.792043] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   12.792050] hub 1-0:1.0: hub_port_status failed (err = -32)
[   12.951950] type=1505 audit(1257365643.840:6): operation="profile_load" pid=375 name=/usr/bin/evince
[   12.952754] type=1505 audit(1257365643.840:7): operation="profile_load" pid=375 name=/usr/bin/evince-previewer
[   12.953608] type=1505 audit(1257365643.840:8): operation="profile_load" pid=375 name=/usr/bin/evince-thumbnailer
[   13.012077] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   13.012084] hub 1-0:1.0: hub_port_status failed (err = -32)
[   13.216839] type=1505 audit(1257365644.100:9): operation="profile_load" pid=377 name=/usr/lib/cups/backend/cups-pdf
[   13.217002] type=1505 audit(1257365644.100:10): operation="profile_load" pid=377 name=/usr/sbin/cupsd
[   13.222713] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   13.222750] hub 1-0:1.0: hub_port_status failed (err = -32)
[   13.291896] type=1505 audit(1257365644.180:11): operation="profile_load" pid=378 name=/usr/sbin/tcpdump
[   13.432067] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   13.432103] hub 1-0:1.0: hub_port_status failed (err = -32)
[   13.432106] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[   13.432120] hub 1-0:1.0: unable to enumerate USB device on port 7
[   14.047359] Adding 1285160k swap on /dev/sda5.  Priority:-1 extents:1 across:1285160k 
[   14.507998] EXT4-fs (sda1): internal journal on sda1:8
[   15.237042] udev: starting version 147
[   17.005298] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   17.007466] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SM00 [0xb00-0xb07]
[   17.007472] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.007499] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[   17.182669] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.196236] lp: driver loaded but no devices found
[   17.260581] type=1505 audit(1257365648.150:12): operation="profile_replace" pid=665 name=/usr/share/gdm/guest-session/Xsession
[   17.333557] parport_pc 00:07: reported by Plug and Play ACPI
[   17.333602] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   17.405032] type=1505 audit(1257365648.290:13): operation="profile_replace" pid=672 name=/sbin/dhclient3
[   17.405212] type=1505 audit(1257365648.290:14): operation="profile_replace" pid=672 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.405295] type=1505 audit(1257365648.290:15): operation="profile_replace" pid=672 name=/usr/lib/connman/scripts/dhclient-script
[   17.426260] lp0: using parport0 (interrupt-driven).
[   17.428848] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[   17.428936] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   17.428939] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   17.428943] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   17.428944]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   17.428945]     Might be a BIOS bug, if BIOS says ECC is enabled
[   17.428947]     Use of the override can cause unknown side effects.
[   17.428975] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   17.601453] ppdev: user-space parallel port driver
[   18.160113] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   18.323814] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.944909] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   23.574506] usplash:313 freeing invalid memtype ffffffffd8000000-ffffffffdc000000
[   25.651081] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   28.482785] type=1505 audit(1257365659.370:16): operation="profile_replace" pid=676 name=/usr/bin/evince
[   28.484498] type=1505 audit(1257365659.370:17): operation="profile_replace" pid=676 name=/usr/bin/evince-previewer
[   28.485835] type=1505 audit(1257365659.370:18): operation="profile_replace" pid=676 name=/usr/bin/evince-thumbnailer
[   28.843734] type=1505 audit(1257365659.730:19): operation="profile_replace" pid=999 name=/usr/lib/cups/backend/cups-pdf
[   28.843995] type=1505 audit(1257365659.730:20): operation="profile_replace" pid=999 name=/usr/sbin/cupsd
[   28.931413] type=1505 audit(1257365659.820:21): operation="profile_replace" pid=1018 name=/usr/sbin/tcpdump
[   29.843496] [drm] Setting GART location based on new memory map
[   29.843791] [drm] Loading R300 Microcode
[   29.843809] [drm] Num pipes: 2
[   29.843815] [drm] writeback test succeeded in 1 usecs
[   31.322062] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   31.322070] hub 1-0:1.0: hub_port_status failed (err = -32)
[   31.324089] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   31.324092] hub 1-0:1.0: hub_port_status failed (err = -32)
[   36.600020] eth0: no IPv6 routers present
[   36.758735] ACPI Error: Illegal I/O port address/length above 64K: 0x0000000000400020/4 20090521 hwvalid-154
[   36.758745] ACPI Exception: AE_LIMIT, Returned by Handler for [SystemIO] 20090521 evregion-424
[   36.758752] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node ffff88001b8e0580), AE_LIMIT
[   36.758780] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] 20090521 evgpe-568
[   36.807863] ACPI Error: Illegal I/O port address/length above 64K: 0x0000000000400020/4 20090521 hwvalid-154
[   36.807873] ACPI Exception: AE_LIMIT, Returned by Handler for [SystemIO] 20090521 evregion-424
[   36.807879] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node ffff88001b8e0580), AE_LIMIT
[   36.807907] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] 20090521 evgpe-568
[   37.062069] ehci_hcd 0000:00:13.2: port 6 reset error -110
[   37.062081] hub 1-0:1.0: hub_port_status failed (err = -32)
[   37.064107] ehci_hcd 0000:00:13.2: port 7 reset error -110
[   37.064109] hub 1-0:1.0: hub_port_status failed (err = -32)
]
sorry for so long.
thx for reading ! :)

---

### Post by gpstar on 2009-11-04
sounds like the udev bug.

check the posts in the last few threads here

[http://ubuntuforums.org/showthread.php?t=1307542&page=3](http://ubuntuforums.org/showthread.php?t=1307542&page=3)

a update to udev in the karmic proposed repos fixes the hotswap/automount issue with esata/usb/card readers.

---

### Post by johenkel on 2009-11-05
Thanks for the reply, but it did not help.
I got the same error message in *dmesg* and when I do *lsusb* the device is not shown in the list. 
It does list the usb hubs though ? hm ?

Anybody got a good idea ?
johenkel

---

