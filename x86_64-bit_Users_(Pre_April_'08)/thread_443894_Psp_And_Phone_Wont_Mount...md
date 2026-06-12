---
title: "Psp And Phone Wont Mount.."
date: 2007-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by zorro26 on 2007-05-14
HI GUYS, I AM NEW TO LINUX, WELL HAVE BEEN USING IT FOR FEW MONTHS, INSTALLED IT QUITE FEW TIME, PLAYED AROUND ALOT AND LEARNT ALOT. PROBLEM I AM HAVING IS I TRIED TO MOUNT MY PSP BUT IT WONT WORK, I USE TO MOUNT MY SAMSUNG I300 WHICH USES MASS STORAGE FORMULA USED TO MOUND FOR FEW MINS UNDER TFAT FOLDERS OR SOMETHING BUT THAT NOT HAPPENING NOW. 

I SEARCHED UBUNTU, LINUX, PSP FORUMS AND GOOGLED ALOT. I FOLLWED AND DIDT LOADS OF STUFF (I JUST COPY AND PASTE COMANDS IN TERMINAL WITH OUT KNOWING WHAT THEY MEAN).

like these

mount -t vfat /dev/sda /mnt/psp/ 
but i get this 
mount: special device /dev/sda does not exist

CHANGED MY FSTAB FILES LOADS .. NOW IT LOOKS LIKE THIS..
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=57a37a62-927c-4715-9cfb-ec1e5639812d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f8f64f27-3e09-4dd8-8fdc-4968f1ddc584 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


MY  DMESG IS AS FOLLOWING 
> [    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=57a37a62-927c-4715-9cfb-ec1e5639812d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff10000 (usable)
[    0.000000]  BIOS-e820: 000000003ff10000 - 000000003ff20000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff20000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261904) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000fad60
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x10000507 MSFT 0x00000097) @ 0x000000003ff10000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x10000507 MSFT 0x00000097) @ 0x000000003ff10200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x10000507 MSFT 0x00000097) @ 0x000000003ff10390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x10000507 MSFT 0x00000097) @ 0x000000003ff20040
[    0.000000] ACPI: DSDT (v001  A0217 A0217001 0x00000001 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ff10000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261904) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff10000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261904
[    0.000000] On node 0 totalpages: 261807
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1085 pages reserved
[    0.000000]   DMA zone: 2858 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254284 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
[    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257142
[    0.000000] Kernel command line: root=UUID=57a37a62-927c-4715-9cfb-ec1e5639812d ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   12.538643] Console: colour VGA+ 80x25
[   12.539718] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.540346] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   12.540440] Checking aperture...
[   12.540444] CPU 0: aperture @ 9812000000 size 32 MB
[   12.540446] Aperture too small (32 MB)
[   12.545809] No AGP bridge found
[   12.559141] Memory: 1019564k/1047616k available (2217k kernel code, 27664k reserved, 1162k data, 304k init)
[   12.635510] Calibrating delay using timer specific routine.. 4402.47 BogoMIPS (lpj=8804958)
[   12.635569] Security Framework v1.0.0 initialized
[   12.635575] SELinux:  Disabled at boot.
[   12.635601] Mount-cache hash table entries: 256
[   12.635766] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.635768] CPU: L2 Cache: 1024K (64 bytes/line)
[   12.635771] CPU 0/0 -> Node 0
[   12.635794] SMP alternatives: switching to UP code
[   12.636186] Early unpacking initramfs... done
[   12.940107] ACPI: Core revision 20060707
[   12.940583] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   12.982825] Using local APIC timer interrupts.
[   13.028238] result 12501014
[   13.028240] Detected 12.501 MHz APIC timer.
[   13.031224] Brought up 1 CPUs
[   13.031251] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   13.031253] time.c: Detected 2200.178 MHz processor.
[   13.031548] Time:  0:59:29  Date: 04/15/107
[   13.031586] NET: Registered protocol family 16
[   13.031670] ACPI: bus type pci registered
[   13.031676] PCI: Using configuration type 1
[   13.037952] ACPI: Interpreter enabled
[   13.037954] ACPI: Using IOAPIC for interrupt routing
[   13.038851] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.038855] PCI: Probing PCI hardware (bus 00)
[   13.039498] Boot video device is 0000:03:00.0
[   13.039676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.058677] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   13.058930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   13.059828] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   13.060041] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[   13.060251] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[   13.060459] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   13.060722] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[   13.060934] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[   13.061146] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[   13.061356] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[   13.061428] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.061435] pnp: PnP ACPI init
[   13.067522] pnp: PnP ACPI: found 15 devices
[   13.067571] PCI: Using ACPI for IRQ routing
[   13.067574] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.067640] NET: Registered protocol family 8
[   13.067642] NET: Registered protocol family 20
[   13.068439] pnp: 00:0a: ioport range 0xc00-0xc0f has been reserved
[   13.068442] pnp: 00:0a: ioport range 0xd00-0xd0f has been reserved
[   13.068444] pnp: 00:0a: ioport range 0xa20-0xa2f has been reserved
[   13.068447] pnp: 00:0a: ioport range 0xa30-0xa3f has been reserved
[   13.068682] PCI: Bridge: 0000:00:01.0
[   13.068684]   IO window: e000-efff
[   13.068688]   MEM window: dff00000-dfffffff
[   13.068691]   PREFETCH window: dc000000-deffffff
[   13.068695] PCI: Bridge: 0000:00:06.0
[   13.068697]   IO window: d000-dfff
[   13.068700]   MEM window: disabled.
[   13.068702]   PREFETCH window: disabled.
[   13.068705] PCI: Bridge: 0000:00:07.0
[   13.068707]   IO window: c000-cfff
[   13.068710]   MEM window: disabled.
[   13.068712]   PREFETCH window: disabled.
[   13.068727] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.068735] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.068743] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.068805] NET: Registered protocol family 2
[   13.095204] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   13.095515] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   13.097287] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.098169] TCP: Hash tables configured (established 131072 bind 65536)
[   13.098172] TCP reno registered
[   13.107257] checking if image is initramfs... it is
[   13.671335] Freeing initrd memory: 7303k freed
[   13.678341] audit: initializing netlink socket (disabled)
[   13.678354] audit(1179190769.096:1): initialized
[   13.678493] VFS: Disk quotas dquot_6.5.1
[   13.678511] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.678557] io scheduler noop registered
[   13.678559] io scheduler anticipatory registered
[   13.678561] io scheduler deadline registered
[   13.678571] io scheduler cfq registered (default)
[   13.738721] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.738746] assign_interrupt_mode Found MSI capability
[   13.738749] Allocate Port Service[0000:00:01.0:pcie00]
[   13.758732] Real Time Clock Driver v1.12ac
[   13.758770] Linux agpgart interface v0.102 (c) Dave Jones
[   13.758773] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.758885] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.759352] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.759506] mice: PS/2 mouse device common for all mice
[   13.759968] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.760192] input: Macintosh mouse button emulation as /class/input/input0
[   13.760219] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.760223] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.760424] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   13.760582] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.760585] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.760758] TCP cubic registered
[   13.760766] NET: Registered protocol family 1
[   13.760874] ACPI: (supports S0 S1 S3 S4 S5)
[   13.760909]   Magic number: 7:558:961
[   13.760922]   hash matches device ttyb2
[   13.761028] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   13.761136] Freeing unused kernel memory: 304k freed
[   13.780019] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.922542] Capability LSM initialized
[   14.950861] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   15.426946] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   15.426971] SIS5513: chipset revision 1
[   15.426973] SIS5513: not 100% native mode: will probe irqs later
[   15.426979] SIS5513: SiS965 ATA 133 (2nd gen) controller
[   15.426991]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   15.427001]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   15.427008] Probing IDE interface ide0...
[   15.455294] usbcore: registered new interface driver usbfs
[   15.455315] usbcore: registered new interface driver hub
[   15.455334] usbcore: registered new device driver usb
[   15.455927] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   15.509081] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   15.509084] Copyright (c) 1999-2006 Intel Corporation.
[   15.581643] Floppy drive(s): fd0 is 1.44M
[   15.625832] FDC 0 is a post-1991 82077
[   15.724935] hda: Maxtor 6L160P0, ATA DISK drive
[   16.401702] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   16.423538] Probing IDE interface ide1...
[   17.163644] hdc: SONY DVD RW DW-G120A, ATAPI CD/DVD-ROM drive
[   17.839166] ide1 at 0x170-0x177,0x376 on irq 15
[   17.852329] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   17.852343] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   17.852603] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   17.852617] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfeb8000
[   17.913280] usb usb1: configuration #1 chosen from 1 choice
[   17.913423] hub 1-0:1.0: USB hub found
[   17.913432] hub 1-0:1.0: 3 ports detected
[   18.019163] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[   18.019177] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   18.019296] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   18.019309] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfeb9000
[   18.081035] usb usb2: configuration #1 chosen from 1 choice
[   18.081175] hub 2-0:1.0: USB hub found
[   18.081182] hub 2-0:1.0: 3 ports detected
[   18.187023] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[   18.187036] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   18.187152] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   18.187166] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdfeba000
[   18.248937] usb usb3: configuration #1 chosen from 1 choice
[   18.249085] hub 3-0:1.0: USB hub found
[   18.249093] hub 3-0:1.0: 2 ports detected
[   18.360641] SCSI subsystem initialized
[   18.365563] libata version 2.20 loaded.
[   18.372807] sata_sis 0000:00:05.0: version 0.7
[   18.372833] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.372847] sata_sis 0000:00:05.0: Detected SiS 182/965L chipset
[   18.372914] ata1: SATA max UDMA/133 cmd 0x000000000001b400 ctl 0x000000000001b002 bmdma 0x000000000001a000 irq 17
[   18.372944] ata2: SATA max UDMA/133 cmd 0x000000000001a800 ctl 0x000000000001a402 bmdma 0x000000000001a008 irq 17
[   18.372960] scsi0 : sata_sis
[   18.380060] hda: max request size: 512KiB
[   18.385519] hda: 320173056 sectors (163928 MB) w/8192KiB Cache, CHS=19929/255/63, UDMA(133)
[   18.395927] hda: cache flushes supported
[   18.395971]  hda: hda1 hda2 < hda5 >
[   18.446185] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   18.446192] Uniform CD-ROM driver Revision: 3.20
[   18.570410] Attempting manual resume
[   18.570414] swsusp: Resume From Partition 3:5
[   18.570415] PM: Checking swsusp image.
[   18.570519] PM: Resume from disk failed.
[   18.582914] EXT3-fs: INFO: recovery required on readonly filesystem.
[   18.582918] EXT3-fs: write access will be enabled during recovery.
[   20.584431] ata1: SATA link down (SStatus 1 SControl 300)
[   20.595008] ATA: abnormal status 0x7F on port 0x000000000001b407
[   20.595047] scsi1 : sata_sis
[   22.319900] kjournald starting.  Commit interval 5 seconds
[   22.319913] EXT3-fs: recovery complete.
[   22.322843] EXT3-fs: mounted filesystem with ordered data mode.
[   22.802444] ata2: SATA link down (SStatus 1 SControl 300)
[   22.813021] ATA: abnormal status 0x7F on port 0x000000000001a807
[   22.813811] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   23.063612] e1000: 0000:00:0b.0: e1000_probe: (PCI:33MHz:32-bit) 00:15:f2:4f:e2:10
[   23.102889] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   23.102997] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[   23.103006] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   23.103029] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   23.103065] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   23.103076] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdfebb000
[   23.103083] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.103156] usb usb4: configuration #1 chosen from 1 choice
[   23.103179] hub 4-0:1.0: USB hub found
[   23.103185] hub 4-0:1.0: 8 ports detected
[   31.646880] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   32.939156] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.000334] NET: Registered protocol family 17
[   33.250705] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.279883] input: PC Speaker as /class/input/input2
[   33.421572] parport: PnPBIOS parport detected.
[   33.421614] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   33.525389] logips2pp: Detected unknown logitech mouse model 1
[   33.623931] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[   33.709227] input: PS/2 Logitech Mouse as /class/input/input3
[   33.944457] intel8x0_measure_ac97_clock: measured 55792 usecs
[   33.944460] intel8x0: clocking to 48000
[   34.093878] fuse init (API version 7.8)
[   34.115151] lp0: using parport0 (interrupt-driven).
[   34.157944] Adding 3004112k swap on /dev/disk/by-uuid/f8f64f27-3e09-4dd8-8fdc-4968f1ddc584.  Priority:-1 extents:1 across:3004112k
[   34.272425] EXT3 FS on hda1, internal journal
[   38.769132] NET: Registered protocol family 10
[   38.769223] lo: Disabled Privacy Extensions
[   41.805027] Using specific hotkey driver
[   41.822829] No dock devices found.
[   41.853159] input: Power Button (FF) as /class/input/input4
[   41.856788] ACPI: Power Button (FF) [PWRF]
[   41.879768] input: Power Button (CM) as /class/input/input5
[   41.883350] ACPI: Power Button (CM) [PWRB]
[   41.969888] ibm_acpi: ec object not found
[   42.010174] pcc_acpi: loading...
[   42.223683] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (version 2.00.00)
[   42.223731] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   42.223734] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[   42.223736] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   42.223738] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   45.321735] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   45.327624] [fglrx] Maximum main memory to use for locked dma buffers: 921 MBytes.
[   45.327863] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   45.588663] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.003054] ppdev: user-space parallel port driver
[   48.902423] [fglrx] total      GART = 130023424
[   48.902429] [fglrx] free       GART = 114032640
[   48.902431] [fglrx] max single GART = 114032640
[   48.902433] [fglrx] total      LFB  = 33423360
[   48.902435] [fglrx] free       LFB  = 21884928
[   48.902437] [fglrx] max single LFB  = 21884928
[   48.902438] [fglrx] total      Inv  = 0
[   48.902439] [fglrx] free       Inv  = 0
[   48.902441] [fglrx] max single Inv  = 0
[   48.902442] [fglrx] total      TIM  = 0
[   51.730903] Bluetooth: Core ver 2.11
[   51.730940] NET: Registered protocol family 31
[   51.730941] Bluetooth: HCI device and connection manager initialized
[   51.730944] Bluetooth: HCI socket layer initialized
[   51.779015] Bluetooth: L2CAP ver 2.8
[   51.779018] Bluetooth: L2CAP socket layer initialized
[   51.898146] Bluetooth: RFCOMM socket layer initialized
[   51.898156] Bluetooth: RFCOMM TTY layer initialized
[   51.898157] Bluetooth: RFCOMM ver 1.8
[   55.340546] eth0: no IPv6 routers present
[  160.817770] usb 3-2: new full speed USB device using ohci_hcd and address 2
[  162.260130] usb 3-2: device descriptor read/64, error -110
[  164.850506] usb 3-2: new full speed USB device using ohci_hcd and address 3
[  166.374605] usb 3-2: new full speed USB device using ohci_hcd and address 4
[  167.816958] usb 3-2: device descriptor read/64, error -110
[  171.962292] usb 2-2: new full speed USB device using ohci_hcd and address 2
[  173.404637] usb 2-2: device descriptor read/64, error -110
[  181.691907] usb 2-2: device descriptor read/64, error -110
[  181.819065] usb 2-2: new full speed USB device using ohci_hcd and address 3
[  183.259578] usb 2-2: device descriptor read/64, error -110
[  191.998616] usb 2-2: device descriptor read/64, error -110
[  192.125774] usb 2-2: new full speed USB device using ohci_hcd and address 4
[  194.407572] usb 2-2: device descriptor read/8, error -110
[  196.732691] usb 2-2: device descriptor read/8, error -110
[  196.859637] usb 2-2: new full speed USB device using ohci_hcd and address 5
[  199.139558] usb 2-2: device descriptor read/8, error -110
[  201.464691] usb 2-2: device descriptor read/8, error -110

CAN SOMEONE BE PATIENT ENOUGH TO HELP ME WITH SLOW STEPS STARTING FROM STEP ONE..

---

### Post by dfreer on 2007-05-14
please don't shout, it's not going to get your question answered any faster (if anything people won't even bother to read your message). it looks like from dmesg that it is causing a bunch of errors. 

try this out:
[http://ubuntuforums.org/showthread.php?t=58380](http://ubuntuforums.org/showthread.php?t=58380)

EDIT: Also, this thread isn't even in the right section, so that might hurt your chances of getting your questions answered even further

---

### Post by zorro26 on 2007-05-15
sorry i didnt ment to shout just left my caps on, 
thanks for the link but no that dosnt help cause i dont have sda1 file in dev folder. can you  pls tell me what would be the right forum so i can ask my ques there. thankyou

---

### Post by dfreer on 2007-05-15
hey, no worries :) 
well, normally you should have posted in "Hardware and laptops" or "Gaming and leisure".
I'm not much help cuz I don't have a PSP. but from your dmesg it doesn't look like it is recognizing the PSP right. You might make a new post in those sections showing the output from
```
dmesg | tail
```
and ask how to get ubuntu to recognize the PSP. Good luck!

---

