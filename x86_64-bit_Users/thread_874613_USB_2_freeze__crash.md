---
title: "USB 2 freeze / crash"
date: 2008-07-30
forum: x86 64-bit Users
---

### Post by peckham2008 on 2008-07-30
Hello,
USB 1 works on my system. I have USB mouse, keyboard and HK Soundsticks all working. But USB 2 seems very patchy. Trying to use a USB 2 dvb-t tuner or external hard disk results in the USB 1 and 2 stopping. This is not always immediate but during a transfer and often enough to make USB 2 devices totally unusable. 
I've posted below some basic info on the system taken prior to plugging in any USB 2 devices. If anybody has any ideas on how to fix this it would be great. I can post the output of dmesg after a failure as well if that helps.

thanks for any advice
Ben

ben@kuroi:~$ uname -a
Linux kuroi 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux


ben@kuroi:~$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
02:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
ben@kuroi:~$

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 21:01:46 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] Command line: root=UUID=b6965e38-ecaf-483f-b18f-21c035258ac4 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001a8000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1736704) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1736704
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6980 checksum 0
[    0.000000] ACPI: RSDP 000F6980, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT CFEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP CFEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT CFEE30C0, 48EF (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: SSDT CFEE7A40, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET CFEE7C80, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG CFEE7CC0, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC CFEE79C0, 0068 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000001a8000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1736704) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-00000001a8000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1736704
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   851680
[    0.000000]     0:  1048576 ->  1736704
[    0.000000] On node 0 totalpages: 1539711
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1224 pages reserved
[    0.000000]   DMA zone: 2719 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[    0.000000]   Normal zone: 9408 pages used for memmap
[    0.000000]   Normal zone: 678720 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
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
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1514743
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=b6965e38-ecaf-483f-b18f-21c035258ac4 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   21.481066] Marking TSC unstable due to TSCs unsynchronized
[   21.481068] time.c: Detected 2104.784 MHz processor.
[   21.481740] Console: colour VGA+ 80x25
[   21.481743] console [tty0] enabled
[   21.481759] Checking aperture...
[   21.481762] CPU 0: aperture @ 9c20000000 size 32 MB
[   21.481763] Aperture too small (32 MB)
[   21.491265] No AGP bridge found
[   21.491266] Your BIOS doesn't leave a aperture memory hole
[   21.491268] Please enable the IOMMU option in the BIOS setup
[   21.491269] This costs you 64 MB of RAM
[   21.520699] Mapping aperture over 65536 KB of RAM @ 4000000
[   21.520704] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
[   21.585254] Memory: 5985108k/6946816k available (2489k kernel code, 173736k reserved, 1318k data, 320k init)
[   21.585284] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.663019] Calibrating delay using timer specific routine.. 4298.96 BogoMIPS (lpj=8597923)
[   21.663049] Security Framework initialized
[   21.663055] SELinux:  Disabled at boot.
[   21.663066] AppArmor: AppArmor initialized
[   21.663069] Failure registering capabilities with primary security module.
[   21.663696] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[   21.669578] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   21.672448] Mount-cache hash table entries: 256
[   21.672563] Initializing cgroup subsys ns
[   21.672566] Initializing cgroup subsys cpuacct
[   21.672577] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.672579] CPU: L2 Cache: 512K (64 bytes/line)
[   21.672581] CPU 0/0 -> Node 0
[   21.672583] CPU: Physical Processor ID: 0
[   21.672584] CPU: Processor Core ID: 0
[   21.672604] SMP alternatives: switching to UP code
[   21.673132] Early unpacking initramfs... done
[   21.993077] ACPI: Core revision 20070126
[   21.993128] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.047427] Using local APIC timer interrupts.
[   22.094894] APIC timer calibration result 12528472
[   22.094895] Detected 12.528 MHz APIC timer.
[   22.094985] SMP alternatives: switching to SMP code
[   22.095398] Booting processor 1/2 APIC 0x1
[   22.105925] Initializing CPU#1
[   22.183056] Calibrating delay using timer specific routine.. 4209.58 BogoMIPS (lpj=8419169)
[   22.183062] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.183064] CPU: L2 Cache: 512K (64 bytes/line)
[   22.183066] CPU 1/1 -> Node 0
[   22.183068] CPU: Physical Processor ID: 0
[   22.183069] CPU: Processor Core ID: 1
[   22.183163] AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 02
[   22.182964] Brought up 2 CPUs
[   22.183082] CPU0 attaching sched-domain:
[   22.183084]  domain 0: span 03
[   22.183086]   groups: 01 02
[   22.183088]   domain 1: span 03
[   22.183089]    groups: 03
[   22.183091] CPU1 attaching sched-domain:
[   22.183093]  domain 0: span 03
[   22.183094]   groups: 02 01
[   22.183096]   domain 1: span 03
[   22.183097]    groups: 03
[   22.183315] net_namespace: 120 bytes
[   22.183690] Time:  6:22:32  Date: 07/30/08
[   22.183721] NET: Registered protocol family 16
[   22.183904] ACPI: bus type pci registered
[   22.183977] PCI: Using configuration type 1
[   22.185142] ACPI: EC: Look up EC in DSDT
[   22.189972] ACPI: Interpreter enabled
[   22.189974] ACPI: (supports S0 S1 S4 S5)
[   22.189990] ACPI: Using IOAPIC for interrupt routing
[   22.194476] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.194645] pci 0000:00:12.0: set SATA to AHCI mode
[   22.195679] PCI: Transparent bridge - 0000:00:14.4
[   22.195703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.195969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   22.196108] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[   22.196194] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   22.214199] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214292] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214383] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214473] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214563] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214654] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214744] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214841] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   22.214957] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.214984] pnp: PnP ACPI init
[   22.214992] ACPI: bus type pnp registered
[   22.217800] pnp: PnP ACPI: found 13 devices
[   22.217802] ACPI: ACPI bus type pnp unregistered
[   22.218027] PCI: Using ACPI for IRQ routing
[   22.218030] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.226813] NET: Registered protocol family 8
[   22.226815] NET: Registered protocol family 20
[   22.226888] PCI-DMA: Disabling AGP.
[   22.227158] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   22.227162] PCI-DMA: using GART IOMMU.
[   22.227168] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   22.227349] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   22.227353] hpet0: 4 32-bit timers, 14318180 Hz
[   22.228408] AppArmor: AppArmor Filesystem Enabled
[   22.230761] Time: hpet clocksource has been installed.
[   22.230777] Switched to high resolution mode on CPU 0
[   22.231146] Switched to high resolution mode on CPU 1
[   22.238794] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   22.238796] system 00:01: ioport range 0x220-0x225 has been reserved
[   22.238799] system 00:01: ioport range 0x290-0x294 has been reserved
[   22.238805] system 00:02: ioport range 0x4100-0x411f has been reserved
[   22.238808] system 00:02: ioport range 0x228-0x22f has been reserved
[   22.238810] system 00:02: ioport range 0x40b-0x40b has been reserved
[   22.238812] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   22.238814] system 00:02: ioport range 0xc00-0xc01 has been reserved
[   22.238816] system 00:02: ioport range 0xc14-0xc14 has been reserved
[   22.238819] system 00:02: ioport range 0xc50-0xc52 has been reserved
[   22.238821] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[   22.238823] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[   22.238825] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[   22.238828] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[   22.238830] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[   22.238832] system 00:02: ioport range 0x4000-0x40fe has been reserved
[   22.238834] system 00:02: ioport range 0x4210-0x4217 has been reserved
[   22.238836] system 00:02: ioport range 0xb00-0xb1f could not be reserved
[   22.238839] system 00:02: ioport range 0x238-0x23f has been reserved
[   22.238850] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.238857] system 00:0c: iomem range 0xcd600-0xcffff has been reserved
[   22.238859] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   22.238861] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   22.238863] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   22.238866] system 00:0c: iomem range 0xcfee0000-0xcfefffff could not be reserved
[   22.238869] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[   22.238871] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   22.238873] system 00:0c: iomem range 0x100000-0xcfedffff could not be reserved
[   22.238876] system 00:0c: iomem range 0xcfff0000-0xd7feffff has been reserved
[   22.238878] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.238880] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.238883] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
[   22.239252] PCI: Bridge: 0000:00:01.0
[   22.239254]   IO window: d000-dfff
[   22.239256]   MEM window: fde00000-fdffffff
[   22.239258]   PREFETCH window: d8000000-dfffffff
[   22.239262] PCI: Bridge: 0000:00:04.0
[   22.239264]   IO window: e000-efff
[   22.239266]   MEM window: fdd00000-fddfffff
[   22.239268]   PREFETCH window: fdc00000-fdcfffff
[   22.239270] PCI: Bridge: 0000:00:14.4
[   22.239273]   IO window: c000-cfff
[   22.239277]   MEM window: fdb00000-fdbfffff
[   22.239281]   PREFETCH window: fda00000-fdafffff
[   22.239299] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   22.239315] NET: Registered protocol family 2
[   22.274897] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   22.276898] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   22.282454] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.283121] TCP: Hash tables configured (established 524288 bind 65536)
[   22.283125] TCP reno registered
[   22.294804] checking if image is initramfs... it is
[   22.903601] Freeing initrd memory: 7976k freed
[   22.908602] audit: initializing netlink socket (disabled)
[   22.908614] audit(1217398952.384:1): initialized
[   22.910598] VFS: Disk quotas dquot_6.5.1
[   22.910665] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   22.910784] io scheduler noop registered
[   22.910787] io scheduler anticipatory registered
[   22.910788] io scheduler deadline registered
[   22.910878] io scheduler cfq registered (default)
[   23.050323] Boot video device is 0000:01:05.0
[   23.050486] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   23.050503] assign_interrupt_mode Found MSI capability
[   23.050523] Allocate Port Service[0000:00:04.0:pcie00]
[   23.077532] Real Time Clock Driver v1.12ac
[   23.077679] hpet_resources: 0xfed00000 is busy
[   23.077704] Linux agpgart interface v0.102
[   23.077706] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.078209] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.078728] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.079386] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.079449] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.079577] PNP: No PS/2 controller found. Probing ports directly.
[   23.080181] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.080189] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.095117] mice: PS/2 mouse device common for all mice
[   23.095158] cpuidle: using governor ladder
[   23.095160] cpuidle: using governor menu
[   23.095288] NET: Registered protocol family 1
[   23.095386] registered taskstats version 1
[   23.095489]   Magic number: 0:717:368
[   23.095605] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.095608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.095609] EDD information not available.
[   23.095620] Freeing unused kernel memory: 320k freed
[   24.285833] fuse init (API version 7.9)
[   24.303503] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.303515] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.466760] SCSI subsystem initialized
[   24.488179] libata version 3.00 loaded.
[   24.489747] sata_sil24 0000:02:00.0: version 1.1
[   24.489777] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.490148] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   24.490417] scsi0 : sata_sil24
[   24.490470] scsi1 : sata_sil24
[   24.490493] ata1: SATA max UDMA/100 host m128@0xfddff000 port 0xfddf8000 irq 16
[   24.490496] ata2: SATA max UDMA/100 host m128@0xfddff000 port 0xfddfa000 irq 16
[   24.579824] usbcore: registered new interface driver usbfs
[   24.579846] usbcore: registered new interface driver hub
[   24.579870] usbcore: registered new device driver usb
[   24.580811] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.740977] Floppy drive(s): fd0 is 1.44M
[   24.760961] FDC 0 is a post-1991 82077
[   26.565956] ata1: SATA link down (SStatus 0 SControl 0)
[   28.647631] ata2: SATA link down (SStatus 0 SControl 0)
[   28.647929] ahci 0000:00:12.0: version 3.0
[   28.647965] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.648179] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   28.648184] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   29.647794] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   29.647799] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part
[   29.648078] scsi2 : ahci
[   29.648145] scsi3 : ahci
[   29.648184] scsi4 : ahci
[   29.648220] scsi5 : ahci
[   29.648293] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[   29.648296] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[   29.648300] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[   29.648303] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[   29.959418] ata3: SATA link down (SStatus 0 SControl 300)
[   30.270076] ata4: SATA link down (SStatus 0 SControl 300)
[   30.745552] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.747286] ata5.00: HPA unlocked: 312579695 -> 312581808, native 312581808
[   30.747291] ata5.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[   30.747293] ata5.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   30.748318] ata5.00: configured for UDMA/133
[   31.058196] ata6: SATA link down (SStatus 0 SControl 300)
[   31.058336] scsi 4:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   31.058435] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.058611] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   31.058836] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   31.058860] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[   31.065514] Driver 'sd' needs updating - please use bus_type methods
[   31.074217] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   31.074227] sd 4:0:0:0: [sda] Write Protect is off
[   31.074230] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.074243] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.074300] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   31.074308] sd 4:0:0:0: [sda] Write Protect is off
[   31.074311] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.074323] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.074327]  sda: sda1 sda2 < sda5 >
[   31.101552] sd 4:0:0:0: [sda] Attached SCSI disk
[   31.105053] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   31.121099] usb usb1: configuration #1 chosen from 1 choice
[   31.121122] hub 1-0:1.0: USB hub found
[   31.121132] hub 1-0:1.0: 2 ports detected
[   31.220867] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   31.221071] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   31.221128] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   31.221150] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[   31.280901] usb usb2: configuration #1 chosen from 1 choice
[   31.280925] hub 2-0:1.0: USB hub found
[   31.280935] hub 2-0:1.0: 2 ports detected
[   31.379409] Attempting manual resume
[   31.379412] swsusp: Resume From Partition 8:5
[   31.379414] PM: Checking swsusp image.
[   31.379553] PM: Resume from disk failed.
[   31.389053] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.389265] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   31.389321] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   31.389345] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[   31.416767] kjournald starting.  Commit interval 5 seconds
[   31.416778] EXT3-fs: mounted filesystem with ordered data mode.
[   31.449867] usb usb3: configuration #1 chosen from 1 choice
[   31.449890] hub 3-0:1.0: USB hub found
[   31.449900] hub 3-0:1.0: 2 ports detected
[   31.553722] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   31.553957] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   31.554009] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   31.554026] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[   31.612674] usb usb4: configuration #1 chosen from 1 choice
[   31.612695] hub 4-0:1.0: USB hub found
[   31.612704] hub 4-0:1.0: 2 ports detected
[   31.704228] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   31.713542] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   31.713719] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   31.713770] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   31.713788] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[   31.773507] usb usb5: configuration #1 chosen from 1 choice
[   31.773528] hub 5-0:1.0: USB hub found
[   31.773539] hub 5-0:1.0: 2 ports detected
[   31.877515] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   31.877717] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   31.877775] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   31.877820] ehci_hcd 0000:00:13.5: debug port 1
[   31.877840] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[   31.905244] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.905368] usb usb6: configuration #1 chosen from 1 choice
[   31.905391] hub 6-0:1.0: USB hub found
[   31.905399] hub 6-0:1.0: 10 ports detected
[   32.009351] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   32.009398] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   32.009540] r8169 Gigabit Ethernet driver 2.2LK loaded
[   32.009568] ACPI: PCI Interrupt 0000:03:0f.0[A] -> GSI 23 (level, low) -> IRQ 23
[   32.009798] eth0: RTL8169sc/8110sc at 0xffffc20001750000, 00:1d:7d:a8:86:97, XID 18000000 IRQ 23
[   32.300806] usb 2-2: device not accepting address 2, error -62
[   32.724335] usb 6-4: new high speed USB device using ehci_hcd and address 2
[   32.858036] usb 6-4: configuration #1 chosen from 1 choice
[   32.858346] hub 6-4:1.0: USB hub found
[   32.858701] hub 6-4:1.0: 4 ports detected
[   40.539757] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   40.539763] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   40.585932] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.611745] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.740135] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   40.887449] parport_pc 00:0a: reported by Plug and Play ACPI
[   40.887506] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.910138] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
[   40.910149] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   40.910160] SB600_PATA: not 100% native mode: will probe irqs later
[   40.910174]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:pio
[   40.910184] Probing IDE interface ide0...
[   40.992050] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   41.059832] input: Power Button (FF) as /devices/virtual/input/input2
[   41.087085] ACPI: Power Button (FF) [PWRF]
[   41.087162] input: Power Button (CM) as /devices/virtual/input/input3
[   41.115033] ACPI: Power Button (CM) [PWRB]
[   41.494103] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   41.524147] [fglrx]   vendor: 1002 device: 791e count: 1
[   41.524240] [fglrx] Maximum main memory to use for locked dma buffers: 5657 MBytes.
[   41.524633] [fglrx] PAT is enabled successfully!
[   41.524656] [fglrx] module loaded - fglrx 8.50.3 [Jun  2 2008] with 1 minors
[   41.760818] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   41.784137] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   41.816455] ACPI: PCI Interrupt 0000:01:05.2[B] -> GSI 19 (level, low) -> IRQ 19
[   44.806637] lp0: using parport0 (interrupt-driven).
[   44.901960] Adding 5662872k swap on /dev/sda5.  Priority:-1 extents:1 across:5662872k
[   45.454591] EXT3 FS on sda1, internal journal
[   45.583032] device-mapper: uevent: version 1.0.3
[   45.583070] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   46.930828] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.392666] No dock devices found.
[   47.695756] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual Core Processor BE-2350 processors (2 cpu cores) (version 2.20.00)
[   47.695595] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xe
[   47.695599] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xf
[   47.695601] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x11
[   47.695603] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x16
[   48.710650] NET: Registered protocol family 10
[   48.710853] lo: Disabled Privacy Extensions
[   49.280984] ppdev: user-space parallel port driver
[   49.459995] audit(1217398979.765:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5098 profile="/usr/sbin/cupsd" namespace="default"
[   53.671527] Clocksource tsc unstable (delta = -259824654 ns)
[   54.229579] r8169: eth0: link up
[   55.578344] Bluetooth: Core ver 2.11
[   55.578432] NET: Registered protocol family 31
[   55.578434] Bluetooth: HCI device and connection manager initialized
[   55.578437] Bluetooth: HCI socket layer initialized
[   55.594398] Bluetooth: L2CAP ver 2.9
[   55.594403] Bluetooth: L2CAP socket layer initialized
[   55.678409] Bluetooth: RFCOMM socket layer initialized
[   55.678427] Bluetooth: RFCOMM TTY layer initialized
[   55.678429] Bluetooth: RFCOMM ver 1.8
[   55.833728] NET: Registered protocol family 17
[   56.667186] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   57.041278] [fglrx] GART Table is not in FRAME_BUFFER range
[   57.042806] [fglrx] Maximum main memory to use for locked dma buffers: 5657 MBytes.
[   57.043799] [fglrx] Reserved FB block: Shared offset:0, size:1000000
[   57.043805] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000
[   57.239821] /dev/vmmon[5887]: Module vmmon: registered with major=10 minor=165
[   57.239833] /dev/vmmon[5887]: Initial HV check: anyNotCapable=0 anyUnlocked=1 anyEnabled=1 anyDisabled=0
[   57.239838] /dev/vmmon[5887]: HV check: anyNotCapable=0 anyUnlocked=1 anyEnabled=1 anyDisabled=0
[   57.239840] /dev/vmmon[5887]: Module vmmon: initialized
[   57.316364] /dev/vmci[5899]: VMCI: Driver initialized.
[   57.316582] /dev/vmci[5899]: Module vmci: registered with major=10 minor=62
[   57.316586] /dev/vmci[5899]: Module vmci: initialized
[   57.361027] vsock: no version for "VMCIDatagram_Send" found: kernel tainted.
[   57.399447] NET: Registered protocol family 33
[   57.811360] /dev/vmnet: open called by PID 5956 (vmnet-bridge)
[   57.811370] /dev/vmnet: hub 0 does not exist, allocating memory.
[   57.811380] /dev/vmnet: port on hub 0 successfully opened
[   57.811392] bridge-eth0: enabling the bridge
[   57.811395] bridge-eth0: up
[   57.811397] bridge-eth0: attached
[   57.870714] /dev/vmnet: open called by PID 5968 (vmnet-netifup)
[   57.870727] /dev/vmnet: hub 1 does not exist, allocating memory.
[   57.870738] /dev/vmnet: port on hub 1 successfully opened
[   57.966036] /dev/vmnet: open called by PID 5967 (vmnet-dhcpd)
[   57.966049] /dev/vmnet: port on hub 1 successfully opened
[   57.973245] /dev/vmnet: open called by PID 5993 (vmnet-netifup)
[   57.973367] /dev/vmnet: hub 8 does not exist, allocating memory.
[   57.973459] /dev/vmnet: port on hub 8 successfully opened
[   58.023173] /dev/vmnet: open called by PID 5997 (vmnet-dhcpd)
[   58.023189] /dev/vmnet: port on hub 8 successfully opened
[   58.053030] /dev/vmnet: open called by PID 6012 (vmnet-natd)
[   58.053043] /dev/vmnet: port on hub 8 successfully opened
[   61.683779] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445526674717748767 new 18445526674715611388 attempts 1
[   64.427459] vmnet1: no IPv6 routers present
[   64.582096] vmnet8: no IPv6 routers present
[   65.566908] hda-intel: Invalid position buffer, using LPIB read method instead.
[   68.718783] eth0: no IPv6 routers present
[  101.671166] usb 6-4.1: new full speed USB device using ehci_hcd and address 3
[  101.716445] usb 6-4.1: configuration #1 chosen from 1 choice
[  101.716784] hub 6-4.1:1.0: USB hub found
[  101.716984] hub 6-4.1:1.0: 3 ports detected
[  101.868776] usb 6-4.1.2: new low speed USB device using ehci_hcd and address 4
[  101.915677] usb 6-4.1.2: configuration #1 chosen from 1 choice
[  102.009844] usb 6-4.1.3: new full speed USB device using ehci_hcd and address 5
[  102.056962] usb 6-4.1.3: configuration #1 chosen from 1 choice
[  102.057370] usbcore: registered new interface driver hiddev
[  102.076466] input: Macally Peripherals  USB Optical Micromouse as /devices/pci0000:00/0000:00:13.5/usb6/6-4/6-4.1/6-4.1.2/6-4.1.2:1.0/input/input4
[  102.095107] input,hidraw0: USB HID v1.00 Mouse [Macally Peripherals  USB Optical Micromouse] on usb-0000:00:13.5-4.1.2
[  102.096802] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:13.5/usb6/6-4/6-4.1/6-4.1.3/6-4.1.3:1.0/input/input5
[  102.106532] input,hidraw1: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:13.5-4.1.3
[  102.108863] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:13.5/usb6/6-4/6-4.1/6-4.1.3/6-4.1.3:1.1/input/input6
[  102.133882] input,hidraw2: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:13.5-4.1.3
[  102.133900] usbcore: registered new interface driver usbhid
[  102.133904] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver


this shows in dmesg after the error. The freeze didn't happen till 90% finished copying a 3.6GB file from an external USB 2 drive to the internal drive. I tried turning of the AMD Cool&Quiet in the bios  but it didn't help.

[  488.633960] usb 6-6: reset high speed USB device using ehci_hcd and address 3
[  503.765001] usb 6-6: device descriptor read/64, error -110
[  518.999941] usb 6-6: device descriptor read/64, error -110
[  519.215693] usb 6-6: reset high speed USB device using ehci_hcd and address 3
[  534.346767] usb 6-6: device descriptor read/64, error -110
[  549.582747] usb 6-6: device descriptor read/64, error -110
[  549.798506] usb 6-6: reset high speed USB device using ehci_hcd and address 3
ben@kuroi:~$

---

### Post by jim-bob on 2009-05-05
Hey Ben!
Did you solved that USB-problem?
I think, I've got the same bug in my system.
:-(

Any hint would be appreciate.
Jim-Bob

---

### Post by Saxicide on 2009-06-27
I have a similar problem while trying to install--once I get past the boot-up menu (Try without an changes, Install, etc) all of my USB 2.0 devices shut down.  This means my keyboard, mouse, and wireless network adapter.  I don't even have any USB 1 ports.

---

