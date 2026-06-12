---
title: "Unusually long boot time"
date: 2008-09-16
forum: x86 64-bit Users
---

### Post by djshaw on 2008-09-16
Hey,

I am a Slacker; I just installed ubuntu for the first time --package management in slackware just isn't the greatest. 
(This might belong in the newbie support category...)

The machine takes a ridiculous amount of time to boot, almost 5 minutes. I have no idea why. 

I haven't setup wireless yet. I am going to hold off until I fix this boot issue.

Does any one know what might be going on?

dmesg:

> 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f72fc00 (usable)
[    0.000000]  BIOS-e820: 000000003f72fc00 - 000000003f730000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f730000 - 000000003f740000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f740000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed13000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000feda0000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 259887) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259887
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259887
[    0.000000] On node 0 totalpages: 259887
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 238 pages used for memmap
[    0.000000]   HighMem zone: 30273 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F4E50 checksum 0
[    0.000000] ACPI: RSDP 000F4E50, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3F730000, 003C (r1 INTEL  D915GAG  20040609 MSFT       97)
[    0.000000] ACPI: FACP 3F730200, 0081 (r2 INTEL  D915GAG  20040609 MSFT       97)
[    0.000000] ACPI: DSDT 3F730440, 5AC1 (r1 INTEL  D915GAG         1 INTL  2002026)
[    0.000000] ACPI: FACS 3F740000, 0040
[    0.000000] ACPI: APIC 3F730390, 0068 (r1 INTEL  D915GAG  20040609 MSFT       97)
[    0.000000] ACPI: MCFG 3F730400, 003C (r1 INTEL  D915GAG  20040609 MSFT       97)
[    0.000000] ACPI: ASF! 3F735F10, 0099 (r16 LEGEND I865PASF        1 INTL  2002026)
[    0.000000] ACPI: TCPA 3F735FB0, 0034 (r1 INTEL  TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: WDDT 3F735FE4, 0040 (r1 INTEL  OEMWDDT         1 INTL  2002026)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:a0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257857
[    0.000000] Kernel command line: root=UUID=9eff3a96-46ae-439d-8765-1c4126a8f128 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3000.134 MHz processor.
[   22.583071] Console: colour VGA+ 80x25
[   22.583075] console [tty0] enabled
[   22.583390] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.583739] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.608876] Memory: 1018016k/1039548k available (2177k kernel code, 20812k reserved, 1006k data, 368k init, 122044k highmem)
[   22.608885] virtual kernel memory layout:
[   22.608886]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.608887]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.608888]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.608889]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.608890]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.608891]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   22.608892]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   22.608895] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.608931] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.688881] Calibrating delay using timer specific routine.. 6005.98 BogoMIPS (lpj=12011966)
[   22.688906] Security Framework initialized
[   22.688913] SELinux:  Disabled at boot.
[   22.688926] AppArmor: AppArmor initialized
[   22.688930] Failure registering capabilities with primary security module.
[   22.688939] Mount-cache hash table entries: 512
[   22.689064] Initializing cgroup subsys ns
[   22.689070] Initializing cgroup subsys cpuacct
[   22.689082] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   22.689091] monitor/mwait feature present.
[   22.689093] using mwait in idle threads.
[   22.689099] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.689102] CPU: L2 cache: 1024K
[   22.689104] CPU: Physical Processor ID: 0
[   22.689106] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   22.689117] Compat vDSO mapped to ffffe000.
[   22.689134] Checking 'hlt' instruction... OK.
[   22.705319] SMP alternatives: switching to UP code
[   22.707155] Early unpacking initramfs... done
[   23.054380] ACPI: Core revision 20070126
[   23.057386] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.065505] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   23.065524] SMP alternatives: switching to SMP code
[   23.066309] Booting processor 1/1 eip 3000
[   23.076507] Initializing CPU#1
[   23.156445] Calibrating delay using timer specific routine.. 6000.43 BogoMIPS (lpj=12000876)
[   23.156455] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000 00000000
[   23.156463] monitor/mwait feature present.
[   23.156469] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.156472] CPU: L2 cache: 1024K
[   23.156475] CPU: Physical Processor ID: 0
[   23.156477] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   23.156854] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   23.156894] Total of 2 processors activated (12006.42 BogoMIPS).
[   23.157042] ENABLING IO-APIC IRQs
[   23.157216] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.304448] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.324445] Brought up 2 CPUs
[   23.324472] CPU0 attaching sched-domain:
[   23.324475]  domain 0: span 03
[   23.324478]   groups: 01 02
[   23.324483]   domain 1: span 03
[   23.324485]    groups: 03
[   23.324488] CPU1 attaching sched-domain:
[   23.324489]  domain 0: span 03
[   23.324491]   groups: 02 01
[   23.324494]   domain 1: span 03
[   23.324496]    groups: 03
[   23.324769] net_namespace: 64 bytes
[   23.324782] Booting paravirtualized kernel on bare hardware
[   23.325377] Time: 16:56:08  Date: 09/16/08
[   23.325403] NET: Registered protocol family 16
[   23.325668] EISA bus registered
[   23.325674] ACPI: bus type pci registered
[   23.327088] PCI: Using configuration type 1
[   23.327115] Setting up standard PCI resources
[   23.337885] ACPI: EC: Look up EC in DSDT
[   25.347027] ACPI: Interpreter enabled
[   25.347031] ACPI: (supports S0 S1 S4 S5)
[   25.347048] ACPI: Using IOAPIC for interrupt routing
[   25.355503] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.356241] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   25.356246] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   25.357012] PCI: Transparent bridge - 0000:00:1e.0
[   25.357054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.357215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   25.357324] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   25.357509] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   25.357615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   25.361066] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.361287] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.361506] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   25.361723] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   25.361939] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   25.362154] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.362373] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   25.362597] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   25.362787] ACPI: Power Resource [URP1] (off)
[   25.362833] ACPI: Power Resource [FDDP] (off)
[   25.362877] ACPI: Power Resource [LPTP] (off)
[   25.362923] ACPI: Power Resource [URP2] (off)
[   25.363070] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.363113] pnp: PnP ACPI init
[   25.363122] ACPI: bus type pnp registered
[   25.367922] pnp: PnP ACPI: found 14 devices
[   25.367925] ACPI: ACPI bus type pnp unregistered
[   25.367930] PnPBIOS: Disabled by ACPI PNP
[   25.368238] PCI: Using ACPI for IRQ routing
[   25.368242] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.382600] NET: Registered protocol family 8
[   25.382603] NET: Registered protocol family 20
[   25.382681] AppArmor: AppArmor Filesystem Enabled
[   25.386460] Time: tsc clocksource has been installed.
[   25.398664] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   25.398668] system 00:09: ioport range 0x400-0x47f has been reserved
[   25.398671] system 00:09: ioport range 0x500-0x53f has been reserved
[   25.398679] system 00:0b: iomem range 0xffc00000-0xfff7ffff has been reserved
[   25.398685] system 00:0c: ioport range 0x400-0x47f has been reserved
[   25.398688] system 00:0c: ioport range 0x680-0x6ff has been reserved
[   25.398690] system 00:0c: ioport range 0x500-0x53f has been reserved
[   25.398694] system 00:0c: iomem range 0xeec00000-0xeec03fff could not be reserved
[   25.398696] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   25.398699] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   25.398702] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   25.398705] system 00:0c: iomem range 0xfed13000-0xfed13fff could not be reserved
[   25.398708] system 00:0c: iomem range 0xfed14000-0xfed17fff could not be reserved
[   25.398710] system 00:0c: iomem range 0xfed18000-0xfed18fff could not be reserved
[   25.398713] system 00:0c: iomem range 0xfed19000-0xfed19fff could not be reserved
[   25.398716] system 00:0c: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   25.398719] system 00:0c: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   25.398725] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   25.398728] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[   25.398730] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   25.398733] system 00:0d: iomem range 0x100000-0x3f7fffff could not be reserved
[   25.398736] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   25.429259] PCI: Bridge: 0000:00:01.0
[   25.429261]   IO window: disabled.
[   25.429266]   MEM window: ff200000-ff2fffff
[   25.429269]   PREFETCH window: bf900000-bf9fffff
[   25.429273] PCI: Bridge: 0000:00:1c.0
[   25.429274]   IO window: disabled.
[   25.429279]   MEM window: ff600000-ff6fffff
[   25.429283]   PREFETCH window: bfd00000-bfdfffff
[   25.429288] PCI: Bridge: 0000:00:1c.1
[   25.429289]   IO window: disabled.
[   25.429294]   MEM window: ff500000-ff5fffff
[   25.429298]   PREFETCH window: bfc00000-bfcfffff
[   25.429303] PCI: Bridge: 0000:00:1c.2
[   25.429304]   IO window: disabled.
[   25.429309]   MEM window: ff400000-ff4fffff
[   25.429313]   PREFETCH window: bfb00000-bfbfffff
[   25.429317] PCI: Bridge: 0000:00:1c.3
[   25.429319]   IO window: disabled.
[   25.429324]   MEM window: ff300000-ff3fffff
[   25.429327]   PREFETCH window: bfa00000-bfafffff
[   25.429333] PCI: Bridge: 0000:00:1e.0
[   25.429335]   IO window: b000-bfff
[   25.429340]   MEM window: ff700000-ff7fffff
[   25.429344]   PREFETCH window: bfe00000-bfefffff
[   25.429364] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.429370] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.429390] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   25.429395] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.429413] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   25.429419] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   25.429438] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   25.429443] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   25.429462] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   25.429467] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   25.429478] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.429490] NET: Registered protocol family 2
[   25.466697] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.466990] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.467589] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.467889] TCP: Hash tables configured (established 131072 bind 65536)
[   25.467893] TCP reno registered
[   25.478822] checking if image is initramfs... it is
[   25.930088] Switched to high resolution mode on CPU 0
[   25.930217] Switched to high resolution mode on CPU 1
[   26.124262] Freeing initrd memory: 7706k freed
[   26.125175] audit: initializing netlink socket (disabled)
[   26.125187] audit(1221584170.392:1): initialized
[   26.125392] highmem bounce pool size: 64 pages
[   26.127809] VFS: Disk quotas dquot_6.5.1
[   26.127904] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.128051] io scheduler noop registered
[   26.128053] io scheduler anticipatory registered
[   26.128055] io scheduler deadline registered
[   26.128067] io scheduler cfq registered (default)
[   26.128081] Boot video device is 0000:00:02.0
[   26.128164] PCI: Firmware left 0000:06:08.0 e100 interrupts enabled, disabling
[   26.128296] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.128337] assign_interrupt_mode Found MSI capability
[   26.128371] Allocate Port Service[0000:00:01.0:pcie00]
[   26.128465] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.128509] assign_interrupt_mode Found MSI capability
[   26.128544] Allocate Port Service[0000:00:1c.0:pcie00]
[   26.128591] Allocate Port Service[0000:00:1c.0:pcie02]
[   26.128687] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   26.128730] assign_interrupt_mode Found MSI capability
[   26.128766] Allocate Port Service[0000:00:1c.1:pcie00]
[   26.128812] Allocate Port Service[0000:00:1c.1:pcie02]
[   26.128913] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   26.128956] assign_interrupt_mode Found MSI capability
[   26.128993] Allocate Port Service[0000:00:1c.2:pcie00]
[   26.129038] Allocate Port Service[0000:00:1c.2:pcie02]
[   26.129136] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   26.129179] assign_interrupt_mode Found MSI capability
[   26.129215] Allocate Port Service[0000:00:1c.3:pcie00]
[   26.129260] Allocate Port Service[0000:00:1c.3:pcie02]
[   26.129573] isapnp: Scanning for PnP cards...
[   26.480927] isapnp: No Plug & Play device found
[   26.518133] Real Time Clock Driver v1.12ac
[   26.518264] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.518398] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.519242] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.520262] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.520344] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.520479] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   26.523385] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.523393] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.545303] mice: PS/2 mouse device common for all mice
[   26.545463] EISA: Probing bus 0 at eisa.0
[   26.545493] EISA: Detected 0 cards.
[   26.545496] cpuidle: using governor ladder
[   26.545498] cpuidle: using governor menu
[   26.545579] NET: Registered protocol family 1
[   26.545609] Using IPI No-Shortcut mode
[   26.545636] registered taskstats version 1
[   26.545737]   Magic number: 8:807:944
[   26.545787]   hash matches device ptyyf
[   26.545819]   hash matches device tty1
[   26.545840] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.545842] EDD information not available.
[   26.546040] Freeing unused kernel memory: 368k freed
[   26.568600] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   46.573429] fuse init (API version 7.9)
[   47.959100] ACPI: Processor [CPU1] (supports 8 throttling states)
[   47.980979] ACPI: Processor [CPU2] (supports 8 throttling states)
[   63.801606] SCSI subsystem initialized
[   64.303831] libata version 3.00 loaded.
[   64.404823] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   64.404864] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   64.404879] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   64.404911] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   64.404937] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   64.404949] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   65.695531] ata_piix 0000:00:1f.1: version 2.12
[   65.695551] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   65.695592] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   65.763378] scsi0 : ata_piix
[   65.867279] scsi1 : ata_piix
[   65.868661] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   65.868665] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   66.187306] ata1.00: ATAPI: HL-DT-STDVD-ROM GDR8163B, 0L23, max UDMA/33
[   66.359072] ata1.00: configured for UDMA/33
[   66.533718] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8163B 0L23 PQ: 0 ANSI: 5
[   66.533816] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   66.533842] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   66.533882] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   66.630522] scsi2 : ata_piix
[   66.726426] scsi3 : ata_piix
[   66.727929] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 19
[   66.727933] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 19
[   66.891707] ata3.00: ATA-6: WDC WD1600JD-00HBB0, 08.02D08, max UDMA/133
[   66.891712] ata3.00: 312581808 sectors, multi 16: LBA48 
[   66.907700] ata3.00: configured for UDMA/133
[   67.073009] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600JD-00H 08.0 PQ: 0 ANSI: 5
[   80.960409] usbcore: registered new interface driver usbfs
[   80.960445] usbcore: registered new interface driver hub
[   80.971360] usbcore: registered new device driver usb
[   81.003338] USB Universal Host Controller Interface driver v3.0
[   81.003413] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   81.003427] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   81.003432] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   81.003780] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   81.003814] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000c800
[   81.003992] usb usb1: configuration #1 chosen from 1 choice
[   81.004027] hub 1-0:1.0: USB hub found
[   81.004035] hub 1-0:1.0: 2 ports detected
[   81.107300] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   81.107314] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   81.107320] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   81.107352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   81.107380] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000cc00
[   81.107532] usb usb2: configuration #1 chosen from 1 choice
[   81.107565] hub 2-0:1.0: USB hub found
[   81.107572] hub 2-0:1.0: 2 ports detected
[   81.211209] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   81.211225] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   81.211230] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   81.211264] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   81.211296] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
[   81.211450] usb usb3: configuration #1 chosen from 1 choice
[   81.211485] hub 3-0:1.0: USB hub found
[   81.211493] hub 3-0:1.0: 2 ports detected
[   81.315107] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   81.315122] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   81.315128] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   81.315164] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   81.315197] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[   81.315361] usb usb4: configuration #1 chosen from 1 choice
[   81.315405] hub 4-0:1.0: USB hub found
[   81.315414] hub 4-0:1.0: 2 ports detected
[   81.419418] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   81.419437] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   81.419443] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   81.419477] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   81.423413] ehci_hcd 0000:00:1d.7: debug port 1
[   81.423423] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   81.423436] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa3bc00
[   81.438859] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   81.439008] usb usb5: configuration #1 chosen from 1 choice
[   81.439048] hub 5-0:1.0: USB hub found
[   81.439057] hub 5-0:1.0: 8 ports detected
[   86.561900] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[   86.585783] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   86.585794] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   86.585802] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   86.585810] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   86.641756] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[   97.231275] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   97.231280] e100: Copyright(c) 1999-2006 Intel Corporation
[   97.231353] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 22
[   97.588205] e100: eth0: e100_probe: addr 0xff7fd000, irq 22, MAC addr 00:11:11:b2:31:52
[  111.720928] Driver 'sr' needs updating - please use bus_type methods
[  111.767550] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[  111.767556] Uniform CD-ROM driver Revision: 3.20
[  111.767623] sr 0:0:0:0: Attached scsi CD-ROM sr0
[  112.053621] Driver 'sd' needs updating - please use bus_type methods
[  112.053738] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  112.053799] sd 2:0:0:0: [sda] Write Protect is off
[  112.053803] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  112.053831] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  112.053909] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  112.053927] sd 2:0:0:0: [sda] Write Protect is off
[  112.053930] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  112.053961] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  112.053966]  sda: sda1 sda2 < sda5 >
[  112.108629] sd 2:0:0:0: [sda] Attached SCSI disk
[  112.908828] sr 0:0:0:0: Attached scsi generic sg0 type 5
[  112.908862] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  118.456697] Attempting manual resume
[  118.456701] swsusp: Resume From Partition 8:5
[  118.456703] PM: Checking swsusp image.
[  118.456859] PM: Resume from disk failed.
[  118.725503] kjournald starting.  Commit interval 5 seconds
[  118.725511] EXT3-fs: mounted filesystem with ordered data mode.
[  153.847225] Linux agpgart interface v0.102
[  153.983334] agpgart: Detected an Intel 915G Chipset.
[  153.984040] agpgart: Detected 7932K stolen memory.
[  154.017174] agpgart: AGP aperture is 256M @ 0xd0000000
[  154.834262] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  154.930406] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  162.889131] intel_rng: FWH not detected
[  164.182521] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  171.011676] iTCO_vendor_support: vendor-support=0
[  171.190513] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  171.191001] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[  171.191328] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  185.795625] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[  189.050352] parport_pc 00:08: reported by Plug and Play ACPI
[  189.050386] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  206.293299] input: Power Button (FF) as /devices/virtual/input/input4
[  206.303256] ACPI: Power Button (FF) [PWRF]
[  206.303600] input: Power Button (CM) as /devices/virtual/input/input5
[  206.339215] ACPI: Power Button (CM) [PWRB]
[  223.651430] b43-phy0: Broadcom 4318 WLAN found
[  223.694040] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[  223.694064] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[  223.739097] phy0: Selected rate control algorithm 'simple'
[  270.945364] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[  270.945401] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  275.832331] lp0: using parport0 (interrupt-driven).
[  276.489589] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[  277.611540] EXT3 FS on sda1, internal journal
[  281.523375] ip_tables: (C) 2000-2006 Netfilter Core Team
[  289.921788] No dock devices found.
[  290.388998] ACPI: \_SB_.PCI0.IDE1.CHN1.DRV0: found ejectable bay
[  290.389008] ACPI: \_SB_.PCI0.IDE1.CHN1.DRV0: Adding notify handler
[  290.389065] ACPI: Error installing bay notify handler
[  290.389070] ACPI: Bay [\_SB_.PCI0.IDE1.CHN1.DRV0] Added
[  304.949849] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  304.949856] apm: disabled - APM is not SMP safe.
[  305.616284] ppdev: user-space parallel port driver
[  305.824966] audit(1221584451.004:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5797 profile="/usr/sbin/cupsd" namespace="default"
[  309.976213] input: b43-phy0 as /devices/virtual/input/input6
[  310.171208] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  310.171314] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  310.208687] Bluetooth: Core ver 2.11
[  310.210015] NET: Registered protocol family 31
[  310.210021] Bluetooth: HCI device and connection manager initialized
[  310.210026] Bluetooth: HCI socket layer initialized
[  310.396358] Bluetooth: L2CAP ver 2.9
[  310.396365] Bluetooth: L2CAP socket layer initialized
[  310.485129] Bluetooth: RFCOMM socket layer initialized
[  310.485148] Bluetooth: RFCOMM TTY layer initialized
[  310.485151] Bluetooth: RFCOMM ver 1.8
[  313.002894] input: b43-phy0 as /devices/virtual/input/input7
[  313.118851] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  313.118862] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  327.424225] [drm] Initialized drm 1.1.0 20060810
[  327.436790] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  327.436803] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  327.438716] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  330.289833] input: b43-phy0 as /devices/virtual/input/input8
[  330.385250] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  330.385260] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  347.473242] input: b43-phy0 as /devices/virtual/input/input9
[  347.588317] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  347.588327] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  347.952962] NET: Registered protocol family 10
[  347.953328] lo: Disabled Privacy Extensions
[  347.954269] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  364.915021] input: b43-phy0 as /devices/virtual/input/input10
[  365.020723] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  365.020734] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  382.123153] input: b43-phy0 as /devices/virtual/input/input11
[  382.209159] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  382.209172] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  399.277664] input: b43-phy0 as /devices/virtual/input/input12
[  399.366902] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  399.366914] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  416.436760] input: b43-phy0 as /devices/virtual/input/input13
[  416.526092] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  416.526104] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  433.598690] input: b43-phy0 as /devices/virtual/input/input14
[  433.724705] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  433.724716] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).


---

### Post by mrsteveman1 on 2008-09-16
The only error i see is the firmware message about the broadcom driver.

Boot the thing and edit the grub options to remove the "splash" and "silent" options, so you can see where it is stopped.

---

