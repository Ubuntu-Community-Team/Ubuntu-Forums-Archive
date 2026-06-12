---
title: "intel core 2 duo-APIC error on CPU1: 00(40)- Ubuntu x86 or Ubuntu x64?"
date: 2007-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ctw on 2007-01-03
Hi People,

Till 2 weeks I bought me one XPC Barebone with intel core 2 duo.
I've tested first to install the Ubuntu 6.10 Desktop distro and I didn't find any problem, but I read in this forum that is better to install the Ubuntu distro x64 for this kind of CPU.

Here is mein dmesg with the error:


catworld@catworld-xpc:~$ dmesg
[    0.000000] Bootdata ok (command line is root=/dev/sda4 ro quiet splash locale=ca_ES)
[    0.000000] Linux version 2.6.17-10-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 21:16:35 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 XPC                                   ) @ 0x00000000000f9220
[    0.000000] ACPI: RSDT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff3040
[    0.000000] ACPI: FADT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff30c0
[    0.000000] ACPI: MCFG (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff7440
[    0.000000] ACPI: MADT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fff7340
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20041203) @ 0x000000007fff74c0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20041203) @ 0x000000007fff7950
[    0.000000] ACPI: DSDT (v001 XPC     SD37V10 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fff0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
[    0.000000] On node 0 totalpages: 515641
[    0.000000]   DMA zone: 2576 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Checking aperture...
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sda4 ro quiet splash locale=ca_ES
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2400.719 MHz processor.
[   23.705527] Console: colour VGA+ 80x25
[   23.706783] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.707712] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.727932] Memory: 2053560k/2097088k available (2129k kernel code, 43140k reserved, 1424k data, 188k init)
[   23.806348] Calibrating delay using timer specific routine.. 4805.04 BogoMIPS (lpj=9610089)
[   23.806391] Security Framework v1.0.0 initialized
[   23.806396] SELinux:  Disabled at boot.
[   23.806414] Mount-cache hash table entries: 256
[   23.806537] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.806539] CPU: L2 cache: 4096K
[   23.806542] using mwait in idle threads.
[   23.806543] CPU: Physical Processor ID: 0
[   23.806544] CPU: Processor Core ID: 0
[   23.806550] CPU0: Thermal monitoring enabled (TM1)
[   23.806559] SMP alternatives: switching to UP code
[   23.806762] checking if image is initramfs... it is
[   24.230279] Freeing initrd memory: 5746k freed
[   24.233706] ACPI: Core revision 20060707
[   24.239320] ACPI: Looking for DSDT ... not found!
[   24.288453] activating NMI Watchdog ... done.
[   24.288460] Using local APIC timer interrupts.
[   24.330063] result 16671640
[   24.330064] Detected 16.671 MHz APIC timer.
[   24.333863] SMP alternatives: switching to SMP code
[   24.333980] Booting processor 1/2 APIC 0x1
[   24.345002] Initializing CPU#1
[   24.421591] Calibrating delay using timer specific routine.. 4801.72 BogoMIPS (lpj=9603445)
[   24.421597] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.421598] CPU: L2 cache: 4096K
[   24.421600] CPU: Physical Processor ID: 0
[   24.421601] CPU: Processor Core ID: 1
[   24.421606] CPU1: Thermal monitoring enabled (TM2)
[   24.422015] Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[  **[COLOR="Navy"] 24.425596] APIC error on CPU1: 00(40)[/COLOR]**
[   24.425611] Brought up 2 CPUs
[   24.425642] testing NMI watchdog ... OK.
[   24.555744] migration_cost=19
[   24.555960] NET: Registered protocol family 16
[   24.555977] ACPI: bus type pci registered
[   24.558673] PCI: Using MMCONFIG at e0000000
[   24.567466] ACPI: Interpreter enabled
[   24.567468] ACPI: Using IOAPIC for interrupt routing
[   24.567868] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.567870] PCI: Probing PCI hardware (bus 00)
[   24.569581] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[   24.569724] Boot video device is 0000:02:00.0
[   24.569947] PCI: Transparent bridge - 0000:00:1e.0
[   24.569974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.577891] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   24.578488] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   24.580633] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   24.580818] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.581002] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   24.581184] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 11 12 14 *15)
[   24.581365] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.581564] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.581744] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   24.581925] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   24.582111] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.582119] pnp: PnP ACPI init
[   24.584140] pnp: PnP ACPI: found 11 devices
[   24.584173] PCI: Using ACPI for IRQ routing
[   24.584175] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.584250] PCI-DMA: Disabling IOMMU.
[   24.584510] pnp: 00:07: ioport range 0x400-0x4bf could not be reserved
[   24.584664] PCI: Bridge: 0000:00:01.0
[   24.584666]   IO window: b000-bfff
[   24.584668]   MEM window: fd900000-fd9fffff
[   24.584670]   PREFETCH window: fdc00000-fdcfffff
[   24.584672] PCI: Bridge: 0000:00:03.0
[   24.584674]   IO window: d000-dfff
[   24.584676]   MEM window: fa000000-fcffffff
[   24.584677]   PREFETCH window: d0000000-dfffffff
[   24.584679] PCI: Bridge: 0000:00:1c.0
[   24.584681]   IO window: c000-cfff
[   24.584684]   MEM window: fde00000-fdefffff
[   24.584686]   PREFETCH window: fdd00000-fddfffff
[   24.584689] PCI: Bridge: 0000:00:1e.0
[   24.584690]   IO window: e000-efff
[   24.584693]   MEM window: fdb00000-fdbfffff
[   24.584695]   PREFETCH window: fda00000-fdafffff
[   24.584702] GSI 16 sharing vector 0xA9 and IRQ 16
[   24.584704] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[   24.584707] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.584710] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 169
[   24.584713] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.584721] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[   24.584725] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.584730] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.584755] NET: Registered protocol family 2
[   24.621581] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   24.621752] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   24.623311] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   24.623752] TCP: Hash tables configured (established 262144 bind 65536)
[   24.623754] TCP reno registered
[   24.624292] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   24.624609] audit: initializing netlink socket (disabled)
[   24.624621] audit(1167819655.924:1): initialized
[   24.624750] VFS: Disk quotas dquot_6.5.1
[   24.624769] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.624809] Initializing Cryptographic API
[   24.624813] io scheduler noop registered
[   24.624820] io scheduler anticipatory registered
[   24.624825] io scheduler deadline registered
[   24.624839] io scheduler cfq registered (default)
[   32.647505] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   32.648502] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[   32.648506] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.648517] assign_interrupt_mode Found MSI capability
[   32.648543] Allocate Port Service[0000:00:01.0:pcie00]
[   32.648570] Allocate Port Service[0000:00:01.0:pcie03]
[   32.648596] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 169
[   32.648599] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   32.648609] assign_interrupt_mode Found MSI capability
[   32.648620] Allocate Port Service[0000:00:03.0:pcie00]
[   32.648643] Allocate Port Service[0000:00:03.0:pcie03]
[   32.648672] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[   32.648675] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   32.648697] assign_interrupt_mode Found MSI capability
[   32.648720] Allocate Port Service[0000:00:1c.0:pcie00]
[   32.648743] Allocate Port Service[0000:00:1c.0:pcie02]
[   32.648765] Allocate Port Service[0000:00:1c.0:pcie03]
[   32.662527] Real Time Clock Driver v1.12ac
[   32.662559] Linux agpgart interface v0.101 (c) Dave Jones
[   32.662561] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.662920] mice: PS/2 mouse device common for all mice
[   32.663310] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.663393] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.663395] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.663626] PNP: No PS/2 controller found. Probing ports directly.
[   32.664515] i8042.c: No controller found.
[   32.664581] TCP bic registered
[   32.664588] NET: Registered protocol family 1
[   32.664592] NET: Registered protocol family 8
[   32.664594] NET: Registered protocol family 20
[   32.664640] ACPI: (supports S0 S1 S4 S5)
[   32.664675] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   32.664692] Freeing unused kernel memory: 188k freed
[   32.698521] vga16fb: initializing
[   32.698524] vga16fb: mapped to 0xffff8100000a0000
[   32.825385] Console: switching to colour frame buffer device 80x25
[   32.825388] fb0: VGA16 VGA frame buffer device
[   33.842631] Capability LSM initialized
[   33.861747] ACPI: Fan [FAN] (on)
[   33.863946] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[   33.863975] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   33.863978] ACPI: Getting cpuindex for acpiid 0x2
[   33.863982] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   33.863984] ACPI: Getting cpuindex for acpiid 0x3
[   33.864740] ACPI: Thermal Zone [THRM] (-73 C)
[   34.076980] ICH7: IDE controller at PCI slot 0000:00:1f.1
[   34.076992] GSI 17 sharing vector 0xD1 and IRQ 17
[   34.076994] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 209
[   34.077002] ICH7: chipset revision 1
[   34.077004] ICH7: not 100% native mode: will probe irqs later
[   34.077011]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:pio
[   34.077018] Probing IDE interface ide0...
[   34.815931] hda: HL-DT-ST DVDRAM GSA-H12N, ATAPI CD/DVD-ROM drive
[   35.150709] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   35.160173] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.160180] Uniform CD-ROM driver Revision: 3.20
[   35.247074] SCSI subsystem initialized
[   35.249172] libata version 1.20 loaded.
[   35.249813] ata_piix 0000:00:1f.2: version 1.05
[   35.249831] GSI 18 sharing vector 0xD9 and IRQ 18
[   35.249833] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 217
[   35.249845] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   35.249869] ata1: SATA max UDMA/133 cmd 0xFA00 ctl 0xF902 bmdma 0xF600 irq 217
[   35.249884] ata2: SATA max UDMA/133 cmd 0xF800 ctl 0xF702 bmdma 0xF608 irq 217
[   35.418730] ata1: disabling port
[   35.418733] scsi0 : ata_piix
[   35.581225] ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:207f
[   35.581227] ata2: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[   35.589301] ata2: dev 0 configured for UDMA/133
[   35.589314] scsi1 : ata_piix
[   35.589444]   Vendor: ATA       Model: ST3250824AS       Rev: 3.AA
[   35.589452]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   35.593200] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   35.593208] sda: Write Protect is off
[   35.593209] sda: Mode Sense: 00 3a 00 00
[   35.593220] SCSI device sda: drive cache: write back
[   35.593251] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   35.593258] sda: Write Protect is off
[   35.593259] sda: Mode Sense: 00 3a 00 00
[   35.593270] SCSI device sda: drive cache: write back
[   35.593272]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[   35.633514] sd 1:0:0:0: Attached scsi disk sda
[   35.995420] Probing IDE interface ide1...
[   36.005297] usbcore: registered new driver usbfs
[   36.005310] usbcore: registered new driver hub
[   36.005842] USB Universal Host Controller Interface driver v3.0
[   36.005879] GSI 19 sharing vector 0xE1 and IRQ 19
[   36.005882] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 225
[   36.005889] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   36.005892] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   36.005971] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   36.005993] uhci_hcd 0000:00:1d.0: irq 225, io base 0x0000ff00
[   36.006043] usb usb1: configuration #1 chosen from 1 choice
[   36.006056] hub 1-0:1.0: USB hub found
[   36.006060] hub 1-0:1.0: 2 ports detected
[   36.031452] ieee1394: Initialized config rom entry `ip1394'
[   36.109435] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[   36.109443] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   36.109447] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   36.109520] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   36.109541] uhci_hcd 0000:00:1d.1: irq 217, io base 0x0000fe00
[   36.109647] usb usb2: configuration #1 chosen from 1 choice
[   36.109721] hub 2-0:1.0: USB hub found
[   36.109725] hub 2-0:1.0: 2 ports detected
[   36.214285] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[   36.214292] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   36.214296] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   36.214394] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   36.214415] uhci_hcd 0000:00:1d.2: irq 209, io base 0x0000fd00
[   36.214518] usb usb3: configuration #1 chosen from 1 choice
[   36.214591] hub 3-0:1.0: USB hub found
[   36.214595] hub 3-0:1.0: 2 ports detected
[   36.319007] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[   36.319013] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   36.319017] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   36.319115] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   36.319136] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000fc00
[   36.319244] usb usb4: configuration #1 chosen from 1 choice
[   36.319319] hub 4-0:1.0: USB hub found
[   36.319323] hub 4-0:1.0: 2 ports detected
[   36.350994] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   36.423552] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 225
[   36.424493] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   36.424497] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   36.424536] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   36.424569] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   36.424575] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xfdfff000
[   36.428463] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.429106] usb usb5: configuration #1 chosen from 1 choice
[   36.429121] hub 5-0:1.0: USB hub found
[   36.429126] hub 5-0:1.0: 8 ports detected
[   36.532264] ACPI: PCI Interrupt 0000:04:0a.0[A] -> GSI 18 (level, low) -> IRQ 209
[   36.532271] PCI: Via IRQ fixup for 0000:04:0a.0, from 10 to 1
[   36.532291] PCI: Setting latency timer of device 0000:04:0a.0 to 64
[   36.585394] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[209]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   36.614589] Attempting manual resume
[   36.652058] kjournald starting.  Commit interval 5 seconds
[   36.652068] EXT3-fs: mounted filesystem with ordered data mode.
[   36.882609] usb 1-2: device not accepting address 2, error -71
[   37.435757] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   37.584851] usb 5-2: configuration #1 chosen from 1 choice
[   37.828363] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   37.864928] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00301bbc000005f4]
[   37.961876] usb 5-5: configuration #1 chosen from 1 choice
[   37.961973] hub 5-5:1.0: USB hub found
[   37.962079] hub 5-5:1.0: 4 ports detected
[   38.454718] usb 5-5.3: new high speed USB device using ehci_hcd and address 5
[   38.548507] usb 5-5.3: configuration #1 chosen from 1 choice
[   38.790283] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   38.977202] usb 4-2: configuration #1 chosen from 1 choice
[   43.761351] FDC 0 is a post-1991 82077
[   43.769029] input: PC Speaker as /class/input/input0
[   43.811637] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.816559] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.896596] hw_random hardware driver 1.0.0 loaded
[   44.361209] tg3.c:v3.59.1 (August 25, 2006)
[   44.361227] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[   44.361235] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   44.398811] usbcore: registered new driver hiddev
[   44.404449] eth0: Tigon3 [partno(BCM95789) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:30:1b:bc:05:90
[   44.404454] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[   44.404456] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   44.417470] input: Logitech USB Receiver as /class/input/input1
[   44.417504] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-2
[   44.449405] input: Logitech USB Receiver as /class/input/input2
[   44.449459] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2
[   44.449469] usbcore: registered new driver usbhid
[   44.449472] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   44.468327] ieee80211_crypt: registered algorithm 'NULL'
[   44.469819] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   44.469821] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   44.517041] PM: Writing back config space on device 0000:03:00.0 at offset c (was fffc0000, writing 0)
[   44.683500] usbcore: registered new driver libusual
[   44.699342] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   44.746246] Initializing USB Mass Storage driver...
[   44.746301] scsi2 : SCSI emulation for USB Mass Storage devices
[   44.746342] usb-storage: device found at 2
[   44.746344] usb-storage: waiting for device to settle before scanning
[   44.746347] usbcore: registered new driver usb-storage
[   44.746350] USB Mass Storage support registered.
[   44.760607] nvidia: module license 'NVIDIA' taints kernel.
[   44.763620] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[   44.763628] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   44.763739] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8776  Mon Oct 16 21:53:43 PDT 2006
[   45.075821] ts: Compaq touchscreen protocol output
[   45.148614] zd1211rw 5-5.3:1.0: firmware version 4605
[   45.168347] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[   45.169070] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   45.190563] zd1211rw 5-5.3:1.0: zd1211 chip 07b8:6001 v4330 high 00-12-0e AL2230_RF pa0 g--
[   45.193069] zd1211rw 5-5.3:1.0: eth1
[   45.193080] usbcore: registered new driver zd1211rw
[   45.556296] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   45.717454] NET: Registered protocol family 17
[   45.920716] lp: driver loaded but no devices found
[   45.943268] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   45.943270] ieee1394: sbp2: Try serialize_io=0 for better performance
[   45.960614] Adding 2730976k swap on /dev/disk/by-uuid/fbf1ec5a-7fac-4ea2-8bf5-ac2ad3896835.  Priority:-1 extents:1 across:2730976k
[   45.996377] EXT3 FS on sda4, internal journal
[   46.303631] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   46.303634] tg3: eth0: Flow control is off for TX and off for RX.
[   49.741948] usb-storage: device scan complete
[   49.745531]   Vendor: USB2.0    Model: CF  CardReader    Rev: 9144
[   49.745539]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   49.749334]   Vendor: USB2.0    Model: SM  CardReader    Rev: 9144
[   49.749341]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   49.753329]   Vendor: USB2.0    Model: SD  CardReader    Rev: 9144
[   49.753336]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   49.756984]   Vendor: USB2.0    Model: MS  CardReader    Rev: 9144
[   49.756992]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   49.771641] sd 2:0:0:0: Attached scsi removable disk sdb
[   49.771675] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   49.774651] sd 2:0:0:1: Attached scsi removable disk sdc
[   49.774680] sd 2:0:0:1: Attached scsi generic sg2 type 0
[   49.777772] sd 2:0:0:2: Attached scsi removable disk sdd
[   49.777797] sd 2:0:0:2: Attached scsi generic sg3 type 0
[   49.780772] sd 2:0:0:3: Attached scsi removable disk sde
[   49.780797] sd 2:0:0:3: Attached scsi generic sg4 type 0
[   50.847533] ACPI: Power Button (FF) [PWRF]
[   50.847542] ACPI: Power Button (CM) [PWRB]
[   50.918949] ibm_acpi: ec object not found
[   50.945536] pcc_acpi: loading...
[   51.234153] acpi-cpufreq: CPU0 - ACPI performance management activated.
[   51.234468] acpi-cpufreq: CPU1 - ACPI performance management activated.
[   55.497250] Bluetooth: Core ver 2.8
[   55.497254] NET: Registered protocol family 31
[   55.497255] Bluetooth: HCI device and connection manager initialized
[   55.497267] Bluetooth: HCI socket layer initialized
[   55.509331] Bluetooth: L2CAP ver 2.8
[   55.509334] Bluetooth: L2CAP socket layer initialized
[   55.514061] Bluetooth: RFCOMM socket layer initialized
[   55.514073] Bluetooth: RFCOMM TTY layer initialized
[   55.514075] Bluetooth: RFCOMM ver 1.7
[   56.205191] NET: Registered protocol family 10
[   56.205285] lo: Disabled Privacy Extensions
[   56.205371] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   56.205399] IPv6 over IPv4 tunneling driver
[   66.889833] eth0: no IPv6 routers present


ANybody knows if there is a kernel patch to resolve this error ?
At the momment what it's better for intel  core 2 duo, ubuntu x86 or ubuntu x64?


TIA

---

### Post by Sef on 2007-01-03
> At the momment what it's better for intel core 2 duo, ubuntu x86 or ubuntu x64?

I would stick with the x86 right now.  It is 32-bit and so less problems installing things like flash.

---

