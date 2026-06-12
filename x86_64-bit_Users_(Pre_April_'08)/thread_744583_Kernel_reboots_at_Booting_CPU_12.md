---
title: "Kernel reboots at Booting CPU 1/2"
date: 2008-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Elpres on 2008-04-03
Good morning,

I have been experiencing a problem that has only showed up after I setup dual boot on my machine. One would think that some how in the process I have stuffed up something. 
What happens is that when I boot my normal selection from Grub the boot processes gets to Booting CPU 1/2 and hangs for a second (this is when I know the problem happens) it then spits out a bit more code and the machine reboots. This is really annoying. I have managed to somehow get into Ubuntu 7.10 using the rescue option. Most of the time this problem occurs no matter what option I use. I have tried the noapic acpi=off option and still no go. This is the dmesg from when I have successfully booted.

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] Command line: root=UUID=ec2e8377-6730-4f92-9d4c-451a0b65813e ro single
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6BE0 checksum 0
[    0.000000] ACPI: RSDP 000F6BE0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEE3180, 4B32 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEE7E00, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEE7E80, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEE7D00, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7FEE7F00, 019E (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 7FEE8390, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1127 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515612
[    0.000000] Kernel command line: root=UUID=ec2e8377-6730-4f92-9d4c-451a0b65813e ro single
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   28.506612] time.c: Detected 2199.997 MHz processor.
[   28.507843] Console: colour VGA+ 80x25
[   28.510763] Checking aperture...
[   28.510814] Calgary: detecting Calgary via BIOS EBDA area
[   28.510816] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   28.527847] Memory: 2054428k/2096000k available (2274k kernel code, 41184k reserved, 1185k data, 296k init)
[   28.527946] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   28.605063] Calibrating delay using timer specific routine.. 4403.20 BogoMIPS (lpj=8806407)
[   28.605184] Security Framework v1.0.0 initialized
[   28.605232] SELinux:  Disabled at boot.
[   28.605452] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   28.606099] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.606643] Mount-cache hash table entries: 256
[   28.606807] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.606888] CPU: L2 cache: 2048K
[   28.606933] CPU 0/0 -> Node 0
[   28.606978] using mwait in idle threads.
[   28.607023] CPU: Physical Processor ID: 0
[   28.607068] CPU: Processor Core ID: 0
[   28.607117] CPU0: Thermal monitoring enabled (TM2)
[   28.607171] SMP alternatives: switching to UP code
[   28.607437] Early unpacking initramfs... done
[   28.925292] ACPI: Core revision 20070126
[   28.925372] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.956881] Using local APIC timer interrupts.
[   30.002341] result 12499981
[   30.002385] Detected 12.499 MHz APIC timer.
[   30.003746] SMP alternatives: switching to SMP code
[   30.003859] Booting processor 1/2 APIC 0x1                ----------- This is where it hangs
[   30.014101] Initializing CPU#1
[   30.091612] Calibrating delay using timer specific routine.. 4400.17 BogoMIPS (lpj=8800341)
[   30.091618] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.091620] CPU: L2 cache: 2048K
[   30.091622] CPU 1/1 -> Node 0
[   30.091623] CPU: Physical Processor ID: 0
[   30.091624] CPU: Processor Core ID: 1
[   30.091629] CPU1: Thermal monitoring enabled (TM2)
[   30.091902] Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[   30.091926] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   30.115601] Brought up 2 CPUs
[   30.172117] migration_cost=10
[   30.172380] NET: Registered protocol family 16
[   30.172491] ACPI: bus type pci registered
[   30.172541] PCI: Using configuration type 1
[   30.173536] ACPI: EC: Look up EC in DSDT
[   30.177106] ACPI: Interpreter enabled
[   30.177156] ACPI: (supports S0 S3 S4 S5)
[   30.177381] ACPI: Using IOAPIC for interrupt routing
[   30.182264] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.182326] PCI: Probing PCI hardware (bus 00)
[   30.183727] PCI: Transparent bridge - 0000:00:1e.0
[   30.183828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.183947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   30.184011] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   30.184075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   30.184140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   30.197119] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   30.197678] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   30.198299] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   30.198855] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
[   30.199411] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   30.199993] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   30.200549] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[   30.201104] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   30.201657] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.201713] pnp: PnP ACPI init
[   30.201762] ACPI: bus type pnp registered
[   30.203892] pnp: PnP ACPI: found 13 devices
[   30.203938] ACPI: ACPI bus type pnp unregistered
[   30.204026] PCI: Using ACPI for IRQ routing
[   30.204072] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.204219] NET: Registered protocol family 8
[   30.204265] NET: Registered protocol family 20
[   30.204326] PCI-GART: No AMD northbridge found.
[   30.204374] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   30.204585] hpet0: 4 64-bit timers, 14318180 Hz
[   30.205674] pnp: 00:09: ioport range 0x400-0x4bf has been reserved
[   30.205725] pnp: 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   30.205783] pnp: 00:0b: iomem range 0xcd000-0xcffff has been reserved
[   30.205832] pnp: 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   30.205880] pnp: 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   30.205929] pnp: 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   30.206208] PCI: Bridge: 0000:00:01.0
[   30.206254]   IO window: a000-afff
[   30.206301]   MEM window: f4000000-f7ffffff
[   30.206348]   PREFETCH window: e0000000-efffffff
[   30.206395] PCI: Bridge: 0000:00:1c.0
[   30.206441]   IO window: 9000-9fff
[   30.206488]   MEM window: disabled.
[   30.206534]   PREFETCH window: disabled.
[   30.206582] PCI: Bridge: 0000:00:1c.3
[   30.206628]   IO window: b000-bfff
[   30.206675]   MEM window: fc000000-fc0fffff
[   30.206722]   PREFETCH window: disabled.
[   30.206770] PCI: Bridge: 0000:00:1c.4
[   30.206816]   IO window: c000-cfff
[   30.206863]   MEM window: f8000000-f9ffffff
[   30.206910]   PREFETCH window: 80000000-800fffff
[   30.206959] PCI: Bridge: 0000:00:1e.0
[   30.207003]   IO window: disabled.
[   30.207051]   MEM window: fa000000-fbffffff
[   30.207098]   PREFETCH window: disabled.
[   30.207153] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.207245] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.207259] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.207350] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.207364] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   30.207456] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   30.207470] ACPI: PCI Interrupt 0000:00:1c.4[A] -> <6>Time: tsc clocksource has been installed.
[   30.207586] GSI 16 (level, low) -> IRQ 16
[   30.207633] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   30.207641] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   30.207650] NET: Registered protocol family 2
[   30.251647] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   30.252300] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   30.255240] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   30.255805] TCP: Hash tables configured (established 262144 bind 65536)
[   30.255854] TCP reno registered
[   30.267728] checking if image is initramfs... it is
[   30.896960] Freeing initrd memory: 7748k freed
[   30.900698] audit: initializing netlink socket (disabled)
[   30.900761] audit(1207274831.356:1): initialized
[   30.902439] VFS: Disk quotas dquot_6.5.1
[   30.902521] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   30.902636] io scheduler noop registered
[   30.902682] io scheduler anticipatory registered
[   30.902728] io scheduler deadline registered
[   30.902849] io scheduler cfq registered (default)
[   30.904697] Boot video device is 0000:01:00.0
[   30.904809] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.904837] assign_interrupt_mode Found MSI capability
[   30.904886] Allocate Port Service[0000:00:01.0:pcie00]
[   30.904950] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.904984] assign_interrupt_mode Found MSI capability
[   30.905031] Allocate Port Service[0000:00:1c.0:pcie00]
[   30.905057] Allocate Port Service[0000:00:1c.0:pcie02]
[   30.905119] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   30.905153] assign_interrupt_mode Found MSI capability
[   30.905199] Allocate Port Service[0000:00:1c.3:pcie00]
[   30.905223] Allocate Port Service[0000:00:1c.3:pcie02]
[   30.905287] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   30.905321] assign_interrupt_mode Found MSI capability
[   30.905368] Allocate Port Service[0000:00:1c.4:pcie00]
[   30.905390] Allocate Port Service[0000:00:1c.4:pcie02]
[   30.921480] Real Time Clock Driver v1.12ac
[   30.921673] hpet_resources: 0xfed00000 is busy
[   30.921703] Linux agpgart interface v0.102 (c) Dave Jones
[   30.921750] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.921893] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.922388] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.922946] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.923098] input: Macintosh mouse button emulation as /class/input/input0
[   30.923234] PNP: No PS/2 controller found. Probing ports directly.
[   30.923614] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.923669] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.923901] mice: PS/2 mouse device common for all mice
[   30.924050] TCP cubic registered
[   30.924146] NET: Registered protocol family 1
[   30.924352] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   30.924415] Freeing unused kernel memory: 296k freed
[   31.043963] AppArmor: AppArmor initialized<5>audit(1207274831.500:2):  type=1505 info="AppArmor initialized" pid=1233
[   31.048039] fuse init (API version 7.8)
[   31.051677] Failure registering capabilities with primary security module.
[   31.076005] ACPI: Processor [CPU0] (supports 8 throttling states)
[   31.076215] ACPI: SSDT 7FEE8300, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   31.076428] ACPI: Processor [CPU1] (supports 8 throttling states)
[   31.076548] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.076678] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.404401] usbcore: registered new interface driver usbfs
[   31.404469] usbcore: registered new interface driver hub
[   31.427839] usbcore: registered new device driver usb
[   31.428498] USB Universal Host Controller Interface driver v3.0
[   31.428622] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.428721] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   31.428724] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   31.428887] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   31.428969] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d100
[   31.429121] usb usb1: configuration #1 chosen from 1 choice
[   31.429194] hub 1-0:1.0: USB hub found
[   31.429245] hub 1-0:1.0: 2 ports detected
[   31.447166] SCSI subsystem initialized
[   31.450673] libata version 2.21 loaded.
[   31.530894] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   31.530993] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   31.530997] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   31.531160] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   31.531240] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d200
[   31.531564] usb usb2: configuration #1 chosen from 1 choice
[   31.531735] hub 2-0:1.0: USB hub found
[   31.531783] hub 2-0:1.0: 2 ports detected
[   31.635176] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.635271] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   31.635274] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   31.635443] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   31.635520] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d000
[   31.635851] usb usb3: configuration #1 chosen from 1 choice
[   31.636026] hub 3-0:1.0: USB hub found
[   31.636074] hub 3-0:1.0: 2 ports detected
[   31.739641] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   31.739735] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   31.739738] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   31.739914] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   31.739991] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d300
[   31.740350] usb usb4: configuration #1 chosen from 1 choice
[   31.740536] hub 4-0:1.0: USB hub found
[   31.740584] hub 4-0:1.0: 2 ports detected
[   31.771408] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   31.844120] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   31.844214] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   31.844217] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   31.844403] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   31.844481] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d400
[   31.844865] usb usb5: configuration #1 chosen from 1 choice
[   31.845067] hub 5-0:1.0: USB hub found
[   31.845114] hub 5-0:1.0: 2 ports detected
[   31.948695] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.948789] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   31.948792] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   31.948996] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   31.949071] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d500
[   31.949490] usb usb6: configuration #1 chosen from 1 choice
[   31.949723] hub 6-0:1.0: USB hub found
[   31.949771] hub 6-0:1.0: 2 ports detected
[   31.956623] usb 1-2: configuration #1 chosen from 1 choice
[   32.057353] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   32.057880] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   32.057885] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   32.058492] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   32.058575] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   32.058582] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc105000
[   32.062503] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.062654] usb usb7: configuration #1 chosen from 1 choice
[   32.062729] hub 7-0:1.0: USB hub found
[   32.062782] hub 7-0:1.0: 6 ports detected
[   32.078877] usbcore: registered new interface driver hiddev
[   32.123396] usbcore: registered new interface driver usbhid
[   32.123454] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.169306] ata_piix 0000:00:1f.2: version 2.11
[   32.169315] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   32.169552] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   32.169667] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   32.169754] scsi0 : ata_piix
[   32.169828] scsi1 : ata_piix
[   32.169949] ata1: SATA max UDMA/133 cmd 0x000000000001d600 ctl 0x000000000001d702 bmdma 0x000000000001da00 irq 19
[   32.170010] ata2: SATA max UDMA/133 cmd 0x000000000001d800 ctl 0x000000000001d902 bmdma 0x000000000001da08 irq 19
[   32.349546] usb 1-2: USB disconnect, address 2
[   32.377128] ata1.00: Host Protected Area detected:
[   32.377131] 	current size: 156299375 sectors
[   32.377133] 	native size: 156301488 sectors
[   32.501909] ata1.00: native size increased to 156301488 sectors
[   32.501969] ata1.00: ATA-7: MAXTOR STM380215AS, 3.AAD, max UDMA/133
[   32.502022] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   32.576837] ata1.00: configured for UDMA/133
[   32.590309] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   32.775838] usb 1-2: configuration #1 chosen from 1 choice
[   32.792992] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /class/input/input1
[   32.793058] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:1a.0-2
[   32.936770] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /class/input/input2
[   32.936852] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:1a.0-2
[   33.052644] ata2.00: ATAPI: Optiarc DVD RW AD-7200S, 1.04, max UDMA/100
[   33.224958] ata2.00: configured for UDMA/100
[   33.225109] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM380215 3.AA PQ: 0 ANSI: 5
[   33.226880] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7200S  1.04 PQ: 0 ANSI: 5
[   33.227024] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   33.227253] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   33.227366] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   33.227391] scsi2 : ata_piix
[   33.227462] scsi3 : ata_piix
[   33.227584] ata3: SATA max UDMA/133 cmd 0x000000000001dd00 ctl 0x000000000001de02 bmdma 0x000000000001e100 irq 19
[   33.227644] ata4: SATA max UDMA/133 cmd 0x000000000001df00 ctl 0x000000000001e002 bmdma 0x000000000001e108 irq 19
[   33.389704] ata3.00: ATA-6: WDC WD800JD-75JNA0, 05.01C05, max UDMA/100
[   33.389758] ata3.00: 156250000 sectors, multi 16: LBA 
[   33.397754] ata3.00: configured for UDMA/100
[   33.564852] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800JD-75JN 05.0 PQ: 0 ANSI: 5
[   33.565178] ahci 0000:03:00.0: version 2.2
[   33.565197] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   34.569803] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   34.570574] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   34.570626] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   34.570718] scsi4 : ahci
[   34.570948] scsi5 : ahci
[   34.571161] ata5: SATA max UDMA/133 cmd 0xffffc20000ab4100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   34.571223] ata6: SATA max UDMA/133 cmd 0xffffc20000ab4180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   34.886866] ata5: SATA link down (SStatus 0 SControl 300)
[   35.195768] ata6: SATA link down (SStatus 0 SControl 300)
[   35.196559] r8169 Gigabit Ethernet driver 2.2LK loaded
[   35.196629] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.196736] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   35.197992] eth0: RTL8168b/8111b at 0xffffc20000ab2000, 00:1d:7d:d1:11:d4, XID 38000000 IRQ 16
[   35.199238] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   35.199291] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
[   35.199655] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   35.199689] scsi6 : pata_jmicron
[   35.199920] scsi7 : pata_jmicron
[   35.200046] ata7: PATA max UDMA/100 cmd 0x000000000001b000 ctl 0x000000000001b102 bmdma 0x000000000001b400 irq 16
[   35.200107] ata8: PATA max UDMA/100 cmd 0x000000000001b200 ctl 0x000000000001b302 bmdma 0x000000000001b408 irq 16
[   35.373414] ata7.00: Host Protected Area detected:
[   35.373416] 	current size: 78122887 sectors
[   35.373418] 	native size: 78125000 sectors
[   35.374007] ata7.00: native size increased to 78125000 sectors
[   35.374061] ata7.00: ATA-6: IC35L060AVV207-0, V22OA66A, max UDMA/100
[   35.374114] ata7.00: 78125000 sectors, multi 16: LBA48 
[   35.397541] ata7.00: configured for UDMA/100
[   35.564833] scsi 6:0:0:0: Direct-Access     ATA      IC35L060AVV207-0 V22O PQ: 0 ANSI: 5
[   35.565276] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   35.565788] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   35.565794] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   35.566068] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   35.566155] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   35.566163] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc104000
[   35.570087] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.570234] usb usb8: configuration #1 chosen from 1 choice
[   35.570306] hub 8-0:1.0: USB hub found
[   35.570358] hub 8-0:1.0: 6 ports detected
[   35.573034] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   35.573092] sd 0:0:0:0: [sda] Write Protect is off
[   35.573139] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.573150] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.573243] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   35.573303] sd 0:0:0:0: [sda] Write Protect is off
[   35.573353] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.573364] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.573427]  sda: sda1 sda2 < sda5 >
[   35.620251] sd 0:0:0:0: [sda] Attached SCSI disk
[   35.620418] sd 2:0:0:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   35.620474] sd 2:0:0:0: [sdb] Write Protect is off
[   35.620521] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.620533] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.620620] sd 2:0:0:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   35.620674] sd 2:0:0:0: [sdb] Write Protect is off
[   35.620720] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.620732] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.620792]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   35.627981] Uniform CD-ROM driver Revision: 3.20
[   35.628075] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   35.629241]  sdb1
[   35.629370] sd 2:0:0:0: [sdb] Attached SCSI disk
[   35.629453] sd 6:0:0:0: [sdc] 78125000 512-byte hardware sectors (40000 MB)
[   35.629507] sd 6:0:0:0: [sdc] Write Protect is off
[   35.629554] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   35.629564] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.629652] sd 6:0:0:0: [sdc] 78125000 512-byte hardware sectors (40000 MB)
[   35.629706] sd 6:0:0:0: [sdc] Write Protect is off
[   35.629752] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   35.629763] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.629822]  sdc: sdc1
[   35.643442] sd 6:0:0:0: [sdc] Attached SCSI disk
[   35.646222] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   35.646289] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   35.646357] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   35.646422] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   35.962485] Attempting manual resume
[   35.962532] swsusp: Resume From Partition 8:5
[   35.962533] PM: Checking swsusp image.
[   35.962686] PM: Resume from disk failed.
[   35.989154] kjournald starting.  Commit interval 5 seconds
[   35.989217] EXT3-fs: mounted filesystem with ordered data mode.
[   43.324932] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.326665] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.349351] input: PC Speaker as /class/input/input3
[   43.359312] Linux video capture interface: v2.00
[   43.510121] parport_pc 00:08: reported by Plug and Play ACPI
[   43.510222] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   43.752742] nvidia: module license 'NVIDIA' taints kernel.
[   44.006048] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.006150] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   44.006232] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   44.062301] usbcore: registered new interface driver xpad
[   44.062356] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   44.210208] cx2388x v4l2 driver version 0.0.6 loaded
[   44.210309] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[   44.210423] CORE cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected]
[   44.210484] TV tuner 4 at 0x1fe, Radio tuner -1 at 0x1fe
[   44.211648] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   44.380007] cx88[0]/0: found at 0000:05:00.0, rev: 5, irq: 20, latency: 32, mmio: 0xfa000000
[   44.380122] cx88[0]/0: registered device video0 [v4l2]
[   44.380191] cx88[0]/0: registered device vbi0
[   44.380291] cx88[0]/2: cx2388x 8802 Driver Manager
[   44.380356] ACPI: PCI Interrupt 0000:05:00.2[A] -> <6>ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   44.380662] GSI 20 (level, low) -> IRQ 20
[   44.380719] cx88[0]/2: found at 0000:05:00.2, rev: 5, irq: 20, latency: 32, mmio: 0xfb000000
[   44.380897] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   44.454163] cx2388x dvb driver version 0.0.6 loaded
[   44.454215] cx8802_register_driver() ->registering driver type=dvb access=shared
[   44.454273] CORE cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21]
[   44.454331] cx88[0]/2: cx2388x based dvb card
[   44.480079] DVB: registering new adapter (cx88[0]).
[   44.480130] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[   44.588844] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   45.573775] lp0: using parport0 (interrupt-driven).
[   45.631347] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   45.969076] EXT3 FS on sda1, internal journal
[   46.185759] kjournald starting.  Commit interval 5 seconds
[   46.185769] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   46.195042] EXT3 FS on sdb1, internal journal
[   46.195048] EXT3-fs: mounted filesystem with ordered data mode.
[   67.978598] No dock devices found.
[   68.053358] input: Power Button (FF) as /class/input/input4
[   68.053374] ACPI: Power Button (FF) [PWRF]
[   68.053410] input: Power Button (CM) as /class/input/input5
[   68.053420] ACPI: Power Button (CM) [PWRB]
[   69.145869] ppdev: user-space parallel port driver
[   69.313283] r8169: eth0: link up
[   69.313289] r8169: eth0: link up
[   69.613030] audit(1207274872.168:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5483 profile="/usr/sbin/cupsd"
[   72.231370] Failure registering capabilities with primary security module.
[   72.255117] NET: Registered protocol family 10
[   72.255348] lo: Disabled Privacy Extensions
[   72.453136] Bluetooth: Core ver 2.11
[   72.453178] NET: Registered protocol family 31
[   72.453180] Bluetooth: HCI device and connection manager initialized
[   72.453182] Bluetooth: HCI socket layer initialized
[   72.488746] Bluetooth: L2CAP ver 2.8
[   72.488749] Bluetooth: L2CAP socket layer initialized
[   72.563361] Bluetooth: RFCOMM socket layer initialized
[   72.563458] Bluetooth: RFCOMM TTY layer initialized
[   72.563460] Bluetooth: RFCOMM ver 1.8
[   76.955005] NET: Registered protocol family 17
[   88.952672] eth0: no IPv6 routers present
[26083.462058] audit(1207263023.737:4):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=8878 profile="/usr/sbin/cupsd" 
```

I would like to upgrade my kernel and still use the packages available on the repos, is that possible?

Windows XP boots fine everytime, booting from another HDD linked from GRUB. This is my GRUB menu.lst

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ec2e8377-6730-4f92-9d4c-451a0b65813e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the defaulreboots after booting processor 1/2t Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7file:///usr/share/ubuntu-artwork/home/index.html
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec2e8377-6730-4f92-9d4c-451a0b65813e ro
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec2e8377-6730-4f92-9d4c-451a0b65813e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Windows
map 		(hd0) (hd1)
map 		(hd1) (hd0)
rootnoverify 	(hd1,0)
chainloader 	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Thanks in advance for all your help. I don't want to reinstall this because I have finally got it setup and updated the way I like it.

---

### Post by wPwLUi3N on 2008-04-03
Problem is there from fresh install or after some tweaking?

---

### Post by mrsteveman1 on 2008-04-03
Boot with this line as your kernel options:

```
vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single
```

It will probably work, if it doesn't something is seriously wrong.

If it works reliably, take away one option at a time until it stops working so you know what was fixing things.

---

### Post by DarkFox.DK on 2008-04-16
> **mrsteveman1 said:**
> Boot with this line as your kernel options:

```
vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single
```

It will probably work, if it doesn't something is seriously wrong.

If it works reliably, take away one option at a time until it stops working so you know what was fixing things.

I do not have dual boot, but i got the same symptoms as the OP.

the minimum of arguments that works for me are
```
acpi=off nosmp
```

If you could maybe make some assumptions on what is wrong, based uppon that, i would be even more happy than i am now :-)

---

### Post by mrsteveman1 on 2008-04-16
By dual boot do you mean dual core?

If so, it would appear something made the kernel panic, if NOSMP fixes things there is a bug somewhere in the handling of an SMP kernel on single core hardware.

acpi causes all kinds of problems, having to disable it is fairly common. The implementation of ACPI on a lot of mainboards is the real problem, manufacturers don't always do it right.

You have to use BOTH of those options at the same time to get it to boot at all?

---

### Post by DarkFox.DK on 2008-04-16
> **mrsteveman1 said:**
> By dual boot do you mean dual core?

Dual boot, i was refering to the OP's problem "..showed up after I setup dual boot.."


> **mrsteveman1 said:**
> If so, it would appear something made the kernel panic, if NOSMP fixes things there is a bug somewhere in the handling of an SMP kernel on single core hardware.

acpi causes all kinds of problems, having to disable it is fairly common. The implementation of ACPI on a lot of mainboards is the real problem, manufacturers don't always do it right.

You have to use BOTH of those options at the same time to get it to boot at all?

Yes, if i leave out acpi=off it hangs on "booting CPU 1/2", and if i leave out NOSMP it hangs on some drive mounting thing, i'm sorry i can't be more accurate right now, but i can't reboot the server right now.

I'll be back later with some more details... after i get some sleep.

---

### Post by DarkFox.DK on 2008-04-17
If i leave out acpi=off it timeouts at some ata thing and keeps trying untill i power cycle it.

if i leave out nosmp it gets to the booting cpu 1/2 and reboots...

---

### Post by mrsteveman1 on 2008-04-17
Whats the processor in this machine? Are you using gutsy or hardy?

---

### Post by DarkFox.DK on 2008-04-17
> **mrsteveman1 said:**
> Whats the processor in this machine? Are you using gutsy or hardy?

It is an Intel Core 2 Duo E8200, Gutsy - 64 bit - server ed.

It seems it only detects one of the cores... at least only one core shows up in the VMware control panel, is there a way i can double-check this?

---

### Post by mrsteveman1 on 2008-04-17
The kernel log should show you how many cores are active:
```

sudo dmesg | grep cpu  (or CPU maybe, its case sensitive)
```

Are you running this on bare hardware or in vmware?

---

### Post by DarkFox.DK on 2008-04-17
> **mrsteveman1 said:**
> The kernel log should show you how many cores are active:
```

sudo dmesg | grep cpu  (or CPU maybe, its case sensitive)
```
Output: ```

$ sudo dmesg | grep CPU
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 42120 bytes of per cpu data
[    0.000000] Initializing CPU#0
[   17.387030] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.539065] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.539118] CPU: L2 cache: 6144K
[   17.539153] CPU 0/0 -> Node 0
[   17.539222] CPU: Physical Processor ID: 0
[   17.539258] CPU: Processor Core ID: 0
[   17.539296] CPU0: Thermal monitoring enabled (TM2)
[   17.860816] Brought up 1 CPUs
```
So it seems it allows 2 CPUs/cores but only brings up one...

> **mrsteveman1 said:**
> Are you running this on bare hardware or in vmware?
Bare hardware, VMware was just the only indication i had on the CPU problem.

edit: looked around some more, this stuff might be relevant
```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz
stepping        : 6
cpu MHz         : 2666.760
cache size      : 6144 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc up pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5339.19
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```
```
$ uname -a
Linux fox 2.6.22-14-server #1 SMP Tue Feb 12 03:10:53 UTC 2008 x86_64 GNU/Linux
```

---

### Post by DrCoolSanta on 2008-04-17
Seems more of a hardware problem. You seem to have put nosmp in the boot procedure and it is still loading the SMP kernel, maybe that's intended. It's allowing 2 CPUs because of the SMP kernel. Get some bootable CD with GUI so that it is easy and use it to check whether the other CPU is alright or not.

---

### Post by DarkFox.DK on 2008-04-18
I just got it to start up without nosmp, and it detected and brought up both cores. however i haven't been able to make it do it again... yet.

Edit: I managed to snap a pic of the screen right before it shuts down when i leave out nosmp:
[img]http://lzd.dk/fail.jpg[/img]
(actually a snap from a video... went forward frame-by-frame untill just before the screen went black)

Edit: i uploaded the videos to youtube, i actually recorded the one where it succeded without nosmp, if you can make anything out of this.
Failed: [http://www.youtube.com/watch?v=peFmyMR3TeA](http://www.youtube.com/watch?v=peFmyMR3TeA)
Succeded: [http://www.youtube.com/watch?v=3xi61G1nE6I](http://www.youtube.com/watch?v=3xi61G1nE6I)

---

### Post by mrsteveman1 on 2008-04-18
Ok so its a core 2 duo processor, which are all SMP chips and should be well supported by the kernel.

As of one of the 2.6.x kernel series all kernels are SMP, they simply disable the SMP stuff if the system has only one CPU. You can see this on a single proc system in the kernel log, it will say "switching to UP code" meaning uniprocessor.

Have you tried booting this machine with NOLAPIC and NOAPIC (i think those are the ones)?

---

### Post by DarkFox.DK on 2008-04-19
> **mrsteveman1 said:**
> Have you tried booting this machine with NOLAPIC and NOAPIC (i think those are the ones)?

I haven't tried those whitout nosmp, but i will try as soon as i get back home to the machine. (should be tomorrow some time)

---

### Post by DarkFox.DK on 2008-04-20
> **DarkFox.DK said:**
> I haven't tried those whitout nosmp, but i will try as soon as i get back home to the machine. (should be tomorrow some time)

Just tried with noapic, it works :-)

---

### Post by mrsteveman1 on 2008-04-20
Thats good that it works. Bugs in the motherboard sometimes have to be worked around like this, but the processor should be very very well supported.

---

