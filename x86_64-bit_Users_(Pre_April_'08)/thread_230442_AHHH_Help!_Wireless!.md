---
title: "AHHH Help! Wireless!"
date: 2006-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by friedokra on 2006-08-05
okay. I've been having tons of problems getting my wireless card to detect wireless internet access (the kind present in restaurants,hotels,home,school,libraries,etc.) see here - okay. I've been having tons of problems getting my wireless card to detect wireless internet access (the kind present in restaurants,hotels,home,school,libraries,etc.) see here - [http://www.ubuntuforums.org/showthread.php?t=224260](http://www.ubuntuforums.org/showthread.php?t=224260)
After this method failed. I tried using the ndiswrapper to enable my wireless adapter for my Acer Aspire 5004 notebook PC. I installed the driver (bcmwl5.inf) After typing: "sudo ndisgk" it says (in the window showing my driver) that the hardware is present. Also included with the inf file was a .cat file and a .sys file. I don't know if I need to do anything with those. After typing "dmesg" in my terminal, it comes back saying:

---

### Post by friedokra on 2006-08-05
"[    0.000000] Bootdata ok (command line is root=/dev/hda1 ro quiet splash)
[    0.000000] Linux version 2.6.15-26-amd64-generic (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Jul 17 19:50:04 UTC 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003befa000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003befa000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00000000000f7f60
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x000000003bef619d
[    0.000000] ACPI: FADT (v001 SiS    755F     0x06040000 PTL  0x000f4240) @ 0x000000003bef9e3e
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003bef9eb2
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x000000003bef9f88
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000003bef9fd8
[    0.000000] ACPI: DSDT (v001 PTLTD       755 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003bef0000
[    0.000000] Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003bef0000
[    0.000000] On node 0 totalpages: 241107
[    0.000000]   DMA zone: 3015 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 238092 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff00000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ e0000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e0000000 size 32 MB (APSIZE f38)
[    0.000000] Aperture from AGP bridge too small (32 MB)
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 4000000
[    0.000000] SMP: Allowing 3 CPUs, 2 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 1800.086 MHz processor.
[   12.190096] Console: colour VGA+ 80x25
[   12.191354] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)[   12.192205] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   12.207193] Memory: 889976k/981952k available (2150k kernel code, 91588k reserved, 757k data, 180k init)
[   12.287250] Calibrating delay using timer specific routine.. 3604.28 BogoMIPS (lpj=7208574)
[   12.287316] Security Framework v1.0.0 initialized
[   12.287324] SELinux:  Disabled at boot.
[   12.287350] Mount-cache hash table entries: 256
[   12.287513] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   12.287516] CPU: L2 Cache: 1024K (64 bytes/line)

---

### Post by friedokra on 2006-08-05
[   12.287519] CPU 0(1) -> Node 0 -> Core 0
[   12.287528] mtrr: v2.0 (20020519)
[   12.287538] SMP alternatives: switching to UP code
[   12.288029] checking if image is initramfs... it is
[   12.899111] Freeing initrd memory: 7097k freed
[   12.907854] ACPI: Looking for DSDT ... not found!
[   12.951673] Using local APIC timer interrupts.
[   13.007145] Detected 12.500 MHz APIC timer.
[   13.007224] Brought up 1 CPUs
[   13.007256] time.c: Using PIT/TSC based timekeeping.
[   13.007258] testing NMI watchdog ... OK.
[   13.047536] NET: Registered protocol family 16
[   13.047563] ACPI: bus type pci registered
[   13.047570] PCI: Using configuration type 1
[   13.048063] ACPI: Subsystem revision 20051216
[   13.049748] ACPI: Interpreter enabled
[   13.049750] ACPI: Using IOAPIC for interrupt routing
[   13.049991] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.049995] PCI: Probing PCI hardware (bus 00)
[   13.051334] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[   13.051368] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[   13.051734] Boot video device is 0000:01:00.0
[   13.051799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.058225] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[   13.071261] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[   13.071430] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
[   13.071600] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[   13.071777] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[   13.071961] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[   13.072127] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[   13.072294] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[   13.072460] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[   13.072745] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.072753] pnp: PnP ACPI init
[   13.073404] pnp: PnP ACPI: found 7 devices
[   13.073417] PCI: Using ACPI for IRQ routing
[   13.073420] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.073507] agpgart: Detected AGP bridge 0
[   13.074484] agpgart: Aperture conflicts with PCI mapping.
[   13.074517] agpgart: Aperture from AGP @ e0000000 size 32 MB
[   13.076089] agpgart: AGP aperture is 32M @ 0xe0000000
[   13.076108] PCI-DMA: Disabling IOMMU.
[   13.076283] pnp: 00:03: ioport range 0x8000-0x807f could not be reserved
[   13.076286] pnp: 00:03: ioport range 0x8080-0x80ff has been reserved
[   13.076289] pnp: 00:03: ioport range 0x8100-0x811f has been reserved
[   13.076292] pnp: 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   13.076476] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[   13.076478] PCI: Bridge: 0000:00:01.0
[   13.076481]   IO window: a000-afff
[   13.076486]   MEM window: e2100000-e21fffff
[   13.076490]   PREFETCH window: e8000000-efffffff
[   13.076494] PCI: Bus 2, cardbus bridge: 0000:00:06.0
[   13.076496]   IO window: 00002400-000024ff
[   13.076500]   IO window: 00002800-000028ff
[   13.076504]   PREFETCH window: 50000000-51ffffff
[   13.076508]   MEM window: 52000000-53ffffff
[   13.076524] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[   13.076531] GSI 16 sharing vector 0xA9 and IRQ 16
[   13.076537] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[   13.076638] Simple Boot Flag at 0x38 set to 0x1
[   13.076770] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   13.077061] audit: initializing netlink socket (disabled)
[   13.077074] audit(1154833240.888:1): initialized
[   13.077205] VFS: Disk quotas dquot_6.5.1
[   13.077222] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.077273] Initializing Cryptographic API
[   13.077277] io scheduler noop registered
[   13.077285] io scheduler anticipatory registered
[   13.077292] io scheduler deadline registered
[   13.077306] io scheduler cfq registered
[   13.091548] Real Time Clock Driver v1.12
[   13.091590] Linux agpgart interface v0.101 (c) Dave Jones
[   13.091693] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   13.096255] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.096498] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.096534] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   13.098176] GSI 17 sharing vector 0xB1 and IRQ 17
[   13.098182] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 177
[   13.098189] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   13.098555] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.098603] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.098607] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.098806] mice: PS/2 mouse device common for all mice
[   13.099818] NET: Registered protocol family 2
[   13.139040] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)[   13.139458] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   13.140600] input: AT Translated Set 2 keyboard as /class/input/input0
[   13.142372] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.143606] TCP: Hash tables configured (established 131072 bind 65536)
[   13.143610] TCP reno registered
[   13.143752] TCP bic registered
[   13.143761] NET: Registered protocol family 1
[   13.143771] NET: Registered protocol family 8
[   13.143773] NET: Registered protocol family 20
[   13.143946] ACPI wakeup devices:
[   13.143949] PCI0  LAN MODM USB0 USB1 USB2 USB3
[   13.143954] ACPI: (supports S0 S3 S4 S5)
[   13.144012] Freeing unused kernel memory: 180k freed
[   13.184174] vga16fb: initializing
[   13.184179] vga16fb: mapped to 0xffff8100000a0000
[   13.258279] Console: switching to colour frame buffer device 80x25
[   13.258284] fb0: VGA16 VGA frame buffer device
[   14.287128] Capability LSM initialized
[   14.343425] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.346501] ACPI: Thermal Zone [THRM] (42 C)
[   14.752271] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   14.752286] GSI 18 sharing vector 0xB9 and IRQ 18
[   14.752291] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 185
[   14.752302] SIS5513: chipset revision 0
[   14.752304] SIS5513: not 100% native mode: will probe irqs later
[   14.752314] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[   14.752329]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
[   14.752341]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
[   14.752350] Probing IDE interface ide0...
[   15.040172] hda: TOSHIBA MK1031GAS, ATA DISK drive
[   15.711166] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   15.735638] Probing IDE interface ide1...
[   16.470068] hdc: MATSHITAUJ-840D, ATAPI CD/DVD-ROM drive
[   16.805675] ide1 at 0x170-0x177,0x376 on irq 15
[   16.813415] hda: max request size: 1024KiB
[   16.820445] hda: 195371568 sectors (100030 MB), CHS=16383/255/63, UDMA(100)
[   16.820518] hda: cache flushes supported
[   16.820664]  hda: hda1 hda2 < hda5 >
[   16.878493] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   16.878501] Uniform CD-ROM driver Revision: 3.20
[   17.155749] usbcore: registered new driver usbfs
[   17.156011] usbcore: registered new driver hub
[   17.157472] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   17.157780] GSI 19 sharing vector 0xC1 and IRQ 19
[   17.157786] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 193
[   17.158249] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   17.412870] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   17.412883] ohci_hcd 0000:00:03.0: irq 193, io mem 0xe2002000
[   17.468642] hub 1-0:1.0: USB hub found
[   17.468653] hub 1-0:1.0: 3 ports detected
[   17.572331] GSI 20 sharing vector 0xC9 and IRQ 20
[   17.572336] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 201
[   17.572574] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   17.788061] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   17.788073] ohci_hcd 0000:00:03.1: irq 201, io mem 0xe2003000
[   17.844045] hub 2-0:1.0: USB hub found
[   17.844055] hub 2-0:1.0: 3 ports detected
[   17.949239] GSI 21 sharing vector 0xD1 and IRQ 21
[   17.949246] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 209
[   17.949697] ehci_hcd 0000:00:03.2: EHCI Host Controller
[   17.949739] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[   17.949996] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   17.950008] ehci_hcd 0000:00:03.2: irq 209, io mem 0xe2004000
[   17.950018] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.950255] hub 3-0:1.0: USB hub found
[   17.950263] hub 3-0:1.0: 6 ports detected
[   18.113025] Attempting manual resume
[   18.137427] EXT3-fs: mounted filesystem with ordered data mode.
[   18.143149] kjournald starting.  Commit interval 5 seconds
[   18.538730] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   31.853902] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.891352] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.118234] sis900.c: v1.08.09 Sep. 19 2005
[   32.118284] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 169
[   32.122906] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[   32.128436] 0000:00:04.0: Using transceiver found at address 13 as default
[   32.129071] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 169, 00:c0:9f:e9:69:54.
[   32.331323] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[   32.331335] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
[   32.331350] Yenta: Using CSCINT to route CSC interrupts to PCI
[   32.331353] Yenta: Routing CardBus interrupts to PCI
[   32.331357] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
[   32.346847] input: PC Speaker as /class/input/input1
[   32.583589] Yenta: ISA IRQ mask 0x06f8, PCI irq 169
[   32.583594] Socket status: 30000006
[   32.597608] ieee80211_crypt: registered algorithm 'NULL'
[   32.666551] ieee80211: 802.11 data/management/control stack, git-1.1.7
[   32.666556] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   32.776560] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 177
[   32.792975] usbcore: registered new driver hiddev
[   32.802570] input: PS/2+USB Mouse as /class/input/input2
[   32.802799] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:03.0-2[   32.802811] usbcore: registered new driver usbhid
[   32.802814] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   32.815694] bcm43xx driver
[   32.861301] ts: Compaq touchscreen protocol output
[   33.120162] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   33.157728] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   33.607772] intel8x0_measure_ac97_clock: measured 59438 usecs
[   33.607776] intel8x0: clocking to 48000
[   33.609129] GSI 22 sharing vector 0xD9 and IRQ 22
[   33.609135] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 217
[   33.614242] NET: Registered protocol family 17
[   33.866817] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   33.875627] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   33.972728] lp: driver loaded but no devices found
[   34.037050] Adding 2626588k swap on /dev/hda5.  Priority:-1 extents:1 across:2626588k
[   34.118030] EXT3 FS on hda1, internal journal
[   34.320284] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   34.320289] md: bitmap version 4.39
[   34.583160] eth0: Media Link On 100mbps full-duplex
[   35.287922] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   35.812018] cdrom: open failed.
[   38.862476] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   40.009251] NET: Registered protocol family 10
[   40.009385] lo: Disabled Privacy Extensions
[   40.009580] IPv6 over IPv4 tunneling driver
[   41.783371] ACPI: AC Adapter [ACAD] (on-line)
[   41.806433] ACPI: Battery Slot [BAT1] (battery present)
[   41.874453] ACPI: Power Button (FF) [PWRF]
[   41.874473] ACPI: Lid Switch [LID]
[   41.874478] ACPI: Power Button (CM) [PWRB]
[   41.874483] ACPI: Sleep Button (CM) [SLPB]
[   41.950456] ibm_acpi: ec object not found
[   41.974252] pcc_acpi: loading...
[   42.465681] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[   42.465719] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4 (1450 mV)
[   42.465722] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[   42.465726] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[   42.465731] cpu_init done, current fid 0xa, vid 0x4
[   48.257440] ppdev: user-space parallel port driver
[   50.394192] eth0: no IPv6 routers present
[   52.594906] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   53.726458] Bluetooth: Core ver 2.8
[   53.726464] NET: Registered protocol family 31
[   53.726466] Bluetooth: HCI device and connection manager initialized
[   53.726478] Bluetooth: HCI socket layer initialized
[   53.835056] Bluetooth: L2CAP ver 2.8
[   53.835062] Bluetooth: L2CAP socket layer initialized
[   53.919257] Bluetooth: RFCOMM socket layer initialized
[   53.919279] Bluetooth: RFCOMM TTY layer initialized
[   53.919281] Bluetooth: RFCOMM ver 1.7
[   57.055347] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   64.521622] eth0: no IPv6 routers present
[   68.085459] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   79.103300] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   90.144257] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  101.162146] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  112.180946] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  169.705757] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  198.334787] ibm_acpi: ec object not found
[  228.710916] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  286.017300] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  342.433543] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed."

---

### Post by friedokra on 2006-08-05
and then when I type (in my terminal) "iwconfig" and get back: 

"lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions."
---------------------------------------------------------------------------
I try to get onto the wireless internet (at several places) and it does not recognize any network. I have wi-fi radar (a program) and network manager (another program) and I cannot get wireless internet to work! I have spent countless hours trying to figure this out. Did I screw up something before  ([http://www.ubuntuforums.org/showthread.php?t=224260](http://www.ubuntuforums.org/showthread.php?t=224260)) that is preventing me from acheiving success now? If anyone knows where I am going wrong, please help. I want to figure this out and school is approaching soon:confused: =

---

### Post by friedokra on 2006-08-06
:KS :KS problem solved....see beginner forums!

---

### Post by compwiz18 on 2006-09-28
To save everyone else the trouble of finding his post in the beginner forums: [http://ubuntuforums.org/showthread.php?t=230450](http://ubuntuforums.org/showthread.php?t=230450)

---

### Post by reedatschool on 2006-10-10
Sweet!  This fixed my wireless problem running Egdy with the latest Kernel (Using the 4311 Broadcom Chipset on a presario V3000).  

Kudos,

Reed

---

