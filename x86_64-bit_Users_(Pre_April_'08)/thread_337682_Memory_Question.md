---
title: "Memory Question"
date: 2007-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlacroix on 2007-01-13
Hello, I have a 64-bit AMD-based PC with 512MB of DDR2 RAM. I bought some more RAM today (another 512MB stick) and now I should have 1GB. But I don't. Instead my bios reads the RAM as 1019MB, and KInfoCenter says I have 997.88MB. I disabled my shared video ram (I have an onboard video card but I use an Nvidia video card instead) and it still only reads as I said above.

I know it might sound petty that I'm worried about a tiny margin of ram, but I want it tall. Do any of you have any ideas on what could be using the other part of my RAM?

---

### Post by cylon359 on 2007-01-14
Your BIOS might have reserved some of it?

---

### Post by jlacroix on 2007-01-14
Do you know of any way I can find out?

---

### Post by wesley_of_course on 2007-01-14
Wesley here ;   

          command ;     free -m

---

### Post by cylon359 on 2007-01-14
One of the first thing the kernel writes to its log is the BIOS memory map... on one of my systems, there is reserved space, and other space used by ACPI:

[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe5c000 (usable)
[    0.000000]  BIOS-e820: 000000007fe5c000 - 000000007fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee9000 - 000000007feed000 (usable)
[    0.000000]  BIOS-e820: 000000007feed000 - 000000007feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007feff000 - 000000007ff00000 (usable)

That's probably where you memory is... so you can't reclaim it.

---

### Post by jlacroix on 2007-01-15
I'll check those things when I get home. :)

Hopefully that will answer it.

---

### Post by jlacroix on 2007-01-15
BTW, thanks to everyone in advance.

---

### Post by jlacroix on 2007-01-15
ACPI NVS shows up on mine, does that mean that's definitely where the RAM is?

---

### Post by jlacroix on 2007-01-15
I almost forgot, here is my dmesg:
```

[    0.000000] Bootdata ok (command line is root=/dev/hdb1 ro quiet splash)
[    0.000000] Linux version 2.6.17-10-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 21:16:35 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003faf0000 (usable)
[    0.000000]  BIOS-e820: 000000003faf0000 - 000000003faf3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003faf3000 - 000000003fb00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 K8M890                                ) @ 0x00000000000f7c70
[    0.000000] ACPI: RSDT (v001 K8M890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003faf3040
[    0.000000] ACPI: FADT (v001 K8M890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003faf30c0
[    0.000000] ACPI: MCFG (v001 K8M890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003faf9980
[    0.000000] ACPI: MADT (v001 K8M890 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003faf98c0
[    0.000000] ACPI: DSDT (v001 K8M890 AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003faf0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003faf0000
[    0.000000] On node 0 totalpages: 255819
[    0.000000]   DMA zone: 2577 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 253242 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3fb00000:a0500000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ c8000000 size 128 MB
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hdb1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 1600.049 MHz processor.
[   34.483329] Console: colour VGA+ 80x25
[   34.484057] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   34.485244] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   34.498453] Memory: 1015936k/1043392k available (2129k kernel code, 27068k reserved, 1424k data, 188k init)
[   34.575365] Calibrating delay using timer specific routine.. 3202.07 BogoMIPS (lpj=6404140)
[   34.575428] Security Framework v1.0.0 initialized
[   34.575434] SELinux:  Disabled at boot.
[   34.575459] Mount-cache hash table entries: 256
[   34.575612] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   34.575616] CPU: L2 Cache: 128K (64 bytes/line)
[   34.575620] CPU 0/0(1) -> Node 0 -> Core 0
[   34.575637] SMP alternatives: switching to UP code
[   34.575901] checking if image is initramfs... it is
[   35.182348] Freeing initrd memory: 5707k freed
[   35.186237] ACPI: Core revision 20060707
[   35.190447] ACPI: Looking for DSDT ... not found!
[   35.236531] Using local APIC timer interrupts.
[   35.298940] result 12500397
[   35.298942] Detected 12.500 MHz APIC timer.
[   35.302323] Brought up 1 CPUs
[   35.302366] testing NMI watchdog ... OK.
[   35.342380] migration_cost=0
[   35.342671] NET: Registered protocol family 16
[   35.342701] ACPI: bus type pci registered
[   35.346699] PCI: Using MMCONFIG at e0000000
[   35.346737] PCI: No mmconfig possible on device 0:18
[   35.359222] ACPI: Interpreter enabled
[   35.359227] ACPI: Using IOAPIC for interrupt routing
[   35.359931] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.359936] PCI: Probing PCI hardware (bus 00)
[   35.365400] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[   35.366511] Boot video device is 0000:05:05.0
[   35.366548] PCI: Transparent bridge - 0000:00:13.1
[   35.366624] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.475749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[   35.476547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   35.477501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PE._PRT]
[   35.478421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[   35.479151] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   35.479670] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   35.480195] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   35.480714] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
[   35.481190] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   35.481662] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   35.482142] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   35.482640] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 *11 12)
[   35.486485] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.486499] pnp: PnP ACPI init
[   35.494156] pnp: PnP ACPI: found 15 devices
[   35.494222] PCI: Using ACPI for IRQ routing
[   35.494226] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   35.494458] PCI-DMA: Disabling IOMMU.
[   35.495195] pnp: 00:01: ioport range 0x400-0x47f could not be reserved
[   35.495200] pnp: 00:01: ioport range 0x500-0x50f has been reserved
[   35.495439] PCI: Bridge: 0000:00:01.0
[   35.495444]   IO window: e000-efff
[   35.495449]   MEM window: dd000000-deffffff
[   35.495454]   PREFETCH window: b0000000-bfffffff
[   35.495458] PCI: Bridge: 0000:00:02.0
[   35.495461]   IO window: d000-dfff
[   35.495466]   MEM window: dfc00000-dfcfffff
[   35.495470]   PREFETCH window: dfb00000-dfbfffff
[   35.495474] PCI: Bridge: 0000:00:03.0
[   35.495477]   IO window: c000-cfff
[   35.495482]   MEM window: dfe00000-dfefffff
[   35.495487]   PREFETCH window: dfd00000-dfdfffff
[   35.495492] PCI: Bridge: 0000:00:13.0
[   35.495495]   IO window: b000-bfff
[   35.495500]   MEM window: dfa00000-dfafffff
[   35.495504]   PREFETCH window: df900000-df9fffff
[   35.495510] PCI: Bridge: 0000:00:13.1
[   35.495514]   IO window: a000-afff
[   35.495519]   MEM window: db000000-dcffffff
[   35.495523]   PREFETCH window: d0000000-d7ffffff
[   35.495539] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   35.495557] GSI 16 sharing vector 0xA9 and IRQ 16
[   35.495562] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 169
[   35.495567] PCI: Via IRQ fixup for 0000:00:02.0, from 11 to 9
[   35.495588] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   35.495601] GSI 17 sharing vector 0xB1 and IRQ 17
[   35.495605] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 177
[   35.495611] PCI: Via IRQ fixup for 0000:00:03.0, from 11 to 1
[   35.495631] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   35.495643] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   35.495654] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   35.495700] NET: Registered protocol family 2
[   35.533984] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   35.534265] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   35.535718] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   35.536521] TCP: Hash tables configured (established 131072 bind 65536)
[   35.536525] TCP reno registered
[   35.536945] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   35.537346] audit: initializing netlink socket (disabled)
[   35.537362] audit(1168864005.060:1): initialized
[   35.537526] VFS: Disk quotas dquot_6.5.1
[   35.537554] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   35.537606] Initializing Cryptographic API
[   35.537612] io scheduler noop registered
[   35.537622] io scheduler anticipatory registered
[   35.537630] io scheduler deadline registered
[   35.537648] io scheduler cfq registered (default)
[   35.538011] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 169
[   35.538020] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   35.538053] assign_interrupt_mode Found MSI capability
[   35.538114] Allocate Port Service[0000:00:02.0:pcie00]
[   35.538159] Allocate Port Service[0000:00:02.0:pcie01]
[   35.538193] Allocate Port Service[0000:00:02.0:pcie02]
[   35.538222] Allocate Port Service[0000:00:02.0:pcie03]
[   35.538262] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 177
[   35.538269] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   35.538308] assign_interrupt_mode Found MSI capability
[   35.538357] Allocate Port Service[0000:00:03.0:pcie00]
[   35.538392] Allocate Port Service[0000:00:03.0:pcie01]
[   35.538420] Allocate Port Service[0000:00:03.0:pcie02]
[   35.538449] Allocate Port Service[0000:00:03.0:pcie03]
[   35.580611] Real Time Clock Driver v1.12ac
[   35.580656] Linux agpgart interface v0.101 (c) Dave Jones
[   35.580659] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.580785] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.581071] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.581941] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.582322] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.582660] mice: PS/2 mouse device common for all mice
[   35.583216] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.583447] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.583452] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.583740] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   35.583744] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   35.583975] serio: i8042 AUX port at 0x60,0x64 irq 12
[   35.583991] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.584241] TCP bic registered
[   35.584258] NET: Registered protocol family 1
[   35.584266] NET: Registered protocol family 8
[   35.584268] NET: Registered protocol family 20
[   35.584481] ACPI: (supports S0 S1 S4 S5)
[   35.584530] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   35.584554] Freeing unused kernel memory: 188k freed
[   35.630060] input: AT Translated Set 2 keyboard as /class/input/input0
[   35.658146] vga16fb: initializing
[   35.658154] vga16fb: mapped to 0xffff8100000a0000
[   35.827398] Console: switching to colour frame buffer device 80x25
[   35.827408] fb0: VGA16 VGA frame buffer device
[   36.913394] Capability LSM initialized
[   36.961065] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   36.961072] ACPI: Getting cpuindex for acpiid 0x1
[   37.536219] SCSI subsystem initialized
[   37.540548] libata version 1.20 loaded.
[   37.541902] sata_via 0000:00:0f.0: version 1.1
[   37.541924] GSI 18 sharing vector 0xD1 and IRQ 18
[   37.541929] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 209
[   37.541934] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 1
[   37.541965] sata_via 0000:00:0f.0: routed to hard irq line 1
[   37.542015] ata1: SATA max UDMA/133 cmd 0xFF00 ctl 0xFE02 bmdma 0xFB00 irq 209
[   37.542036] ata2: SATA max UDMA/133 cmd 0xFD00 ctl 0xFC02 bmdma 0xFB08 irq 209
[   37.709259] scsi0 : sata_via
[   37.876996] scsi1 : sata_via
[   37.891831] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   37.891850] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 0
[   37.891876] VP_IDE: chipset revision 7
[   37.891878] VP_IDE: not 100% native mode: will probe irqs later
[   37.891891] VP_IDE: VIA vt8237a (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   37.891899]     ide0: BM-DMA at 0xfa00-0xfa07, BIOS settings: hda:DMA, hdb:DMA
[   37.891914]     ide1: BM-DMA at 0xfa08-0xfa0f, BIOS settings: hdc:DMA, hdd:pio
[   37.891926] Probing IDE interface ide0...
[   38.313732] hda: WDC WD200EB-11CSF0, ATA DISK drive
[   38.597293] hdb: ST380011A, ATA DISK drive
[   38.659562] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   38.675261] Probing IDE interface ide1...
[   39.539845] hdc: LITE-ON DVDRW LH-16W1P, ATAPI CD/DVD-ROM drive
[   40.215378] ide1 at 0x170-0x177,0x376 on irq 15
[   40.235250] hda: max request size: 128KiB
[   40.248873] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[   40.248882] hda: cache flushes not supported
[   40.248926]  hda: hda1 hda2
[   40.265557] hdb: max request size: 512KiB
[   40.265917] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   40.266041] hdb: cache flushes supported
[   40.266077]  hdb: hdb1 hdb2 < hdb5 >
[   40.337219] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   40.337229] Uniform CD-ROM driver Revision: 3.20
[   40.868578] usbcore: registered new driver usbfs
[   40.868602] usbcore: registered new driver hub
[   40.869779] USB Universal Host Controller Interface driver v3.0
[   40.869844] GSI 19 sharing vector 0xD9 and IRQ 19
[   40.869849] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 217
[   40.869855] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 9
[   40.869881] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   40.870056] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   40.870087] uhci_hcd 0000:00:10.0: irq 217, io base 0x0000f900
[   40.870180] usb usb1: configuration #1 chosen from 1 choice
[   40.870204] hub 1-0:1.0: USB hub found
[   40.870212] hub 1-0:1.0: 2 ports detected
[   40.977840] GSI 20 sharing vector 0xE1 and IRQ 20
[   40.977846] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 225
[   40.977852] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 1
[   40.977879] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   40.978048] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   40.978078] uhci_hcd 0000:00:10.1: irq 225, io base 0x0000f800
[   40.978324] usb usb2: configuration #1 chosen from 1 choice
[   40.978482] hub 2-0:1.0: USB hub found
[   40.978496] hub 2-0:1.0: 2 ports detected
[   41.085593] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 209
[   41.085600] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 1
[   41.085626] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   41.085801] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   41.085829] uhci_hcd 0000:00:10.2: irq 209, io base 0x0000f700
[   41.086069] usb usb3: configuration #1 chosen from 1 choice
[   41.086234] hub 3-0:1.0: USB hub found
[   41.086247] hub 3-0:1.0: 2 ports detected
[   41.193454] GSI 21 sharing vector 0xE9 and IRQ 21
[   41.193461] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 233
[   41.193467] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 9
[   41.193492] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   41.193666] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   41.193696] uhci_hcd 0000:00:10.3: irq 233, io base 0x0000f600
[   41.193950] usb usb4: configuration #1 chosen from 1 choice
[   41.194105] hub 4-0:1.0: USB hub found
[   41.194121] hub 4-0:1.0: 2 ports detected
[   41.221152] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   41.310415] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 209
[   41.310423] PCI: Via IRQ fixup for 0000:00:10.4, from 5 to 1
[   41.310501] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   41.310561] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   41.310608] ehci_hcd 0000:00:10.4: irq 209, io mem 0xdffff000
[   41.310616] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   41.310688] usb usb5: configuration #1 chosen from 1 choice
[   41.310714] hub 5-0:1.0: USB hub found
[   41.310721] hub 5-0:1.0: 8 ports detected
[   41.490136] Attempting manual resume
[   41.513693] kjournald starting.  Commit interval 5 seconds
[   41.513706] EXT3-fs: mounted filesystem with ordered data mode.
[   41.756326] usb 1-1: device not accepting address 2, error -71
[   43.313938] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   43.499054] usb 1-1: configuration #1 chosen from 1 choice
[   43.745272] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   43.922384] usb 1-2: configuration #1 chosen from 1 choice
[   50.998973] FDC 0 is a post-1991 82077
[   51.014345] parport: PnPBIOS parport detected.
[   51.014398] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   51.068417] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[   51.068474] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 233
[   51.068481] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 9
[   51.068598] eth0: VIA Rhine II at 0x1f200, 00:16:17:d6:e6:06, IRQ 233.
[   51.069314] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   51.092978] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   51.097572] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   51.356026] input: PC Speaker as /class/input/input1
[   51.707700] Linux video capture interface: v1.00
[   51.804445] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   52.031375] nvidia: module license 'NVIDIA' taints kernel.
[   52.036561] GSI 22 sharing vector 0x32 and IRQ 22
[   52.036567] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 18 (level, low) -> IRQ 50
[   52.036753] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8776  Mon Oct 16 21:53:43 PDT 2006
[   52.376140] usbcore: registered new driver hiddev
[   52.395142] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   52.395202] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-1
[   52.430120] input: THRUSTMASTER 2 in 1 DT as /class/input/input3
[   52.430156] input: USB HID v1.10 Gamepad [THRUSTMASTER 2 in 1 DT] on usb-0000:00:10.0-2
[   52.430174] usbcore: registered new driver usbhid
[   52.430178] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   52.439824] bttv: driver version 0.9.16 loaded
[   52.439829] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   52.439905] bttv: Bt8xx card found (0).
[   52.439959] GSI 23 sharing vector 0x3A and IRQ 23
[   52.439963] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 17 (level, low) -> IRQ 58
[   52.439996] bttv0: Bt878 (rev 17) at 0000:05:04.0, irq: 58, latency: 64, mmio: 0xd7fff000
[   52.440012] bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
[   52.440017] bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
[   52.440053] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   52.441213] bttv0: using tuner=19
[   52.441216] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   52.443344] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   52.445468] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   52.483796] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   52.483801] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   52.483832] tuner 0-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   52.516040] bttv0: registered device video0
[   52.516076] bttv0: registered device vbi0
[   52.516098] bttv0: PLL: 28636363 => 35468950 .. ok
[   52.614545] bt878: AUDIO driver version 0.0.0 loaded
[   52.614589] bt878: Bt878 AUDIO function found (0).
[   52.614609] ACPI: PCI Interrupt 0000:05:04.1[A] -> GSI 17 (level, low) -> IRQ 58
[   52.614617] bt878_probe: card id=[0x31002], Unknown card.
[   52.614619] Exiting..
[   52.614623] ACPI: PCI interrupt for device 0000:05:04.1 disabled
[   52.614627] bt878: probe of 0000:05:04.1 failed with error -22
[   52.843232] NET: Registered protocol family 17
[   52.915406] ts: Compaq touchscreen protocol output
[   53.009001] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 58
[   53.009009] PCI: Via IRQ fixup for 0000:04:01.0, from 11 to 10
[   53.009093] PCI: Setting latency timer of device 0000:04:01.0 to 64
[   53.394449] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   53.795908] lp0: using parport0 (interrupt-driven).
[   53.869569] Adding 1477940k swap on /dev/disk/by-uuid/63a8ef0e-d32f-4421-a6b5-f6d7f82b7246.  Priority:-1 extents:1 across:1477940k
[   53.946007] EXT3 FS on hdb1, internal journal
[   54.249396] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   54.285725] NTFS volume version 3.1.
[   54.334824] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   54.896164] NET: Registered protocol family 10
[   54.896278] lo: Disabled Privacy Extensions
[   54.896431] IPv6 over IPv4 tunneling driver
[   61.741342] ACPI: Power Button (FF) [PWRF]
[   61.741357] ACPI: Power Button (CM) [PWRB]
[   61.864641] ibm_acpi: ec object not found
[   61.895633] pcc_acpi: loading...
[   62.244319] powernow-k8: Power state transitions not supported
[   65.332028] eth0: no IPv6 routers present
[   75.856127] Bluetooth: Core ver 2.8
[   75.856134] NET: Registered protocol family 31
[   75.856136] Bluetooth: HCI device and connection manager initialized
[   75.856152] Bluetooth: HCI socket layer initialized
[   75.900863] Bluetooth: L2CAP ver 2.8
[   75.900868] Bluetooth: L2CAP socket layer initialized
[   76.003170] Bluetooth: RFCOMM socket layer initialized
[   76.003191] Bluetooth: RFCOMM TTY layer initialized
[   76.003194] Bluetooth: RFCOMM ver 1.7
[   92.015347] hda-intel: Invalid position buffer, using LPIB read method instead.

```

---

### Post by cylon359 on 2007-01-17
That would account for a tiny bit of it.  Your available memory is given by these two regions:

[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003faf0000 (usable)

which are 653312 bytes (ie: the historic 640K), and 1067384832 bytes

Add them together, and then if you divide by 1048576 (bytes in a megabyte), you get 1018 MB. which is basically what your BIOS reports.

---

