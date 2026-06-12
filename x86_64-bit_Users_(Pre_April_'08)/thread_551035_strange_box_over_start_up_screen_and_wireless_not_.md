---
title: "strange box over start up screen and wireless not working"
date: 2007-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by elquer on 2007-09-14
since the day i got back to school i noticed a strange looking box on the left corner of my boot up screen (flash screen) and recently wireless hasn't been connecting when i can see everyone around me has connection,i can see wireless networks available but can't connect.. help needed asap,,,, thanks,

---

### Post by bford16 on 2007-09-15
> **elquer said:**
> since the day i got back to school i noticed a strange looking box on the left corner of my boot up screen (flash screen) and recently wireless hasn't been connecting when i can see everyone around me has connection,i can see wireless networks available but can't connect.. help needed asap,,,, thanks,

Please open a terminal and enter these commands.

dmesg

and

lspci -v

Then post the results here.  That will help knowledgeable people help you.  (Not necessarily me, either.  I'm only an advanced beginner.)

---

### Post by elquer on 2007-09-25
bruno@bruno-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 18:31:23 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] Command line: root=UUID=2566b874-247e-45aa-adcf-230110cdb054 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000057ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000057ef0000 - 0000000057eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000057eff000 - 0000000057f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000057f00000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 360176) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000f8080
[    0.000000] ACPI: RSDT (v001 HP     3093     0x20040224  LTP 0x00000000) @ 0x0000000057ef8bc1
[    0.000000] ACPI: FADT (v001 HP     3093     0x20040224 PTL  0x0000005f) @ 0x0000000057efee2a
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x20040224  LTP 0x00000001) @ 0x0000000057efee9e
[    0.000000] ACPI: MADT (v001 PTLTD    3093   0x20040224  LTP 0x00000000) @ 0x0000000057efef74
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x20040224  LTP 0x00000000) @ 0x0000000057efefc4
[    0.000000] ACPI: DSDT (v001 HP     3091     0x20040224 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000057ef0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 360176) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-0000000057ef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   360176
[    0.000000] On node 0 totalpages: 360079
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2856 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 4868 pages used for memmap
[    0.000000]   DMA32 zone: 351212 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000d2000
[    0.000000] Nosave address range: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 354068
[    0.000000] Kernel command line: root=UUID=2566b874-247e-45aa-adcf-230110cdb054 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    9.266020] Console: colour VGA+ 80x25
[    9.268306] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    9.272279] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.273633] Checking aperture...
[    9.273642] CPU 0: aperture @ 72000000 size 32 MB
[    9.273644] Aperture too small (32 MB)
[    9.286037] No AGP bridge found
[    9.312303] Memory: 1405740k/1440704k available (2218k kernel code, 34576k reserved, 1162k data, 304k init)
[    9.391001] Calibrating delay using timer specific routine.. 3593.46 BogoMIPS (lpj=7186928)
[    9.391074] Security Framework v1.0.0 initialized
[    9.391083] SELinux:  Disabled at boot.
[    9.391112] Mount-cache hash table entries: 256
[    9.391312] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    9.391315] CPU: L2 Cache: 512K (64 bytes/line)
[    9.391318] CPU 0/0 -> Node 0
[    9.391346] SMP alternatives: switching to UP code
[    9.391736] Freeing SMP alternatives: 28k freed
[    9.391870] Early unpacking initramfs... done
[    9.724867] ACPI: Core revision 20060707
[    9.725120] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    9.769840] Using local APIC timer interrupts.
[    9.825507] result 12464265
[    9.825509] Detected 12.464 MHz APIC timer.
[    9.826658] Brought up 1 CPUs
[    9.826704] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    9.826707] time.c: Detected 1794.853 MHz processor.
[    9.827077] Time: 13:49:53  Date: 08/25/107
[    9.827125] NET: Registered protocol family 16
[    9.827229] ACPI: bus type pci registered
[    9.827238] PCI: Using configuration type 1
[    9.829732] ACPI: Interpreter enabled
[    9.829735] ACPI: Using IOAPIC for interrupt routing
[    9.830270] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.830275] PCI: Probing PCI hardware (bus 00)
[    9.832176] Boot video device is 0000:01:05.0
[    9.832772] PCI: Transparent bridge - 0000:00:14.4
[    9.832849] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#05) (try 'pci=assign-busses')
[    9.832851] Please report the result to linux-kernel to fix this permanently
[    9.832878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.835957] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    9.836227] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    9.836492] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    9.836761] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    9.837025] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    9.837290] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    9.837554] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    9.837818] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    9.840430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    9.840821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    9.841249] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.841260] pnp: PnP ACPI init
[    9.844125] pnp: PnP ACPI: found 10 devices
[    9.844197] PCI: Using ACPI for IRQ routing
[    9.844200] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.844326] NET: Registered protocol family 8
[    9.844328] NET: Registered protocol family 20
[    9.844645] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[    9.844648] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[    9.844651] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[    9.844654] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    9.844974] PCI: Bridge: 0000:00:01.0
[    9.844976]   IO window: 9000-9fff
[    9.844980]   MEM window: c0100000-c01fffff
[    9.844984]   PREFETCH window: c8000000-cfffffff
[    9.844994] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[    9.844996]   IO window: 0000a400-0000a4ff
[    9.845003]   IO window: 0000a800-0000a8ff
[    9.845009]   PREFETCH window: 70000000-73ffffff
[    9.845015]   MEM window: 74000000-77ffffff
[    9.845020] PCI: Bridge: 0000:00:14.4
[    9.845024]   IO window: a000-afff
[    9.845030]   MEM window: c0200000-c02fffff
[    9.845036]   PREFETCH window: 70000000-73ffffff
[    9.845077] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[    9.845085] PCI: Setting latency timer of device 0000:05:09.0 to 64
[    9.845171] NET: Registered protocol family 2
[    9.882668] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    9.883372] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    9.888951] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    9.890338] TCP: Hash tables configured (established 262144 bind 65536)
[    9.890342] TCP reno registered
[    9.898714] checking if image is initramfs... it is
[   10.530144] Freeing initrd memory: 7305k freed
[   10.539614] audit: initializing netlink socket (disabled)
[   10.539632] audit(1190728194.224:1): initialized
[   10.539800] VFS: Disk quotas dquot_6.5.1
[   10.539821] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   10.539882] io scheduler noop registered
[   10.539884] io scheduler anticipatory registered
[   10.539887] io scheduler deadline registered
[   10.539900] io scheduler cfq registered (default)
[   11.239291] Real Time Clock Driver v1.12ac
[   11.239339] Linux agpgart interface v0.102 (c) Dave Jones
[   11.239341] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.239955] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   11.239967] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   11.240046] mice: PS/2 mouse device common for all mice
[   11.240612] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.240881] input: Macintosh mouse button emulation as /class/input/input0
[   11.240915] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.240919] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.241220] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   11.244269] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.244277] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.244383] TCP cubic registered
[   11.244393] NET: Registered protocol family 1
[   11.244557] ACPI: (supports S0 S3 S4 S5)
[   11.244604]   Magic number: 7:64:838
[   11.244691]   hash matches device ptyu4
[   11.244733] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   11.244832] Freeing unused kernel memory: 304k freed
[   11.274222] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.450796] Capability LSM initialized
[   12.498842] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   12.498849] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.503934] ACPI: Thermal Zone [THRM] (64 C)
[   13.054385] usbcore: registered new interface driver usbfs
[   13.054413] usbcore: registered new interface driver hub
[   13.054438] usbcore: registered new device driver usb
[   13.055271] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.055315] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   13.055333] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   13.055527] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   13.055549] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   13.132130] usb usb1: configuration #1 chosen from 1 choice
[   13.132161] hub 1-0:1.0: USB hub found
[   13.132175] hub 1-0:1.0: 4 ports detected
[   13.216305] 8139too Fast Ethernet driver 0.9.28
[   13.236651] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   13.236673] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   13.236697] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   13.236717] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   13.241284] ieee1394: Initialized config rom entry `ip1394'
[   13.295746] usb usb2: configuration #1 chosen from 1 choice
[   13.295782] hub 2-0:1.0: USB hub found
[   13.295797] hub 2-0:1.0: 4 ports detected
[   13.399664] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   13.399686] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   13.399712] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   13.399776] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   13.399789] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.399895] usb usb3: configuration #1 chosen from 1 choice
[   13.399920] hub 3-0:1.0: USB hub found
[   13.399927] hub 3-0:1.0: 8 ports detected
[   13.504518] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   13.504541] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   13.504554] ATIIXP: chipset revision 0
[   13.504557] ATIIXP: not 100% native mode: will probe irqs later
[   13.504567]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   13.504583]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   13.504595] Probing IDE interface ide0...
[   13.807478] hda: TOSHIBA MK1031GAS, ATA DISK drive
[   14.082791] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   14.291957] usb 1-1: configuration #1 chosen from 1 choice
[   14.305337] usbcore: registered new interface driver hiddev
[   14.312159] input: Logitech USB Receiver as /class/input/input2
[   14.312290] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[   14.312304] usbcore: registered new interface driver usbhid
[   14.312308] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.478569] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   14.504183] Probing IDE interface ide1...
[   15.238198] hdc: HL-DT-ST DVDRAM GSA-4082N, ATAPI CD/DVD-ROM drive
[   15.574379] ide1 at 0x170-0x177,0x376 on irq 15
[   15.585642] SCSI subsystem initialized
[   15.592602] libata version 2.20 loaded.
[   15.595372] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   15.596489] eth0: RealTek RTL8139 at 0xffffc20000036000, 00:16:36:33:65:91, IRQ 18
[   15.596493] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   15.599875] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   15.600698] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 22 (level, low) -> IRQ 22
[   15.655681] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   15.663740] hda: max request size: 128KiB
[   15.663746] hda: 195371568 sectors (100030 MB), CHS=65535/16/63, UDMA(100)
[   15.676971] hda: cache flushes supported
[   15.677033]  hda: hda1 hda2 < hda5 >
[   15.750660] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[   15.750669] Uniform CD-ROM driver Revision: 3.20
[   16.024190] Attempting manual resume
[   16.024195] swsusp: Resume From Partition 3:5
[   16.024197] PM: Checking swsusp image.
[   16.024412] PM: Resume from disk failed.
[   16.086706] kjournald starting.  Commit interval 5 seconds
[   16.086720] EXT3-fs: mounted filesystem with ordered data mode.
[   34.069564] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.106860] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.124081] ieee80211_crypt: registered algorithm 'NULL'
[   34.126546] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   34.126551] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   34.161255] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[   34.161282] Yenta: Enabling burst memory read transactions
[   34.161288] Yenta: Using CSCINT to route CSC interrupts to PCI
[   34.161290] Yenta: Routing CardBus interrupts to PCI
[   34.161297] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x64
[   34.393567] Yenta: ISA IRQ mask 0x0ee8, PCI irq 17
[   34.393574] Socket status: 30000006
[   34.393577] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   34.393586] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   34.393590] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   34.393594] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x73ffffff
[   34.393956] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   34.448267] input: PC Speaker as /class/input/input3
[   34.481103] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 17
[   34.543004] bcm43xx driver
[   34.543128] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[   34.701797] sdhci: Secure Digital Host Controller Interface driver
[   34.701803] sdhci: Copyright(c) Pierre Ossman
[   34.701857] sdhci: SDHCI controller found at 0000:05:09.4 [104c:8034] (rev 0)
[   34.701882] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 17
[   34.701966] mmc0: SDHCI at 0xc0209400 irq 17 DMA
[   34.702014] mmc1: SDHCI at 0xc0209000 irq 17 DMA
[   34.702064] mmc2: SDHCI at 0xc0208400 irq 17 DMA
[   34.737932] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   34.864327] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   34.976108] MC'97 0 converters and GPIO not ready (0x1)
[   35.312807] fuse init (API version 7.8)
[   35.337019] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   35.373419] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   35.487781] lp: driver loaded but no devices found
[   35.590767] Adding 1871532k swap on /dev/disk/by-uuid/f7aa5cde-826a-470e-bdd1-17aaeb4e4a83.  Priority:-1 extents:1 across:1871532k
[   35.740922] EXT3 FS on hda1, internal journal
[   37.426240] NET: Registered protocol family 17
[   41.514552] ibm_acpi: ec object not found
[   41.626360] input: Power Button (FF) as /class/input/input5
[   41.631288] ACPI: Power Button (FF) [PWRF]
[   41.658325] input: Power Button (CM) as /class/input/input6
[   41.663162] ACPI: Power Button (CM) [PWRB]
[   41.690272] input: Sleep Button (CM) as /class/input/input7
[   41.695119] ACPI: Sleep Button (CM) [SLPB]
[   41.722210] input: Lid Switch as /class/input/input8
[   41.727028] ACPI: Lid Switch [LID]
[   41.765603] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   41.778244] No dock devices found.
[   41.794465] ACPI: AC Adapter [ACAD] (on-line)
[   41.806572] Using specific hotkey driver
[   41.906163] ACPI: Battery Slot [BAT1] (battery present)
[   41.966736] pcc_acpi: loading...
[   41.982352] wmi_add device=ffff810055617800
[   41.982357] calling WQBA
[   42.198467] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (version 2.00.00)
[   42.198513] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[   42.198516] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   42.198519] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[   44.612628] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.967156] Losing some ticks... checking if CPU frequency changed.
[   46.608286] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   46.615793] [fglrx] Maximum main memory to use for locked dma buffers: 1282 MBytes.
[   46.616085] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   46.702044] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   46.803765] ppdev: user-space parallel port driver
[   49.418653] [fglrx] total      GART = 130023424
[   49.418661] [fglrx] free       GART = 114032640
[   49.418664] [fglrx] max single GART = 114032640
[   49.418667] [fglrx] total      LFB  = 134217728
[   49.418669] [fglrx] free       LFB  = 120320000
[   49.418671] [fglrx] max single LFB  = 120320000
[   49.418673] [fglrx] total      Inv  = 0
[   49.418675] [fglrx] free       Inv  = 0
[   49.418677] [fglrx] max single Inv  = 0
[   49.418678] [fglrx] total      TIM  = 0
[   51.617678] NET: Registered protocol family 10
[   51.617795] lo: Disabled Privacy Extensions
[   51.617936] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   59.368984] Bluetooth: Core ver 2.11
[   59.369051] NET: Registered protocol family 31
[   59.369053] Bluetooth: HCI device and connection manager initialized
[   59.369059] Bluetooth: HCI socket layer initialized
[   59.392119] Bluetooth: L2CAP ver 2.8
[   59.392123] Bluetooth: L2CAP socket layer initialized
[   59.493048] Bluetooth: RFCOMM socket layer initialized
[   59.493066] Bluetooth: RFCOMM TTY layer initialized
[   59.493068] Bluetooth: RFCOMM ver 1.8
[   60.761395] eth0: no IPv6 routers present
bruno@bruno-laptop:~$

---

### Post by elquer on 2007-09-25
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2856 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 4868 pages used for memmap
[    0.000000]   DMA32 zone: 351212 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000d2000
[    0.000000] Nosave address range: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 354068
[    0.000000] Kernel command line: root=UUID=2566b874-247e-45aa-adcf-230110cdb054 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    9.266020] Console: colour VGA+ 80x25
[    9.268306] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    9.272279] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.273633] Checking aperture...
[    9.273642] CPU 0: aperture @ 72000000 size 32 MB
[    9.273644] Aperture too small (32 MB)
[    9.286037] No AGP bridge found
[    9.312303] Memory: 1405740k/1440704k available (2218k kernel code, 34576k reserved, 1162k data, 304k init)
[    9.391001] Calibrating delay using timer specific routine.. 3593.46 BogoMIPS (lpj=7186928)
[    9.391074] Security Framework v1.0.0 initialized
[    9.391083] SELinux:  Disabled at boot.
[    9.391112] Mount-cache hash table entries: 256
[    9.391312] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    9.391315] CPU: L2 Cache: 512K (64 bytes/line)
[    9.391318] CPU 0/0 -> Node 0
[    9.391346] SMP alternatives: switching to UP code
[    9.391736] Freeing SMP alternatives: 28k freed
[    9.391870] Early unpacking initramfs... done
[    9.724867] ACPI: Core revision 20060707
[    9.725120] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    9.769840] Using local APIC timer interrupts.
[    9.825507] result 12464265
[    9.825509] Detected 12.464 MHz APIC timer.
[    9.826658] Brought up 1 CPUs
[    9.826704] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    9.826707] time.c: Detected 1794.853 MHz processor.
[    9.827077] Time: 13:49:53  Date: 08/25/107
[    9.827125] NET: Registered protocol family 16
[    9.827229] ACPI: bus type pci registered
[    9.827238] PCI: Using configuration type 1
[    9.829732] ACPI: Interpreter enabled
[    9.829735] ACPI: Using IOAPIC for interrupt routing
[    9.830270] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.830275] PCI: Probing PCI hardware (bus 00)
[    9.832176] Boot video device is 0000:01:05.0
[    9.832772] PCI: Transparent bridge - 0000:00:14.4
[    9.832849] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#05) (try 'pci=assign-busses')
[    9.832851] Please report the result to linux-kernel to fix this permanently
[    9.832878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.835957] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    9.836227] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    9.836492] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    9.836761] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    9.837025] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    9.837290] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    9.837554] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    9.837818] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    9.840430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    9.840821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    9.841249] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.841260] pnp: PnP ACPI init
[    9.844125] pnp: PnP ACPI: found 10 devices
[    9.844197] PCI: Using ACPI for IRQ routing
[    9.844200] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.844326] NET: Registered protocol family 8
[    9.844328] NET: Registered protocol family 20
[    9.844645] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[    9.844648] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[    9.844651] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[    9.844654] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    9.844974] PCI: Bridge: 0000:00:01.0
[    9.844976]   IO window: 9000-9fff
[    9.844980]   MEM window: c0100000-c01fffff
[    9.844984]   PREFETCH window: c8000000-cfffffff
[    9.844994] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[    9.844996]   IO window: 0000a400-0000a4ff
[    9.845003]   IO window: 0000a800-0000a8ff
[    9.845009]   PREFETCH window: 70000000-73ffffff
[    9.845015]   MEM window: 74000000-77ffffff
[    9.845020] PCI: Bridge: 0000:00:14.4
[    9.845024]   IO window: a000-afff
[    9.845030]   MEM window: c0200000-c02fffff
[    9.845036]   PREFETCH window: 70000000-73ffffff
[    9.845077] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[    9.845085] PCI: Setting latency timer of device 0000:05:09.0 to 64
[    9.845171] NET: Registered protocol family 2
[    9.882668] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    9.883372] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    9.888951] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    9.890338] TCP: Hash tables configured (established 262144 bind 65536)
[    9.890342] TCP reno registered
[    9.898714] checking if image is initramfs... it is
[   10.530144] Freeing initrd memory: 7305k freed
[   10.539614] audit: initializing netlink socket (disabled)
[   10.539632] audit(1190728194.224:1): initialized
[   10.539800] VFS: Disk quotas dquot_6.5.1
[   10.539821] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   10.539882] io scheduler noop registered
[   10.539884] io scheduler anticipatory registered
[   10.539887] io scheduler deadline registered
[   10.539900] io scheduler cfq registered (default)
[   11.239291] Real Time Clock Driver v1.12ac
[   11.239339] Linux agpgart interface v0.102 (c) Dave Jones
[   11.239341] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.239955] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   11.239967] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   11.240046] mice: PS/2 mouse device common for all mice
[   11.240612] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.240881] input: Macintosh mouse button emulation as /class/input/input0
[   11.240915] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.240919] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.241220] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   11.244269] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.244277] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.244383] TCP cubic registered
[   11.244393] NET: Registered protocol family 1
[   11.244557] ACPI: (supports S0 S3 S4 S5)
[   11.244604]   Magic number: 7:64:838
[   11.244691]   hash matches device ptyu4
[   11.244733] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   11.244832] Freeing unused kernel memory: 304k freed
[   11.274222] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.450796] Capability LSM initialized
[   12.498842] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   12.498849] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.503934] ACPI: Thermal Zone [THRM] (64 C)
[   13.054385] usbcore: registered new interface driver usbfs
[   13.054413] usbcore: registered new interface driver hub
[   13.054438] usbcore: registered new device driver usb
[   13.055271] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.055315] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   13.055333] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   13.055527] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   13.055549] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   13.132130] usb usb1: configuration #1 chosen from 1 choice
[   13.132161] hub 1-0:1.0: USB hub found
[   13.132175] hub 1-0:1.0: 4 ports detected
[   13.216305] 8139too Fast Ethernet driver 0.9.28
[   13.236651] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   13.236673] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   13.236697] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   13.236717] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   13.241284] ieee1394: Initialized config rom entry `ip1394'
[   13.295746] usb usb2: configuration #1 chosen from 1 choice
[   13.295782] hub 2-0:1.0: USB hub found
[   13.295797] hub 2-0:1.0: 4 ports detected
[   13.399664] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   13.399686] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   13.399712] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   13.399776] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   13.399789] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.399895] usb usb3: configuration #1 chosen from 1 choice
[   13.399920] hub 3-0:1.0: USB hub found
[   13.399927] hub 3-0:1.0: 8 ports detected
[   13.504518] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   13.504541] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   13.504554] ATIIXP: chipset revision 0
[   13.504557] ATIIXP: not 100% native mode: will probe irqs later
[   13.504567]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   13.504583]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   13.504595] Probing IDE interface ide0...
[   13.807478] hda: TOSHIBA MK1031GAS, ATA DISK drive
[   14.082791] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   14.291957] usb 1-1: configuration #1 chosen from 1 choice
[   14.305337] usbcore: registered new interface driver hiddev
[   14.312159] input: Logitech USB Receiver as /class/input/input2
[   14.312290] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[   14.312304] usbcore: registered new interface driver usbhid
[   14.312308] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.478569] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   14.504183] Probing IDE interface ide1...
[   15.238198] hdc: HL-DT-ST DVDRAM GSA-4082N, ATAPI CD/DVD-ROM drive
[   15.574379] ide1 at 0x170-0x177,0x376 on irq 15
[   15.585642] SCSI subsystem initialized
[   15.592602] libata version 2.20 loaded.
[   15.595372] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   15.596489] eth0: RealTek RTL8139 at 0xffffc20000036000, 00:16:36:33:65:91, IRQ 18
[   15.596493] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   15.599875] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   15.600698] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 22 (level, low) -> IRQ 22
[   15.655681] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   15.663740] hda: max request size: 128KiB
[   15.663746] hda: 195371568 sectors (100030 MB), CHS=65535/16/63, UDMA(100)
[   15.676971] hda: cache flushes supported
[   15.677033]  hda: hda1 hda2 < hda5 >
[   15.750660] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[   15.750669] Uniform CD-ROM driver Revision: 3.20
[   16.024190] Attempting manual resume
[   16.024195] swsusp: Resume From Partition 3:5
[   16.024197] PM: Checking swsusp image.
[   16.024412] PM: Resume from disk failed.
[   16.086706] kjournald starting.  Commit interval 5 seconds
[   16.086720] EXT3-fs: mounted filesystem with ordered data mode.
[   34.069564] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.106860] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.124081] ieee80211_crypt: registered algorithm 'NULL'
[   34.126546] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   34.126551] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   34.161255] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[   34.161282] Yenta: Enabling burst memory read transactions
[   34.161288] Yenta: Using CSCINT to route CSC interrupts to PCI
[   34.161290] Yenta: Routing CardBus interrupts to PCI
[   34.161297] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x64
[   34.393567] Yenta: ISA IRQ mask 0x0ee8, PCI irq 17
[   34.393574] Socket status: 30000006
[   34.393577] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   34.393586] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   34.393590] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   34.393594] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x73ffffff
[   34.393956] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   34.448267] input: PC Speaker as /class/input/input3
[   34.481103] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 17
[   34.543004] bcm43xx driver
[   34.543128] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[   34.701797] sdhci: Secure Digital Host Controller Interface driver
[   34.701803] sdhci: Copyright(c) Pierre Ossman
[   34.701857] sdhci: SDHCI controller found at 0000:05:09.4 [104c:8034] (rev 0)
[   34.701882] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 17
[   34.701966] mmc0: SDHCI at 0xc0209400 irq 17 DMA
[   34.702014] mmc1: SDHCI at 0xc0209000 irq 17 DMA
[   34.702064] mmc2: SDHCI at 0xc0208400 irq 17 DMA
[   34.737932] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   34.864327] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   34.976108] MC'97 0 converters and GPIO not ready (0x1)
[   35.312807] fuse init (API version 7.8)
[   35.337019] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   35.373419] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   35.487781] lp: driver loaded but no devices found
[   35.590767] Adding 1871532k swap on /dev/disk/by-uuid/f7aa5cde-826a-470e-bdd1-17aaeb4e4a83.  Priority:-1 extents:1 across:1871532k
[   35.740922] EXT3 FS on hda1, internal journal
[   37.426240] NET: Registered protocol family 17
[   41.514552] ibm_acpi: ec object not found
[   41.626360] input: Power Button (FF) as /class/input/input5
[   41.631288] ACPI: Power Button (FF) [PWRF]
[   41.658325] input: Power Button (CM) as /class/input/input6
[   41.663162] ACPI: Power Button (CM) [PWRB]
[   41.690272] input: Sleep Button (CM) as /class/input/input7
[   41.695119] ACPI: Sleep Button (CM) [SLPB]
[   41.722210] input: Lid Switch as /class/input/input8
[   41.727028] ACPI: Lid Switch [LID]
[   41.765603] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   41.778244] No dock devices found.
[   41.794465] ACPI: AC Adapter [ACAD] (on-line)
[   41.806572] Using specific hotkey driver
[   41.906163] ACPI: Battery Slot [BAT1] (battery present)
[   41.966736] pcc_acpi: loading...
[   41.982352] wmi_add device=ffff810055617800
[   41.982357] calling WQBA
[   42.198467] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (version 2.00.00)
[   42.198513] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[   42.198516] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   42.198519] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[   44.612628] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.967156] Losing some ticks... checking if CPU frequency changed.
[   46.608286] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   46.615793] [fglrx] Maximum main memory to use for locked dma buffers: 1282 MBytes.
[   46.616085] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   46.702044] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   46.803765] ppdev: user-space parallel port driver
[   49.418653] [fglrx] total      GART = 130023424
[   49.418661] [fglrx] free       GART = 114032640
[   49.418664] [fglrx] max single GART = 114032640
[   49.418667] [fglrx] total      LFB  = 134217728
[   49.418669] [fglrx] free       LFB  = 120320000
[   49.418671] [fglrx] max single LFB  = 120320000
[   49.418673] [fglrx] total      Inv  = 0
[   49.418675] [fglrx] free       Inv  = 0
[   49.418677] [fglrx] max single Inv  = 0
[   49.418678] [fglrx] total      TIM  = 0
[   51.617678] NET: Registered protocol family 10
[   51.617795] lo: Disabled Privacy Extensions
[   51.617936] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   59.368984] Bluetooth: Core ver 2.11
[   59.369051] NET: Registered protocol family 31
[   59.369053] Bluetooth: HCI device and connection manager initialized
[   59.369059] Bluetooth: HCI socket layer initialized
[   59.392119] Bluetooth: L2CAP ver 2.8
[   59.392123] Bluetooth: L2CAP socket layer initialized
[   59.493048] Bluetooth: RFCOMM socket layer initialized
[   59.493066] Bluetooth: RFCOMM TTY layer initialized
[   59.493068] Bluetooth: RFCOMM ver 1.8
[   60.761395] eth0: no IPv6 routers present
bruno@bruno-laptop:~$ clear

bruno@bruno-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 70000000-73ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at c0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at c0003800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 17
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at a000 [size=256]
        Memory at c0208000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1355
        Flags: bus master, fast devsel, latency 64, IRQ 20
        Memory at c0204000 (32-bit, non-prefetchable) [size=8K]

05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at c020a000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 70000000-73fff000 (prefetchable)
        Memory window 1: 74000000-77fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at c0208800 (32-bit, non-prefetchable) [size=2K]
        Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at c0206000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
        Subsystem: Hewlett-Packard Company Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at c0209400 (32-bit, non-prefetchable) [size=256]
        Memory at c0209000 (32-bit, non-prefetchable) [size=256]
        Memory at c0208400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by elquer on 2007-09-26
is there anyone who could help me fix this? please!!!!

---

