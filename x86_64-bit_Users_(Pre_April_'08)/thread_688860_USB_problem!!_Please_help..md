---
title: "USB problem!! Please help."
date: 2008-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by terak on 2008-02-05
Okay, so here's the deal.

I installed Ubuntu a few weeks ago and am a pretty green w/ it and with Linux.  I installed it on my 2nd internal harddrive in my laptop (not a partition, laptop has 2 harddrives) and I've managed to work through the forums and have got my wireless network card working, got my touchpad working properly, fixed my boot up speeds, and got my ATI card working like it should.  But now I've run into a problem that I just can't figure out.

My USB has been working just fine since the install.  I turned on 'suspend' mode and when my laptop went to suspend, it wouldn't wake up so I had to do a cold boot (hold down the power button).  Ever since then, none of my USB port work, and I've tried EVERYTHING that I can google.  I've played with setting... I've unplugged the power and left the battery out for the night... anything that I can find, and nothing works. :(  On top of that, when I boot back up into Windows Vista, none of my ports work either.  It gives me a 'device unrecognized' error.  I have a feeling that it has something to do with the USB power settings getting messed up, but I can't figure it out.  There are NO usb settings in my BIOS, I've looked a dozen times and even flashed my BIOS to the latest version.

I need help getting these ports working!

I'm using Ubuntu 7.10 64bit version on a HP dv8110us laptop.

Here's what I get when I run lusb:

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Here's what I get when I run dmesg before plugging anything in:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=7678f372-0b41-4072-9574-f107ea20c43f ro quiet
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fea0000 (usable)
[    0.000000]  BIOS-e820: 000000007fea0000 - 000000007feac000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007feac000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523936) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7C40 checksum 0
[    0.000000] ACPI: RSDP 000F7C40, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 7FEA3ED4, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEABE3B, 0074 (r1 HP     Piranha   6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 7FEA3F08, 7F33 (r1     HP     309B  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEACFC0, 0040
[    0.000000] ACPI: SSDT 7FEABEAF, 00CF (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 7FEABF7E, 0046 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 7FEABFC4, 003C (r1 HP     PORSCHE   6040000 LOHR        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fea0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523936) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fea0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   523936
[    0.000000] On node 0 totalpages: 523839
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7107 pages used for memmap
[    0.000000]   DMA32 zone: 512733 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515551
[    0.000000] Kernel command line: root=UUID=7678f372-0b41-4072-9574-f107ea20c43f ro quiet
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   10.664190] time.c: Detected 1794.824 MHz processor.
[   10.665032] Console: colour VGA+ 80x25
[   10.665050] Checking aperture...
[   10.665054] CPU 0: aperture @ 1f9e000000 size 32 MB
[   10.665056] Aperture too small (32 MB)
[   10.676944] No AGP bridge found
[   10.708280] Memory: 2054296k/2095744k available (2274k kernel code, 41060k reserved, 1181k data, 296k init)
[   10.708341] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.786080] Calibrating delay using timer specific routine.. 3593.29 BogoMIPS (lpj=7186596)
[   10.786121] Security Framework v1.0.0 initialized
[   10.786130] SELinux:  Disabled at boot.
[   10.786316] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   10.788554] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.789648] Mount-cache hash table entries: 256
[   10.789826] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   10.789829] CPU: L2 Cache: 512K (64 bytes/line)
[   10.789833] CPU 0/0 -> Node 0
[   10.789854] SMP alternatives: switching to UP code
[   10.790126] Freeing SMP alternatives: 24k freed
[   10.790614] Early unpacking initramfs... done
[   11.138497] ACPI: Core revision 20070126
[   11.138580] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.817511] Using local APIC timer interrupts.
[   11.873178] result 12464063
[   11.873180] Detected 12.464 MHz APIC timer.
[   11.877148] Brought up 1 CPUs
[   11.877366] NET: Registered protocol family 16
[   11.877453] ACPI: bus type pci registered
[   11.877461] PCI: Using configuration type 1
[   11.878226] ACPI: EC: Look up EC in DSDT
[   11.878950] ACPI: EC: GPE=0x1a, ports=0x66, 0x62
[   11.879977] ACPI: Interpreter enabled
[   11.879980] ACPI: (supports S0 S3 S4 S5)
[   11.879994] ACPI: Using IOAPIC for interrupt routing
[   11.925705] ACPI: EC: GPE=0x1a, ports=0x66, 0x62
[   11.925744] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.925752] PCI: Probing PCI hardware (bus 00)
[   11.927206] PCI: Transparent bridge - 0000:00:14.4
[   11.927309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.927441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   11.927553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   11.927667] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   11.929486] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   11.929589] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   11.929689] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   11.929788] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   11.929888] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   11.929987] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   11.930092] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   11.930191] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   11.930271] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.930286] pnp: PnP ACPI init
[   11.930295] ACPI: bus type pnp registered
[   11.953099] pnp: PnP ACPI: found 10 devices
[   11.953102] ACPI: ACPI bus type pnp unregistered
[   11.953161] PCI: Using ACPI for IRQ routing
[   11.953164] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.953172] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[   11.953218] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[   11.953374] NET: Registered protocol family 8
[   11.953376] NET: Registered protocol family 20
[   11.953497] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   11.953501] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   11.953505] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   11.953513] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   11.953516] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   11.953519] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   11.953522] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   11.953525] pnp: 00:08: ioport range 0x870-0x87f has been reserved
[   11.953531] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   11.953534] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   11.953537] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   11.953823] PCI: Bridge: 0000:00:01.0
[   11.953826]   IO window: 9000-9fff
[   11.953830]   MEM window: c0100000-c01fffff
[   11.953833]   PREFETCH window: c8000000-cfffffff
[   11.953836] PCI: Bridge: 0000:00:04.0
[   11.953838]   IO window: disabled.
[   11.953840]   MEM window: disabled.
[   11.953842]   PREFETCH window: disabled.
[   11.953848] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[   11.953850]   IO window: 0000a400-0000a4ff
[   11.953856]   IO window: 0000a800-0000a8ff
[   11.953862]   PREFETCH window: 88000000-8bffffff
[   11.953868]   MEM window: 8c000000-8fffffff
[   11.953874] PCI: Bridge: 0000:00:14.4
[   11.953878]   IO window: a000-afff
[   11.953884]   MEM window: c0200000-c02fffff
[   11.953890]   PREFETCH window: 88000000-8bffffff
[   11.953909] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   11.953939] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 20
[   11.953994] NET: Registered protocol family 2
[   11.957023] Time: tsc clocksource has been installed.
[   11.989089] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   11.989979] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   11.996511] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   11.997597] TCP: Hash tables configured (established 262144 bind 65536)
[   11.997601] TCP reno registered
[   12.009142] checking if image is initramfs... it is
[   12.680495] Freeing initrd memory: 7745k freed
[   12.689230] audit: initializing netlink socket (disabled)
[   12.689245] audit(1202238466.344:1): initialized
[   12.691228] VFS: Disk quotas dquot_6.5.1
[   12.691286] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   12.691397] io scheduler noop registered
[   12.691399] io scheduler anticipatory registered
[   12.691401] io scheduler deadline registered
[   12.691489] io scheduler cfq registered (default)
[   12.691497] PCI: MSI quirk detected. MSI deactivated.
[   12.692132] Boot video device is 0000:01:05.0
[   12.692295] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   12.692315] assign_interrupt_mode Found MSI capability
[   12.692320] Allocate Port Service[0000:00:04.0:pcie00]
[   12.716055] Real Time Clock Driver v1.12ac
[   12.716150] Linux agpgart interface v0.102 (c) Dave Jones
[   12.716153] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.716736] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   12.716745] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   12.717283] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.717482] input: Macintosh mouse button emulation as /class/input/input0
[   12.717554] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   12.738834] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.738841] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.739056] mice: PS/2 mouse device common for all mice
[   12.739201] TCP cubic registered
[   12.740101] NET: Registered protocol family 1
[   12.740338] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.740346] Freeing unused kernel memory: 296k freed
[   12.772350] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.905594] AppArmor: AppArmor initialized<5>audit(1202238466.560:2):  type=1505 info="AppArmor initialized" pid=1184
[   12.912994] fuse init (API version 7.8)
[   12.917538] Failure registering capabilities with primary security module.
[   12.936748] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.936755] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.945291] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   12.946539] ACPI: Thermal Zone [THRM] (0 C)
[   13.548776] usbcore: registered new interface driver usbfs
[   13.548807] usbcore: registered new interface driver hub
[   13.548830] usbcore: registered new device driver usb
[   13.549587] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.549632] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   13.549778] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   13.549975] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   13.550000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   13.593951] SCSI subsystem initialized
[   13.599394] libata version 2.21 loaded.
[   13.637243] usb usb1: configuration #1 chosen from 1 choice
[   13.637273] hub 1-0:1.0: USB hub found
[   13.637287] hub 1-0:1.0: 4 ports detected
[   13.691104] 8139too Fast Ethernet driver 0.9.28
[   13.739602] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   13.739757] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   13.739826] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   13.739847] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   13.799557] usb usb2: configuration #1 chosen from 1 choice
[   13.799587] hub 2-0:1.0: USB hub found
[   13.799601] hub 2-0:1.0: 4 ports detected
[   13.815356] Marking TSC unstable due to possible TSC halt in C2
[   13.815368] Time: acpi_pm clocksource has been installed.
[   13.903567] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   13.903732] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   13.903794] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   13.903859] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   13.903872] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.903969] usb usb3: configuration #1 chosen from 1 choice
[   13.903998] hub 3-0:1.0: USB hub found
[   13.904006] hub 3-0:1.0: 8 ports detected
[   14.012284] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.012291] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.013307] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   14.013329] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.013342] ATIIXP: chipset revision 0
[   14.013344] ATIIXP: not 100% native mode: will probe irqs later
[   14.013354]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:DMA
[   14.013370]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   14.013380] Probing IDE interface ide0...
[   14.299360] hda: ST9160821A, ATA DISK drive
[   14.579110] hdb: HTS541080G9AT00, ATA DISK drive
[   14.634647] hda: selected mode 0x45
[   14.635222] hdb: selected mode 0x45
[   14.635507] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   14.688308] Probing IDE interface ide1...
[   15.422397] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[   15.757652] hdc: selected mode 0x22
[   15.758562] ide1 at 0x170-0x177,0x376 on irq 15
[   15.762425] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 23 (level, low) -> IRQ 23
[   15.813907] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[c0209000-c02097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   15.819622] hda: max request size: 512KiB
[   15.819740] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[   15.820628] eth0: RealTek RTL8139 at 0xffffc20000ab2400, 00:0f:b0:f5:c8:5b, IRQ 22
[   15.820632] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   15.822417] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   15.834875] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[   15.836285] hda: cache flushes supported
[   15.836336]  hda: hda1 hda2
[   15.888850] hdb: max request size: 128KiB
[   15.889123] hdb: 156301488 sectors (80026 MB) w/7539KiB Cache, CHS=65535/16/63, UDMA(100)
[   15.889389] hdb: cache flushes supported
[   15.889417]  hdb: hdb1 hdb2 < hdb5 >
[   15.944682] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[   15.944693] Uniform CD-ROM driver Revision: 3.20
[   16.392868] Attempting manual resume
[   16.392872] swsusp: Resume From Partition 3:69
[   16.392874] PM: Checking swsusp image.
[   16.393099] PM: Resume from disk failed.
[   16.433490] kjournald starting.  Commit interval 5 seconds
[   16.433502] EXT3-fs: mounted filesystem with ordered data mode.
[   26.071244] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.231827] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.265319] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   26.866589] Yenta: CardBus bridge found at 0000:06:04.0 [103c:309b]
[   26.866617] Yenta: Enabling burst memory read transactions
[   26.866623] Yenta: Using INTVAL to route CSC interrupts to PCI
[   26.866625] Yenta: Routing CardBus interrupts to ISA
[   26.866632] Yenta TI: socket 0000:06:04.0, mfunc 0x00a61b22, devctl 0x64
[   26.881745] input: PC Speaker as /class/input/input2
[   26.919332] ieee80211_crypt: registered algorithm 'NULL'
[   26.921995] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   26.921999] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.989038] sdhci: Secure Digital Host Controller Interface driver
[   26.989042] sdhci: Copyright(c) Pierre Ossman
[   27.014148] bcm43xx driver
[   27.096296] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
[   27.096302] Socket status: 30000006
[   27.096307] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   27.096311] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   27.096314] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   27.100946] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
[   27.100972] ACPI: PCI Interrupt 0000:06:04.4[A] -> GSI 20 (level, low) -> IRQ 20
[   27.101276] mmc0: SDHCI at 0xc020a000 irq 20 DMA
[   27.105537] mmc1: SDHCI at 0xc0209c00 irq 20 DMA
[   27.105756] mmc2: SDHCI at 0xc0209800 irq 20 DMA
[   27.115161] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   27.223406] MC'97 0 converters and GPIO not ready (0x1)
[   27.224207] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[   27.234142] ACPI: PCI Interrupt 0000:06:04.3[B] -> GSI 23 (level, low) -> IRQ 23
[   27.389418] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   27.625493] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   27.689437] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   28.635089] lp: driver loaded but no devices found
[   28.701653] usbcore: registered new interface driver libusual
[   28.707298] Initializing USB Mass Storage driver...
[   28.709066] usbcore: registered new interface driver usb-storage
[   28.709072] USB Mass Storage support registered.
[   28.756538] Adding 3229024k swap on /dev/hdb5.  Priority:-1 extents:1 across:3229024k
[   29.076087] EXT3 FS on hdb1, internal journal
[   30.998369] No dock devices found.
[   31.111909] ACPI: Battery Slot [BAT1] (battery present)
[   31.156529] input: Power Button (FF) as /class/input/input4
[   31.161238] ACPI: Power Button (FF) [PWRF]
[   31.189349] input: Sleep Button (FF) as /class/input/input5
[   31.193976] ACPI: Sleep Button (FF) [SLPF]
[   31.222223] input: Lid Switch as /class/input/input6
[   31.226863] ACPI: Lid Switch [LID]
[   31.255013] input: Power Button (CM) as /class/input/input7
[   31.259655] ACPI: Power Button (CM) [PWRB]
[   31.290107] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.378669] ACPI: AC Adapter [ACAD] (on-line)
[   31.590868] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (version 2.00.00)
[   31.590910] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[   31.590913] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   31.590916] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[   31.592693] powernow-k8: ph2 null fid transition 0xa
[   32.710745] ppdev: user-space parallel port driver
[   32.882343] eth0: link down
[   33.595862] audit(1202260088.071:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4780 profile="/usr/sbin/cupsd"
[   34.057968] Failure registering capabilities with primary security module.
[   34.441465] Bluetooth: Core ver 2.11
[   34.441587] NET: Registered protocol family 31
[   34.441589] Bluetooth: HCI device and connection manager initialized
[   34.441594] Bluetooth: HCI socket layer initialized
[   34.462309] Bluetooth: L2CAP ver 2.8
[   34.462314] Bluetooth: L2CAP socket layer initialized
[   34.649461] Bluetooth: RFCOMM socket layer initialized
[   34.649538] Bluetooth: RFCOMM TTY layer initialized
[   34.649541] Bluetooth: RFCOMM ver 1.8
[   35.430282] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   35.433733] [fglrx] Maximum main memory to use for locked dma buffers: 1887 MBytes.
[   35.433952] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   35.444006] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   36.721032] [fglrx] total      GART = 130023424
[   36.721040] [fglrx] free       GART = 114032640
[   36.721042] [fglrx] max single GART = 114032640
[   36.721045] [fglrx] total      LFB  = 134217728
[   36.721047] [fglrx] free       LFB  = 116002816
[   36.721049] [fglrx] max single LFB  = 116002816
[   36.721051] [fglrx] total      Inv  = 0
[   36.721053] [fglrx] free       Inv  = 0
[   36.721054] [fglrx] max single Inv  = 0
[   36.721056] [fglrx] total      TIM  = 0
[   55.408600] NET: Registered protocol family 17
[   55.658211] ieee80211_crypt: registered algorithm 'WEP'
[   57.110563] NET: Registered protocol family 10
[   57.385722] lo: Disabled Privacy Extensions
[   57.385851] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.385866] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   57.389576] SoftMAC: Open Authentication completed with 00:16:b6:2f:e7:59
[   57.401225] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   73.221341] eth1: no IPv6 routers present
```

And now here is what I get after I plug a USB device in (ie. thumb drive, wireless mouse receiver, harddrive, etc):

```
[  335.581707] usb 3-1: new high speed USB device using ehci_hcd and address 2
[  335.638956] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  335.638961] hub 3-0:1.0: hub_port_status failed (err = -32)
[  335.842772] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  335.842776] hub 3-0:1.0: hub_port_status failed (err = -32)
[  336.046597] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  336.046607] hub 3-0:1.0: hub_port_status failed (err = -32)
[  336.250405] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  336.250410] hub 3-0:1.0: hub_port_status failed (err = -32)
[  336.454229] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  336.454238] hub 3-0:1.0: hub_port_status failed (err = -32)
[  336.454241] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  336.510173] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  336.510177] hub 3-0:1.0: hub_port_status failed (err = -32)
[  336.713997] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  336.714006] hub 3-0:1.0: hub_port_status failed (err = -32)
[  336.917807] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  336.917855] hub 3-0:1.0: hub_port_status failed (err = -32)
[  337.121628] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  337.121637] hub 3-0:1.0: hub_port_status failed (err = -32)
[  337.325448] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  337.325458] hub 3-0:1.0: hub_port_status failed (err = -32)
[  337.325461] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  337.381387] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  337.381391] hub 3-0:1.0: hub_port_status failed (err = -32)
[  337.585204] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  337.585208] hub 3-0:1.0: hub_port_status failed (err = -32)
[  337.789022] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  337.789026] hub 3-0:1.0: hub_port_status failed (err = -32)
[  337.992849] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  337.992858] hub 3-0:1.0: hub_port_status failed (err = -32)
[  338.196658] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  338.196663] hub 3-0:1.0: hub_port_status failed (err = -32)
[  338.196665] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  338.252606] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  338.252609] hub 3-0:1.0: hub_port_status failed (err = -32)
[  338.456432] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  338.456441] hub 3-0:1.0: hub_port_status failed (err = -32)
[  338.660239] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  338.660243] hub 3-0:1.0: hub_port_status failed (err = -32)
[  338.864058] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  338.864062] hub 3-0:1.0: hub_port_status failed (err = -32)
[  339.067882] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  339.067892] hub 3-0:1.0: hub_port_status failed (err = -32)
[  339.067894] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
```

And that's all she wrote!  I can't figure this thing out and I need my USB ports working.  If you have ANY ideas, please let me know... I follow great instructions and will try just about anything.  Thanks!

---

### Post by darkworld on 2008-02-06
looks like there are other suspend problems about. I had a quick scoot round. Found this [http://ubuntuforums.org/showthread.php?t=417302]("http://ubuntuforums.org/showthread.php?t=417302")

---

### Post by Jouke74 on 2008-02-06
Uhh, did you try to boot the Kernel already with the NOACPI NOAPIC and IRQPOLL options? 

Maybe delete the devices in Vista and reinstall all, by letting it scan for new hardware? 

It looks like your USB ports got stuck in S1/S3 state and somehow don't come out. I simple reset should de the trick normally I would have guessed but.... It is possible that your hardware got damaged, although the start-up of USB related devices seems to do it's thing ok? :confused: clueless here.

---

### Post by terak on 2008-02-06
> **Jouke74 said:**
> Uhh, did you try to boot the Kernel already with the NOACPI NOAPIC and IRQPOLL options? 

Maybe delete the devices in Vista and reinstall all, by letting it scan for new hardware? 

It looks like your USB ports got stuck in S1/S3 state and somehow don't come out. I simple reset should de the trick normally I would have guessed but.... It is possible that your hardware got damaged, although the start-up of USB related devices seems to do it's thing ok? :confused: clueless here.

I've added everything I can find to the menu.lst including: noacpi noapic irqpoll noirqdebug and nothing fixes it.

I've also deleted all the devices through the device manager in windows (in safe mode) and re-booted to allow windows to find new hardware.  It finds everything just peachy, but as soon as I plug ANY usb device, it gives me the 'Device Unrecognized' bubble.  It's like the power on the USB ports are stuck.  I don't have any self powered devices that I can plug into the ports to see if they work.... I only have peripherals that run off the USB's power.

Thanks for the suggestions and please share anything else that comes to mind. I'm dying here!  Thanks!

---

### Post by terak on 2008-02-07
BUMP

Anyone have any more thoughts?  Still willing to try to get this fixed and I still don't have a solution.  Since this post, I've unplugged the power, took the battery out and even opened up the laptop and removed the CR2032 battery that's inside.  Removed both hard drives and both memory sticks, in hopes that something would jog the USB out of the powerstate, if that is indeed the case.  Still not working though. :(  If I knew how to get inside and unplug the USB, I would... but atlas, I can't figure that out and am afraid that in doing so I could completely ruin my laptop... and that wouldn't be good.

---

### Post by Everywhere_at_Once on 2008-02-07
I dont have the help your looking for, but i can say that tearing into your laptop and taking everything apart is, chances are, not going to fix your usb problem. see if you can re-install the usb controller, go into windows and get SiSoftware sandra, [here]("http://filehippo.com/download_sandra_lite/") it has very good nitty-gritty information on your computer, and also some diagnostic tools im pretty sure.

i think your problem is very abstract and rare, there may not be the help your looking for on this forum...
it might be an idea to contact a technician. or post in a hardware forum.

good luck

-SW

---

### Post by gruhland on 2008-02-07
I'm sure but could it be that you did not shut down Windows properly but put it in standby/sleep or whatever... mode? It should not make any difference but for example on a harddisk  it would cause that you cannot mount the windows partition read/write with Ubuntu. Maybe there is a similar mechanism which "locks" the USB ports. It's only an idea...

---

### Post by Jouke74 on 2008-02-07
I am afraid that it's hardware related. Both OSes cannot do anything with your USBs, that is already a good indication that excludes some software configuration. Normally a reboot and taking the power off would restore states, and that has not seemed to have happened. Therefore, indeed a technician seems the most useful next step. 

Before you do that, still see if there is in the BIOS something about powersaving/ S1/S3 states yes / no and turn all of those off. Then you basically disable the ACPI using the BIOS. I don't think it will matter though, and I don't know if your BIOS has these options.

---

### Post by terak on 2008-02-07
Okay, well I installed SiSoftware Sandra and here's what I get when I look at my USB info with one device plugged in:

SiSoftware Sandra

```
General Information
Controller : ATI I/O Communications Processor USB 2.0 EHCI controller

Root Hub
Compound Device : No
[COLOR="Red"]Hub Is Bus Powered : No[/COLOR]
Power Switching : Gang-switched
Over-current Protection : Global
Number of Ports : 8

Root Hub: USB Port 1
Status : No Device Connected

Root Hub: USB Port 2
Status : No Device Connected

Root Hub: USB Port 3
Status : No Device Connected

Root Hub: USB Port 4
Status : No Device Connected

Root Hub: USB Port 5
Status : No Device Connected

[COLOR="Red"]Root Hub: USB Port 6
Status : Device Failed Enumeration
Device Connected to Port : Unknown Device
OEM Device Name : ??? (0000) ??? (0000)
Speed : Low (1.5Mbps)
[/COLOR]
Root Hub: USB Port 7
Status : No Device Connected

Root Hub: USB Port 8
Status : No Device Connected
```

So I'm wondering, is there my problem?  Shouldn't the hub be powered??

As for the BIOS, I haven't checked it yet, but will post as soon as I do.

Another thing I found in the SiSoftware... it states that my laptop only support S3, S4, S5 modes.  Could that have been the issue?  Does Ubuntu default to using S1, which could have locked up my USB power?

Also, I already tried to suspend the laptop in Windows and bring it back... works great but didn't fix my USB issues. :/

Thanks and keep the ideas coming! :)

---

### Post by terak on 2008-02-09
BUMP.

Any more thoughts or suggestions besides sending it in?  i really don't mind having someone repair it, i just don't want to risk anyone 'restoring' everything and wiping my harddrive(s) clean.

---

### Post by John Jason Jordan on 2008-02-09
> **terak said:**
> BUMP.

Any more thoughts or suggestions besides sending it in?  i really don't mind having someone repair it, i just don't want to risk anyone 'restoring' everything and wiping my harddrive(s) clean.
When you send a computer in for repair you are just asking for them to destroy your data. Tech support at computer companies *always* assume first that the problem is the user's software rather than their hardware. They do this because if there is any way they can claim it is your software it gets them out of having to fix the problem. Therefore, the first thing they will do is boot the computer. And when they see Linux (unless the computer company specifically supports Linux), they will immediately ship it back to you without even trying to fix it.

In my experience, the only way around this is to send them the computer with a hard disk already wiped out. Or if you dual boot and have Windows on the computer, wipe out Linux so all they see is Windows.

Even if they do support Linux, it is only prudent to make a thorough copy of everything on your hard drive. If your USB ports aren't working and you have no network drive to back everything up to, then you'll have to use your CD/DVD drive. Never let your computer get into someone else's hands without a complete backup first.

---

