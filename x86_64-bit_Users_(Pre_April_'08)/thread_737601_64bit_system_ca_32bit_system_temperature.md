---
title: "64bit system c/a 32bit system temperature"
date: 2008-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by m.hricko on 2008-03-27
Hello,

I have a HP 6715s laptop with Turion X2 TL-58 CPU[http://geizhals.at/eu/a264276.html]("http://geizhals.at/eu/a264276.html") . I have tried a lot of distros and I mentioned one thing. If I run a 64bit distro, the system is heating much more faster than witch 32bit distro, so the fan is turning on more often. It is the same with ubuntu, mandriva, simply-mepis and other 64bit ports and with kernels 2.6.18, 20, 22, 24. Now I am running 32bit gutsy and 64bit hardy beta. I cannot compare it with windows, because i have only a 32bit wxp.

I have been looking for solution through internet a lot of time, but i have not found anything. I have also tried powertop and its suggestions, but i have not found solution.

Can anybody help me please? Thanx a lot.

milo

ps: in attachemet is my lspci and dmesg output

dmesg

[    0.000000] Linux version 2.6.24-12-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu4)) #1 SMP Wed Mar 12 22:31:43 UTC 2008 (Ubuntu 2.6.24-12.22-generic)
[    0.000000] Command line: root=/dev/sda3 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037fb0000 (usable)
[    0.000000]  BIOS-e820: 0000000037fb0000 - 0000000037fc8000 (reserved)
[    0.000000]  BIOS-e820: 0000000037fc8000 - 0000000037fe7fb8 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037fe7fb8 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffbc0000 - 00000000ffcc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 229296) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FE0B0 checksum 0
[    0.000000] ACPI: RSDP 000FE0B0, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 37FC81BC, 0064 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: FACP 37FC8084, 00F4 (r4 HP     0944            3 HP          1)
[    0.000000] ACPI Error (tbfadt-0453): 32/64X address mismatch in "Pm2ControlBlock": [00008800] [0000000000008100], using 64X [20070126]
[    0.000000] ACPI: DSDT 37FC84A4, 11437 (r1 HP        SB400    10000 MSFT  3000001)
[    0.000000] ACPI: FACS 37FE7D80, 0040
[    0.000000] ACPI: SLIC 37FC8220, 0176 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: EPTH 37FC8398, 0038 (r1 HP     0944            1 HP          1)
[    0.000000] ACPI: APIC 37FC83D0, 0062 (r1 HP     0944            1 HP          1)
[    0.000000] ACPI: MCFG 37FC8434, 003C (r1 HP     0944            1 HP          1)
[    0.000000] ACPI: TCPA 37FC8470, 0032 (r2 HP     0944            1 HP          1)
[    0.000000] ACPI: SSDT 37FD98DB, 0059 (r1 HP       HPQNLP        1 MSFT  3000001)
[    0.000000] ACPI: SSDT 37FD9934, 0206 (r1 HP     PSSTBLID        1 HP          1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000037fb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 229296) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037fb0000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   229296
[    0.000000] On node 0 totalpages: 229199
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1207 pages reserved
[    0.000000]   DMA zone: 2736 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3078 pages used for memmap
[    0.000000]   DMA32 zone: 222122 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 224858
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/sda3 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC calibrated against PM_TIMER
[   14.566158] Marking TSC unstable due to TSCs unsynchronized
[   14.566178] time.c: Detected 1895.258 MHz processor.
[   14.567607] Console: colour VGA+ 80x25
[   14.567610] console [tty0] enabled
[   14.567646] Checking aperture...
[   14.567648] CPU 0: aperture @ d060000000 size 32 MB
[   14.567650] Aperture too small (32 MB)
[   14.587604] No AGP bridge found
[   14.611379] Memory: 891708k/917184k available (2466k kernel code, 25088k reserved, 1310k data, 316k init)
[   14.611453] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.688069] Calibrating delay using timer specific routine.. 3800.97 BogoMIPS (lpj=7601943)
[   14.688141] Security Framework initialized
[   14.688166] SELinux:  Disabled at boot.
[   14.688199] AppArmor: AppArmor initialized
[   14.688203] Failure registering capabilities with primary security module.
[   14.688405] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.690138] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.690934] Mount-cache hash table entries: 256
[   14.691260] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.691263] CPU: L2 Cache: 512K (64 bytes/line)
[   14.691266] CPU 0/0 -> Node 0
[   14.691268] CPU: Physical Processor ID: 0
[   14.691269] CPU: Processor Core ID: 0
[   14.691332] SMP alternatives: switching to UP code
[   14.692901] Early unpacking initramfs... done
[   15.385481] ACPI: Core revision 20070126
[   15.385737] ACPI: Looking for DSDT in initramfs... successfully read 66905 bytes from /DSDT.aml.
[   15.385882] ACPI: Table DSDT replaced by host OS
[   15.385902] ACPI: DSDT 00000000, 10559 (r1 HP        SB400    10000 INTL 20061109)
[   15.385907] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"<3>..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   15.556358] Disabling APIC timer
[   15.556471] SMP alternatives: switching to SMP code
[   15.556949] Booting processor 1/2 APIC 0x1
[   15.567228] Initializing CPU#1
[   15.644503] Calibrating delay using timer specific routine.. 3790.78 BogoMIPS (lpj=7581566)
[   15.644509] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.644511] CPU: L2 Cache: 512K (64 bytes/line)
[   15.644514] CPU 1/1 -> Node 0
[   15.644516] CPU: Physical Processor ID: 0
[   15.644517] CPU: Processor Core ID: 1
[   15.644625] AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[   15.644485] Brought up 2 CPUs
[   15.644566] CPU0 attaching sched-domain:
[   15.644569]  domain 0: span 03
[   15.644571]   groups: 01 02
[   15.644574]   domain 1: span 03
[   15.644576]    groups: 03
[   15.644578] CPU1 attaching sched-domain:
[   15.644580]  domain 0: span 03
[   15.644581]   groups: 02 01
[   15.644584]   domain 1: span 03
[   15.644586]    groups: 03
[   15.644833] net_namespace: 120 bytes
[   15.645272] Time: 23:42:29  Date: 03/27/08
[   15.645331] NET: Registered protocol family 16
[   15.645538] ACPI: bus type pci registered
[   15.645617] PCI: Using configuration type 1
[   15.647253] ACPI: EC: Look up EC in DSDT
[   15.648107] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.878846] ACPI: Interpreter enabled
[   15.878850] ACPI: (supports S0 S3 S4 S5)
[   15.878861] ACPI: Using IOAPIC for interrupt routing
[   15.887474] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[   15.887478] ACPI: EC: driver started in interrupt mode
[   15.887541] ACPI: PCI Root Bridge [C08B] (0000:00)
[   15.887758] pci 0000:00:12.0: set SATA to AHCI mode
[   15.888925] PCI: Transparent bridge - 0000:00:14.4
[   15.888998] ACPI: PCI Interrupt Routing Table [\_SB_.C08B._PRT]
[   15.889338] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C08C._PRT]
[   15.889467] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C0FC._PRT]
[   15.911697] ACPI: PCI Interrupt Link [C145] (IRQs 10 11) *0, disabled.
[   15.911875] ACPI: PCI Interrupt Link [C146] (IRQs 10 11) *0, disabled.
[   15.912050] ACPI: PCI Interrupt Link [C147] (IRQs 10 11) *0, disabled.
[   15.912225] ACPI: PCI Interrupt Link [C148] (IRQs 10 11) *0, disabled.
[   15.912402] ACPI: PCI Interrupt Link [C149] (IRQs 10 11) *0, disabled.
[   15.912575] ACPI: PCI Interrupt Link [C14A] (IRQs 9) *0, disabled.
[   15.912750] ACPI: PCI Interrupt Link [C14B] (IRQs 10 11) *0, disabled.
[   15.912925] ACPI: PCI Interrupt Link [C14C] (IRQs 10 11) *0, disabled.
[   15.913079] ACPI: Power Resource [C171] (off)
[   15.913134] ACPI: Power Resource [C24C] (on)
[   15.913256] ACPI: Power Resource [C395] (off)
[   15.913358] ACPI: Power Resource [C396] (off)
[   15.913459] ACPI: Power Resource [C397] (off)
[   15.913562] ACPI: Power Resource [C398] (off)
[   15.913615] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.913647] pnp: PnP ACPI init
[   15.913654] ACPI: bus type pnp registered
[   15.921035] pnp: PnP ACPI: found 11 devices
[   15.921038] ACPI: ACPI bus type pnp unregistered
[   15.921300] PCI: Using ACPI for IRQ routing
[   15.921302] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.921335] PCI: Cannot allocate resource region 0 of device 0000:00:14.2
[   15.936367] NET: Registered protocol family 8
[   15.936369] NET: Registered protocol family 20
[   15.936510] AppArmor: AppArmor Filesystem Enabled
[   15.952390] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   15.952393] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   15.952396] system 00:00: iomem range 0x100000-0xffffffff could not be reserved
[   15.952407] system 00:08: ioport range 0x40b-0x40b has been reserved
[   15.952410] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   15.952413] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   15.952416] system 00:08: ioport range 0x500-0x53f has been reserved
[   15.952419] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   15.952422] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   15.952424] system 00:08: ioport range 0xc50-0xc51 has been reserved
[   15.952427] system 00:08: ioport range 0xc52-0xc52 has been reserved
[   15.952430] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   15.952433] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   15.952436] system 00:08: ioport range 0xcd0-0xcdf has been reserved
[   15.952440] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   15.952443] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   15.952448] system 00:09: ioport range 0x8000-0x802f has been reserved
[   15.952451] system 00:09: ioport range 0x8100-0x811f has been reserved
[   15.952455] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[   15.952458] system 00:09: iomem range 0xfec00000-0xfec000ff could not be reserved
[   15.952461] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[   15.952467] system 00:0a: iomem range 0xcd400-0xcffff has been reserved
[   15.952470] system 00:0a: iomem range 0x0-0x7ffffff could not be reserved
[   15.952473] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.952914] PCI: Bridge: 0000:00:01.0
[   15.952916]   IO window: 4000-4fff
[   15.952919]   MEM window: d0200000-d03fffff
[   15.952921]   PREFETCH window: c0000000-c7ffffff
[   15.952924] PCI: Bridge: 0000:00:04.0
[   15.952925]   IO window: disabled.
[   15.952927]   MEM window: d0000000-d00fffff
[   15.952929]   PREFETCH window: disabled.
[   15.952931] PCI: Bridge: 0000:00:05.0
[   15.952933]   IO window: 2000-3fff
[   15.952935]   MEM window: cc000000-cfffffff
[   15.952937]   PREFETCH window: disabled.
[   15.952939] PCI: Bridge: 0000:00:06.0
[   15.952940]   IO window: disabled.
[   15.952943]   MEM window: c8000000-c80fffff
[   15.952945]   PREFETCH window: disabled.
[   15.952950] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   15.952952]   IO window: 00001000-000010ff
[   15.952961]   IO window: 00001400-000014ff
[   15.952965]   PREFETCH window: 54000000-57ffffff
[   15.952970]   MEM window: 58000000-5bffffff
[   15.952974] PCI: Bridge: 0000:00:14.4
[   15.952975]   IO window: disabled.
[   15.952980]   MEM window: d0100000-d01fffff
[   15.952983]   PREFETCH window: disabled.
[   15.953001] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.953008] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.953014] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   15.953038] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 20
[   15.953098] NET: Registered protocol family 2
[   15.956193] Time: acpi_pm clocksource has been installed.
[   15.956198] Clockevents: could not switch to one-shot mode:<6>Clockevents: could not switch to one-shot mode: lapic is not functional.
[   15.956363] Could not switch to high resolution mode on CPU 1
[   15.956206]  lapic is not functional.
[   15.956208] Could not switch to high resolution mode on CPU 0
[   16.000436] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   16.000964] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   16.002574] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.003323] TCP: Hash tables configured (established 131072 bind 65536)
[   16.003327] TCP reno registered
[   16.016486] checking if image is initramfs... it is
[   16.455949] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   16.456108] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   16.456115] Could not switch to high resolution mode on CPU 1
[   16.455963] Could not switch to high resolution mode on CPU 0
[   16.649402] Freeing initrd memory: 7539k freed
[   16.655743] audit: initializing netlink socket (disabled)
[   16.655755] audit(1206661349.976:1): initialized
[   16.657872] VFS: Disk quotas dquot_6.5.1
[   16.657952] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.658093] io scheduler noop registered
[   16.658095] io scheduler anticipatory registered
[   16.658097] io scheduler deadline registered
[   16.658205] io scheduler cfq registered (default)
[   16.660372] Boot video device is 0000:01:05.0
[   16.660573] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.660593] assign_interrupt_mode Found MSI capability
[   16.660615] Allocate Port Service[0000:00:04.0:pcie00]
[   16.660682] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.660700] assign_interrupt_mode Found MSI capability
[   16.660717] Allocate Port Service[0000:00:05.0:pcie00]
[   16.660778] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.660796] assign_interrupt_mode Found MSI capability
[   16.660813] Allocate Port Service[0000:00:06.0:pcie00]
[   16.690681] Real Time Clock Driver v1.12ac
[   16.690805] Linux agpgart interface v0.102
[   16.690808] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.691935] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.692008] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.692109] PNP: PS/2 Controller [PNP0303:C249,PNP0f13:C24A] at 0x60,0x64 irq 1,12
[   16.693972] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.694750] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.694754] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.694757] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.694759] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.694761] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.708144] mice: PS/2 mouse device common for all mice
[   16.708189] cpuidle: using governor ladder
[   16.708191] cpuidle: using governor menu
[   16.708358] NET: Registered protocol family 1
[   16.708421] registered taskstats version 1
[   16.708559]   Magic number: 0:137:758
[   16.708727] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.708730] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.708732] EDD information not available.
[   16.708740] Freeing unused kernel memory: 316k freed
[   16.730913] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.927717] fuse init (API version 7.9)
[   17.942337] ACPI: Transitioning device [C399] to D3
[   17.942342] ACPI: Transitioning device [C399] to D3
[   17.942345] ACPI: Fan [C399] (off)
[   17.942541] ACPI: Transitioning device [C39A] to D3
[   17.942543] ACPI: Transitioning device [C39A] to D3
[   17.942546] ACPI: Fan [C39A] (off)
[   17.942738] ACPI: Transitioning device [C39B] to D3
[   17.942740] ACPI: Transitioning device [C39B] to D3
[   17.942750] ACPI: Fan [C39B] (off)
[   17.942944] ACPI: Transitioning device [C39C] to D3
[   17.942946] ACPI: Transitioning device [C39C] to D3
[   17.942948] ACPI: Fan [C39C] (off)
[   17.958631] ACPI: Thermal Zone [TZ1] (45 C)
[   18.119606] tg3.c:v3.86 (November 9, 2007)
[   18.119674] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.119685] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   18.363448] SCSI subsystem initialized
[   18.409400] usbcore: registered new interface driver usbfs
[   18.409429] usbcore: registered new interface driver hub
[   18.410212] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.410223] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.412240] usbcore: registered new device driver usb
[   18.431302] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.452670] libata version 3.00 loaded.
[   18.647990] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1a:4b:58:9e:50
[   18.647999] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[   18.648001] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   18.648352] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 23 (level, low) -> IRQ 23
[   18.648607] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   18.648908] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   18.648937] ohci_hcd 0000:00:13.0: irq 23, io mem 0xd0401000
[   18.707169] usb usb1: configuration #1 chosen from 1 choice
[   18.707196] hub 1-0:1.0: USB hub found
[   18.707209] hub 1-0:1.0: 2 ports detected
[   18.811136] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   18.811395] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   18.811469] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   18.811496] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0402000
[   18.871139] usb usb2: configuration #1 chosen from 1 choice
[   18.871165] hub 2-0:1.0: USB hub found
[   18.871179] hub 2-0:1.0: 2 ports detected
[   18.975049] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 17 (level, low) -> IRQ 17
[   18.975289] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   18.975356] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   18.975378] ohci_hcd 0000:00:13.2: irq 17, io mem 0xd0403000
[   19.034995] usb usb3: configuration #1 chosen from 1 choice
[   19.035023] hub 3-0:1.0: USB hub found
[   19.035036] hub 3-0:1.0: 2 ports detected
[   19.138881] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   19.139141] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   19.139210] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   19.139233] ohci_hcd 0000:00:13.3: irq 17, io mem 0xd0404000
[   19.198886] usb usb4: configuration #1 chosen from 1 choice
[   19.198914] hub 4-0:1.0: USB hub found
[   19.198926] hub 4-0:1.0: 2 ports detected
[   19.302787] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 17 (level, low) -> IRQ 17
[   19.303041] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   19.303110] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   19.303133] ohci_hcd 0000:00:13.4: irq 17, io mem 0xd0405000
[   19.362790] usb usb5: configuration #1 chosen from 1 choice
[   19.362814] hub 5-0:1.0: USB hub found
[   19.362825] hub 5-0:1.0: 2 ports detected
[   19.466855] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 23 (level, low) -> IRQ 23
[   19.467104] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   19.467181] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   19.467228] ehci_hcd 0000:00:13.5: debug port 1
[   19.467240] ehci_hcd 0000:00:13.5: irq 23, io mem 0xd0406000
[   19.478518] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.478649] usb usb6: configuration #1 chosen from 1 choice
[   19.478675] hub 6-0:1.0: USB hub found
[   19.478683] hub 6-0:1.0: 10 ports detected
[   19.582691] ahci 0000:00:12.0: version 3.0
[   19.582719] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.582975] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   19.582982] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   19.582985] ahci 0000:00:12.0: nr_ports (4) and implemented port map (0x1) don't match, using nr_ports
[   19.582987] ahci 0000:00:12.0: forcing PORTS_IMPL to 0xf
[   20.585966] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   20.585972] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   20.587222] scsi0 : ahci
[   20.587569] scsi1 : ahci
[   20.587737] scsi2 : ahci
[   20.587895] scsi3 : ahci
[   20.587961] ata1: SATA max UDMA/133 abar m1024@0xd0409000 port 0xd0409100 irq 16
[   20.587965] ata2: SATA max UDMA/133 abar m1024@0xd0409000 port 0xd0409180 irq 16
[   20.587969] ata3: SATA max UDMA/133 abar m1024@0xd0409000 port 0xd0409200 irq 16
[   20.587972] ata4: SATA max UDMA/133 abar m1024@0xd0409000 port 0xd0409280 irq 16
[   21.061702] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.062345] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL132C, max UDMA/100
[   21.062349] ata1.00: 234441648 sectors, multi 16: LBA48 
[   21.062890] ata1.00: configured for UDMA/100
[   21.373546] ata2: SATA link down (SStatus 0 SControl 0)
[   21.685392] ata3: SATA link down (SStatus 0 SControl 0)
[   21.997235] ata4: SATA link down (SStatus 0 SControl 0)

[   21.997362] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL13 PQ: 0 ANSI: 5
[   21.998889] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
[   21.998901] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   21.998911] SB600_PATA: not 100% native mode: will probe irqs later
[   21.998919]     ide0: BM-DMA at 0x5040-0x5047, BIOS settings: hda:DMA, hdb:pio
[   21.998931] Probing IDE interface ide0...
[   22.009618] Driver 'sd' needs updating - please use bus_type methods
[   22.013445] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   22.013460] sd 0:0:0:0: [sda] Write Protect is off
[   22.013463] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.013480] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.013542] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   22.013551] sd 0:0:0:0: [sda] Write Protect is off
[   22.013553] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.013568] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.013572]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3
[   22.110801] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.115354] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.402146] Attempting manual resume
[   22.402150] swsusp: Resume From Partition 8:6
[   22.402152] PM: Checking swsusp image.
[   22.402355] PM: Resume from disk failed.
[   22.427487] kjournald starting.  Commit interval 5 seconds
[   22.427649] EXT3-fs: mounted filesystem with ordered data mode.
[   23.405029] hda: TSSTcorpCD/DVDW TS-L632M, ATAPI CD/DVD-ROM drive
[   23.405070] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   23.405441] hda: MWDMA2 mode selected
[   23.405906] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.037683] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   30.098418] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.117634] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.429539] input: Power Button (FF) as /devices/virtual/input/input3
[   30.489308] ACPI: Power Button (FF) [PWRF]
[   30.489413] input: Sleep Button (CM) as /devices/virtual/input/input4
[   30.505445] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   30.537289] ACPI: Sleep Button (CM) [C28D]
[   30.537359] input: Lid Switch as /devices/virtual/input/input5
[   30.569372] ACPI: Lid Switch [C265]
[   30.573985] ACPI: AC Adapter [C1EB] (on-line)
[   30.616179] ACPI: Battery Slot [C1ED] (battery present)
[   30.616438] ACPI: Battery Slot [C1EC] (battery absent)
[   30.616970] ACPI: WMI-Acer: Mapper loaded
[   30.655691] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
[   30.713186] ACPI: Video Device [C08D] (multi-head: yes  rom: no  post: no)
[   30.929261] Yenta: CardBus bridge found at 0000:02:04.0 [103c:30c2]
[   31.057850] Yenta: ISA IRQ mask 0x0cb8, PCI irq 20
[   31.057856] Socket status: 30000006
[   31.057859] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   31.057865] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   31.258735] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   31.316951] [fglrx] Maximum main memory to use for locked dma buffers: 798 MBytes.
[   31.316987] [fglrx] ASYNCIO init succeed!
[   31.317330] [fglrx] PAT is enabled successfully!
[   31.317359] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   31.510462] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   31.510472] Uniform CD-ROM driver Revision: 3.20
[   31.635025] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   31.780256] NET: Registered protocol family 10
[   31.780482] lo: Disabled Privacy Extensions
[   31.780809] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.842124] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
[   31.842132] serio: Synaptics pass-through port at isa0060/serio4/input0
[   31.882007] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   32.726955] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   32.726961] tg3: eth0: Flow control is on for TX and on for RX.
[   32.728006] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.898419] lp: driver loaded but no devices found
[   34.102717] Adding 2152668k swap on /dev/sda6.  Priority:-1 extents:1 across:2152668k
[   34.710922] EXT3 FS on sda3, internal journal
[   36.109736] kjournald starting.  Commit interval 5 seconds
[   36.110091] EXT3 FS on sda5, internal journal
[   36.110099] EXT3-fs: mounted filesystem with ordered data mode.
[   36.132119] kjournald starting.  Commit interval 5 seconds
[   36.132461] EXT3 FS on sda7, internal journal
[   36.132465] EXT3-fs: mounted filesystem with ordered data mode.
[   36.487109] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.959398] No dock devices found.
[   37.319537] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[   37.319433] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[   37.319439] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[   37.319441] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[   37.319443] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   37.319513] powernow-k8: ph2 null fid transition 0xb
[   38.522138] ppdev: user-space parallel port driver
[   39.255720] Clocksource tsc unstable (delta = -185236677 ns)
[   39.904346] Bluetooth: Core ver 2.11
[   39.904830] NET: Registered protocol family 31
[   39.904833] Bluetooth: HCI device and connection manager initialized
[   39.904838] Bluetooth: HCI socket layer initialized
[   39.924877] Bluetooth: L2CAP ver 2.9
[   39.924882] Bluetooth: L2CAP socket layer initialized
[   39.974440] Bluetooth: RFCOMM socket layer initialized
[   39.974427] Bluetooth: RFCOMM TTY layer initialized
[   39.974432] Bluetooth: RFCOMM ver 1.8
[   40.905445] eth0: no IPv6 routers present
[   41.210502] ACPI: PCI Interrupt 0000:01:05.0[B] -> GSI 19 (level, low) -> IRQ 19
[   42.613703] [fglrx] GART Table is not in FRAME_BUFFER range 
[   42.613714] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   42.613717] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   47.613116] hda-intel: Invalid position buffer, using LPIB read method instead.
[   54.021397] CPU0 attaching NULL sched-domain.
[   54.021407] CPU1 attaching NULL sched-domain.
[   54.035396] CPU0 attaching sched-domain:
[   54.035401]  domain 0: span 03
[   54.035405]   groups: 01 02
[   54.035408]   domain 1: span 03
[   54.035409]    groups: 03
[   54.035413] CPU1 attaching sched-domain:
[   54.035416]  domain 0: span 03
[   54.035418]   groups: 02 01
[   54.035422]   domain 1: span 03
[   54.035424]    groups: 03
[  132.331341] tg3: eth0: Link is down.
[  162.046232] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  162.046238] tg3: eth0: Flow control is on for TX and on for RX.
[  204.516922] [fglrx] PCIe has already been initialized. Reinitializing ...
[  204.524122] [fglrx] GART Table is not in FRAME_BUFFER range 
[  204.524132] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[  204.524135] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[  211.554904] CPU0 attaching NULL sched-domain.
[  211.554912] CPU1 attaching NULL sched-domain.
[  211.586769] CPU0 attaching sched-domain:
[  211.586778]  domain 0: span 03
[  211.586780]   groups: 01 02
[  211.586783]   domain 1: span 03
[  211.586784]    groups: 03
[  211.586786] CPU1 attaching sched-domain:
[  211.586788]  domain 0: span 03
[  211.586789]   groups: 02 01
[  211.586792]   domain 1: span 03
[  211.586793]    groups: 03
[  564.986130] APIC error on CPU0: 00(40)
[  564.984945] APIC error on CPU1: 00(40)

lspci:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

---

### Post by dcstar on 2008-03-29
> **m.hricko said:**
> Hello,

I have a HP 6715s laptop with Turion X2 TL-58 CPU[http://geizhals.at/eu/a264276.html]("http://geizhals.at/eu/a264276.html") . I have tried a lot of distros and I mentioned one thing. If I run a 64bit distro, the system is heating much more faster than witch 32bit distro, so the fan is turning on more often. It is the same with ubuntu, mandriva, simply-mepis and other 64bit ports and with kernels 2.6.18, 20, 22, 24. Now I am running 32bit gutsy and 64bit hardy beta. I cannot compare it with windows, because i have only a 32bit wxp.
........
dmesg
[   37.319537] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[B][   37.319433] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[   37.319439] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[   37.319441] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[   37.319443] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e[/B]
[   37.319513] powernow-k8: ph2 null fid transition 0xb


Simply add in and use the CPU Frequency Scaling applet to set the thing to use less power.

---

### Post by m.hricko on 2008-03-30
Thanks for reply, but i forgot to write, that cpuscaling is runnig on both systems (32 and 64 bit) and CPU is running on 800 MHz. The governor is in both systems cpufreq_conservative and a cpufreqd is running.

---

