---
title: "update to 6.10 - x server doesn't start"
date: 2006-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by alion on 2006-11-10
I did apt-get dist-upgrade, it upgrated my system to 6.10.
On startup I get error "Failed to start x server".
 I see that such error already occured in August. I need to roll back to the previous version of xserver-xorg-core...?
Is there a new, corrected version of it?

---

### Post by kleeman on 2006-11-10
Login without X and checkout the file /var/log/Xorg.0.log . Search for lines starting (EE) and post them here. Also post dmesg and your graphics card as well as /etc/X11/xorg.conf

---

### Post by alion on 2006-11-10
So my dmsg content:
```

[    0.000000] Bootdata ok (command line is root=UUID=9aa8c689-8453-4128-990f-a3305c2ec451 ro quiet splash)
[    0.000000] Linux version 2.6.17-10-generic (root@crested) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 15:34:39 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffde000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000f9210
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000528 MSFT 0x00000097) @ 0x000000007ffd0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x07000528 MSFT 0x00000097) @ 0x000000007ffd0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x07000528 MSFT 0x00000097) @ 0x000000007ffd0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x07000528 MSFT 0x00000097) @ 0x000000007ffde040
[    0.000000] ACPI: DSDT (v001  1XXXX 1XXXX005 0x00000005 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000007ffd0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffd0000
[    0.000000] On node 0 totalpages: 515624
[    0.000000]   DMA zone: 2591 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 513033 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ d0000000 size 128 MB
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=UUID=9aa8c689-8453-4128-990f-a3305c2ec451 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 1800.085 MHz processor.
[   22.243089] Console: colour VGA+ 80x25
[   22.244259] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   22.245930] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.271061] Memory: 2052024k/2096960k available (2129k kernel code, 44548k reserved, 1424k data, 188k init)
[   22.347155] Calibrating delay using timer specific routine.. 3605.31 BogoMIPS (lpj=7210639)
[   22.347210] Security Framework v1.0.0 initialized
[   22.347216] SELinux:  Disabled at boot.
[   22.347237] Mount-cache hash table entries: 256
[   22.347371] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.347375] CPU: L2 Cache: 512K (64 bytes/line)
[   22.347378] CPU 0/0(1) -> Node 0 -> Core 0
[   22.347393] SMP alternatives: switching to UP code
[   22.347645] checking if image is initramfs... it is
[   23.012096] Freeing initrd memory: 7219k freed
[   23.016308] ACPI: Core revision 20060707
[   23.016779] ACPI: Looking for DSDT ... not found!
[   23.059821] Using local APIC timer interrupts.
[   23.115293] result 12500599
[   23.115295] Detected 12.500 MHz APIC timer.
[   23.118074] Brought up 1 CPUs
[   23.118204] testing NMI watchdog ... OK.
[   23.158245] migration_cost=0
[   23.158489] NET: Registered protocol family 16
[   23.158517] ACPI: bus type pci registered
[   23.158525] PCI: Using configuration type 1
[   23.164749] ACPI: Interpreter enabled
[   23.164751] ACPI: Using IOAPIC for interrupt routing
[   23.165463] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.165466] PCI: Probing PCI hardware (bus 00)
[   23.169134] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[   23.169496] PCI: Quirk-MSI-K8T Soundcard On
[   23.169499] PCI: Unexpected Value in PCI-Register: no Change!
[   23.169719] Boot video device is 0000:01:00.0
[   23.169795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.196123] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   23.196369] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   23.196614] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   23.197092] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.197339] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.197582] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.197828] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.198082] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.198161] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.198171] pnp: PnP ACPI init
[   23.203489] pnp: PnP ACPI: found 14 devices
[   23.203541] PCI: Using ACPI for IRQ routing
[   23.203544] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.203719] agpgart: Detected AGP bridge 0
[   23.207680] agpgart: AGP aperture is 128M @ 0xd0000000
[   23.207700] PCI-DMA: Disabling IOMMU.
[   23.208425] pnp: 00:0a: ioport range 0x680-0x6ff has been reserved
[   23.208429] pnp: 00:0a: ioport range 0x295-0x296 has been reserved
[   23.208620] PCI: Bridge: 0000:00:01.0
[   23.208623]   IO window: disabled.
[   23.208628]   MEM window: faf00000-fbffffff
[   23.208632]   PREFETCH window: e0000000-f9ffffff
[   23.208653] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.208702] NET: Registered protocol family 2
[   23.245887] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   23.246226] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   23.249372] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   23.250006] TCP: Hash tables configured (established 262144 bind 65536)
[   23.250009] TCP reno registered
[   23.250365] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   23.250709] audit: initializing netlink socket (disabled)
[   23.250719] audit(1163182994.016:1): initialized
[   23.250860] VFS: Disk quotas dquot_6.5.1
[   23.250878] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.250924] Initializing Cryptographic API
[   23.250928] io scheduler noop registered
[   23.250935] io scheduler anticipatory registered
[   23.250942] io scheduler deadline registered
[   23.250958] io scheduler cfq registered (default)
[   23.271937] Real Time Clock Driver v1.12ac
[   23.271975] Linux agpgart interface v0.101 (c) Dave Jones
[   23.271978] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.272095] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.272606] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.272791] mice: PS/2 mouse device common for all mice
[   23.273276] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.273464] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   23.273468] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   23.273741] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   23.273986] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.274001] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.274219] TCP bic registered
[   23.274228] NET: Registered protocol family 1
[   23.274234] NET: Registered protocol family 8
[   23.274236] NET: Registered protocol family 20
[   23.274400] ACPI: (supports S0 S1 S3 S4 S5)
[   23.274442] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.274462] Freeing unused kernel memory: 188k freed
[   23.295224] input: AT Translated Set 2 keyboard as /class/input/input0
[   23.327376] vga16fb: initializing
[   23.327381] vga16fb: mapped to 0xffff8100000a0000
[   23.480221] Console: switching to colour frame buffer device 80x25
[   23.480227] fb0: VGA16 VGA frame buffer device
[   24.518210] Capability LSM initialized
[   24.550760] ACPI: Processor [CPU1] (supports 16 throttling states)
[   24.550769] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   24.550775] ACPI: Getting cpuindex for acpiid 0x2
[   24.931707] SCSI subsystem initialized
[   24.935466] libata version 1.20 loaded.
[   24.936562] sata_via 0000:00:0f.0: version 1.1
[   24.936584] GSI 16 sharing vector 0xA9 and IRQ 16
[   24.936587] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[   24.936598] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 9
[   24.936630] sata_via 0000:00:0f.0: routed to hard irq line 9
[   24.936675] ata1: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xD000 irq 169
[   24.936696] ata2: SATA max UDMA/133 cmd 0xD800 ctl 0xD402 bmdma 0xD008 irq 169
[   25.107376] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   25.107382] ata1: dev 0 ATA-6, max UDMA/133, 234441648 sectors: LBA48
[   25.119230] ata1: dev 0 configured for UDMA/133
[   25.119233] scsi0 : sata_via
[   25.290326] scsi1 : sata_via
[   25.290501]   Vendor: ATA       Model: ST3120827AS       Rev: 3.42
[   25.290509]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   25.298588] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   25.298600] sda: Write Protect is off
[   25.298603] sda: Mode Sense: 00 3a 00 00
[   25.298616] SCSI device sda: drive cache: write back
[   25.298665] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   25.298674] sda: Write Protect is off
[   25.298676] sda: Mode Sense: 00 3a 00 00
[   25.298688] SCSI device sda: drive cache: write back
[   25.298693]  sda: sda1 sda2 sda3 sda4
[   25.339164] sd 0:0:0:0: Attached scsi disk sda
[   25.617877] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   25.617897] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[   25.617904] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 9
[   25.617929] VP_IDE: chipset revision 6
[   25.617932] VP_IDE: not 100% native mode: will probe irqs later
[   25.617943] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   25.617951]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[   25.617965]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   25.617976] Probing IDE interface ide0...
[   26.189354] Probing IDE interface ide1...
[   27.060148] hdc: SONY DVD-ROM DDU1613, ATAPI CD/DVD-ROM drive
[   27.395657] ide1 at 0x170-0x177,0x376 on irq 15
[   27.403539] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   27.403546] Uniform CD-ROM driver Revision: 3.20
[   27.459773] Probing IDE interface ide0...
[   27.511107] usbcore: registered new driver usbfs
[   27.511132] usbcore: registered new driver hub
[   27.512101] USB Universal Host Controller Interface driver v3.0
[   27.512152] GSI 17 sharing vector 0xB1 and IRQ 17
[   27.512156] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 177
[   27.512167] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 1
[   27.512192] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   27.512322] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   27.512356] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000c400
[   27.512432] usb usb1: configuration #1 chosen from 1 choice
[   27.512452] hub 1-0:1.0: USB hub found
[   27.512458] hub 1-0:1.0: 2 ports detected
[   27.619405] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 177
[   27.619411] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[   27.619437] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   27.619536] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   27.619562] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000c000
[   27.619713] usb usb2: configuration #1 chosen from 1 choice
[   27.619814] hub 2-0:1.0: USB hub found
[   27.619822] hub 2-0:1.0: 2 ports detected
[   27.727133] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 177
[   27.727138] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 1
[   27.727160] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   27.727255] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   27.727276] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000b800
[   27.727432] usb usb3: configuration #1 chosen from 1 choice
[   27.727534] hub 3-0:1.0: USB hub found
[   27.727541] hub 3-0:1.0: 2 ports detected
[   27.834976] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 177
[   27.834981] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 1
[   27.835003] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   27.835104] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   27.835126] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000b400
[   27.835270] usb usb4: configuration #1 chosen from 1 choice
[   27.835374] hub 4-0:1.0: USB hub found
[   27.835381] hub 4-0:1.0: 2 ports detected
[   27.942902] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 177
[   27.942907] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 1
[   27.943041] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   27.943269] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   27.943312] ehci_hcd 0000:00:10.4: irq 177, io mem 0xfaeff800
[   27.943321] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.943467] usb usb5: configuration #1 chosen from 1 choice
[   27.943578] hub 5-0:1.0: USB hub found
[   27.943586] hub 5-0:1.0: 8 ports detected
[   28.115682] kjournald starting.  Commit interval 5 seconds
[   28.115692] EXT3-fs: mounted filesystem with ordered data mode.
[   39.016355] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.022635] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.250819] Floppy drive(s): fd0 is 1.44M
[   39.267788] r8169 Gigabit Ethernet driver 2.2LK loaded
[   39.267813] GSI 18 sharing vector 0xB9 and IRQ 18
[   39.267816] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 185
[   39.267969] eth0: Identified chip type is 'RTL8169s/8110s'.
[   39.267974] eth0: RTL8169 at 0xffffc20000042c00, 00:11:09:61:63:61, IRQ 185
[   39.278441] FDC 0 is a post-1991 82077
[   39.588129] parport: PnPBIOS parport detected.
[   39.588179] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   39.659723] input: PC Speaker as /class/input/input1
[   40.094700] r8169: eth0: link down
[   40.216616] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.247289] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   40.317133] ts: Compaq touchscreen protocol output
[   40.357658] GSI 19 sharing vector 0xC1 and IRQ 19
[   40.357663] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
[   40.357674] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 1
[   40.357829] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   40.987638] r8169: eth0: link up
[   41.102228] lp0: using parport0 (interrupt-driven).
[   41.183472] Adding 2008116k swap on /dev/disk/by-uuid/badec5e7-0d72-45bd-8a7d-69939008a017.  Priority:-1 extents:1 across:2008116k
[   41.278970] EXT3 FS on sda3, internal journal
[   41.453942] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   41.453947] md: bitmap version 4.39
[   41.600366] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[   42.603958] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   42.650256] NTFS volume version 3.1.
[   42.700079] NTFS volume version 3.1.
[   43.949359] NET: Registered protocol family 17
[   47.570405] NET: Registered protocol family 10
[   47.570492] lo: Disabled Privacy Extensions
[   47.570616] IPv6 over IPv4 tunneling driver
[   49.322755] ACPI: Power Button (FF) [PWRF]
[   49.322781] ACPI: Sleep Button (CM) [SLPB]
[   49.322786] ACPI: Power Button (CM) [PWRB]
[   49.411177] ibm_acpi: ec object not found
[   49.441855] pcc_acpi: loading...
[   49.733640] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   49.741489] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   54.630284] Bluetooth: Core ver 2.8
[   54.630289] NET: Registered protocol family 31
[   54.630292] Bluetooth: HCI device and connection manager initialized
[   54.630306] Bluetooth: HCI socket layer initialized
[   54.658493] Bluetooth: L2CAP ver 2.8
[   54.658496] Bluetooth: L2CAP socket layer initialized
[   54.684901] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[   54.698832] Bluetooth: RFCOMM socket layer initialized
[   54.698848] Bluetooth: RFCOMM TTY layer initialized
[   54.698850] Bluetooth: RFCOMM ver 1.7
[   58.380312] eth0: no IPv6 routers present


```
Video card info, from lspci:
```
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

Contents of Xorg.log
```

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 10 14:21:15 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
....
.....
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded


```

---

### Post by ner0tic on 2006-11-10
first things first try this:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by alion on 2006-11-10
Thank you for reply. I found that the xserver-xorg package was not fully installed for some reason. I did usual apt-get install xserver-org, it downloaded&installed remained parts. Now everything works like a charm.

---

