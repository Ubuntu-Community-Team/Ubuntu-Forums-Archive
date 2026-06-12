---
title: "CDROM doesn't work! :("
date: 2007-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by imablackhat on 2007-07-25
Okay well, my CDROM drive is supposed to be /dev/hda in Ubuntu, but there is no /dev/hda, or /dev/cdrom or sda, etc, there are /dev/hdd,hdc,hdb (those are my 3 hard drives).... The CDROM drive works obviously because I installed Ubuntu, and it works in the Bios and back when I used to use Windows... Heres how my Bios is kinda setup:

Primary: NEC DVDRW CDROM DRIVE
Secondary: A hard drive
Primary: A hard drive
Secondary: A hard drive

(I don't see how it would matter if I set my CDROM to secondary because either way it should be picked up but its not).

Any help at all is appreciated.

---

### Post by imablackhat on 2007-07-25
Oh and by the way, some people were asking me to post my dmesg, so here it is....

dmesg

[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=8ff7598f-0d60-4204-a80e-d9983343389f ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 VIAK8T                                ) @ 0x00000000000f79f0
[    0.000000] ACPI: RSDT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee3040
[    0.000000] ACPI: FADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee30c0
[    0.000000] ACPI: MADT (v001 VIAK8T AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fee82c0
[    0.000000] ACPI: DSDT (v001 VIAK8T AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261856
[    0.000000] On node 0 totalpages: 261759
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1086 pages reserved
[    0.000000]   DMA zone: 2857 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254236 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257093
[    0.000000] Kernel command line: root=UUID=8ff7598f-0d60-4204-a80e-d9983343389f ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   23.533021] Console: colour VGA+ 80x25
[   23.533844] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.535160] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   23.535254] Checking aperture...
[   23.535258] CPU 0: aperture @ f0000000 size 128 MB
[   23.548028] Memory: 1019880k/1047424k available (2217k kernel code, 27156k reserved, 1162k data, 304k init)
[   23.625206] Calibrating delay using timer specific routine.. 4404.77 BogoMIPS (lpj=8809549)
[   23.625260] Security Framework v1.0.0 initialized
[   23.625269] SELinux:  Disabled at boot.
[   23.625291] Mount-cache hash table entries: 256
[   23.625443] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.625445] CPU: L2 Cache: 512K (64 bytes/line)
[   23.625448] CPU 0/0 -> Node 0
[   23.625469] SMP alternatives: switching to UP code
[   23.625642] Freeing SMP alternatives: 28k freed
[   23.625748] Early unpacking initramfs... done
[   23.903633] ACPI: Core revision 20060707
[   23.906236] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.958421] Using local APIC timer interrupts.
[   24.003837] result 12498936
[   24.003838] Detected 12.498 MHz APIC timer.
[   24.004844] Brought up 1 CPUs
[   24.005041] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   24.005043] time.c: Detected 2199.809 MHz processor.
[   24.005311] Time: 23:36:18  Date: 06/25/107
[   24.005342] NET: Registered protocol family 16
[   24.005412] ACPI: bus type pci registered
[   24.005418] PCI: Using configuration type 1
[   24.012148] ACPI: Interpreter enabled
[   24.012154] ACPI: Using IOAPIC for interrupt routing
[   24.012613] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.012617] PCI: Probing PCI hardware (bus 00)
[   24.013339] PCI: MSI-K8T-Neo2Fir, attempting to turn soundcard ON
[   24.013343] PCI: MSI-K8T-Neo2Fir, soundcard on
[   24.013488] Boot video device is 0000:01:00.0
[   24.013528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.070709] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   24.071009] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   24.071312] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   24.071598] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.071867] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.072129] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.072388] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.072647] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   24.073102] ACPI: PCI Interrupt Link [ALKA] (IRQs *20), disabled.
[   24.073538] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   24.073854] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   24.074233] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[   24.076752] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.076764] pnp: PnP ACPI init
[   24.081050] pnp: PnP ACPI: found 12 devices
[   24.081101] PCI: Using ACPI for IRQ routing
[   24.081104] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.081113] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   24.081185] NET: Registered protocol family 8
[   24.081187] NET: Registered protocol family 20
[   24.081239] agpgart: Detected AGP bridge 0
[   24.085021] agpgart: AGP aperture is 128M @ 0xf0000000
[   24.085453] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[   24.085456] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[   24.085683] PCI: Bridge: 0000:00:01.0
[   24.085685]   IO window: disabled.
[   24.085688]   MEM window: f8000000-faffffff
[   24.085692]   PREFETCH window: e0000000-efffffff
[   24.085705] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.085761] NET: Registered protocol family 2
[   24.124745] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   24.124956] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   24.126735] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   24.127649] TCP: Hash tables configured (established 131072 bind 65536)
[   24.127652] TCP reno registered
[   24.136801] checking if image is initramfs... it is
[   24.694637] Freeing initrd memory: 6824k freed
[   24.700544] audit: initializing netlink socket (disabled)
[   24.700559] audit(1185406578.124:1): initialized
[   24.700692] VFS: Disk quotas dquot_6.5.1
[   24.700709] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.700753] io scheduler noop registered
[   24.700755] io scheduler anticipatory registered
[   24.700757] io scheduler deadline registered
[   24.700768] io scheduler cfq registered (default)
[   24.720400] Real Time Clock Driver v1.12ac
[   24.720441] Linux agpgart interface v0.102 (c) Dave Jones
[   24.720444] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.720547] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.720658] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.721044] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.721221] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.721378] mice: PS/2 mouse device common for all mice
[   24.721821] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.722000] input: Macintosh mouse button emulation as /class/input/input0
[   24.722028] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.722031] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.722263] PNP: No PS/2 controller found. Probing ports directly.
[   24.722705] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.722709] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.722853] TCP cubic registered
[   24.722860] NET: Registered protocol family 1
[   24.722963] ACPI: (supports S0 S1 S4 S5)
[   24.723004]   Magic number: 15:905:656
[   24.723117] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.723214] Freeing unused kernel memory: 304k freed
[   25.904121] Capability LSM initialized
[   25.932736] ACPI: Fan [FAN] (on)
[   25.936580] ACPI: Thermal Zone [THRM] (40 C)
[   26.392563] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.14
[   26.392568] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
[   26.392570] Copyright (c) 2004 Red Hat Inc.
[   26.392589] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 17 (level, low) -> IRQ 17
[   26.393268] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
[   26.393271] eth0: Ethernet Address: 00:69:00:1C:10:6B
[   26.402867] ieee1394: Initialized config rom entry `ip1394'
[   26.414466] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[   26.470469] SCSI subsystem initialized
[   26.475247] libata version 2.20 loaded.
[   26.485321] usbcore: registered new interface driver usbfs
[   26.485341] usbcore: registered new interface driver hub
[   26.485359] usbcore: registered new device driver usb
[   26.486168] USB Universal Host Controller Interface driver v3.0
[   26.488261] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fb001000-fb0017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   26.522526] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   26.522536] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   26.522547] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   26.522685] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   26.522715] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000e300
[   26.522830] usb usb1: configuration #1 chosen from 1 choice
[   26.522852] hub 1-0:1.0: USB hub found
[   26.522859] hub 1-0:1.0: 2 ports detected
[   26.630200] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   26.630213] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   26.630232] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   26.630254] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e400
[   26.630337] usb usb2: configuration #1 chosen from 1 choice
[   26.630361] hub 2-0:1.0: USB hub found
[   26.630367] hub 2-0:1.0: 2 ports detected
[   26.647571] FDC 0 is a post-1991 82077
[   26.737994] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   26.738007] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   26.738029] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   26.738052] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e500
[   26.738138] usb usb3: configuration #1 chosen from 1 choice
[   26.738164] hub 3-0:1.0: USB hub found
[   26.738169] hub 3-0:1.0: 2 ports detected
[   26.845869] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   26.845882] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   26.845904] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   26.845926] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e600
[   26.846007] usb usb4: configuration #1 chosen from 1 choice
[   26.846030] hub 4-0:1.0: USB hub found
[   26.846035] hub 4-0:1.0: 2 ports detected
[   26.873741] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   26.953997] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   26.954013] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   26.954034] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   26.954076] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfb002000
[   26.954082] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.954157] usb usb5: configuration #1 chosen from 1 choice
[   26.954180] hub 5-0:1.0: USB hub found
[   26.954185] hub 5-0:1.0: 8 ports detected
[   27.061709] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[   27.061920] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[   27.062015] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   27.062023] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[   27.062035] VP_IDE: chipset revision 6
[   27.062036] VP_IDE: not 100% native mode: will probe irqs later
[   27.062046] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[   27.062054]     ide0: BM-DMA at 0xe200-0xe207, BIOS settings: hda:DMA, hdb:DMA
[   27.062064]     ide1: BM-DMA at 0xe208-0xe20f, BIOS settings: hdc:DMA, hdd:DMA
[   27.062071] Probing IDE interface ide0...
[   62.112519] ide0: Wait for ready failed before probe !
[   62.323574] usb 1-1: device not accepting address 2, error -71
[   62.387676] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011066600125a8c]
[   62.755201] hdb: ST3200826A, ATA DISK drive
[   62.811275] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   62.812929] Probing IDE interface ide1...
[   63.230688] hdc: ST340016A, ATA DISK drive
[   63.510387] hdd: WDC WD2500JB-55GVC0, ATA DISK drive
[   63.569000] ide1 at 0x170-0x177,0x376 on irq 15
[   63.610266] hdb: max request size: 512KiB
[   63.618417] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[   63.618525] hdb: cache flushes supported
[   63.618566]  hdb: hdb1
[   63.637563] hdc: max request size: 128KiB
[   63.637674] hdc: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   63.637678] hdc: cache flushes not supported
[   63.637695]  hdc: hdc1 hdc2 < hdc5 >
[   63.676113] hdd: max request size: 512KiB
[   63.677374] hdd: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[   63.679351] hdd: cache flushes supported
[   63.679364]  hdd: hdd1
[   63.881899] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   64.171454] usb 1-1: configuration #1 chosen from 1 choice
[   64.216791] Attempting manual resume
[   64.216795] swsusp: Resume From Partition 22:5
[   64.216797] PM: Checking swsusp image.
[   64.217029] PM: Resume from disk failed.
[   64.241207] kjournald starting.  Commit interval 5 seconds
[   64.241217] EXT3-fs: mounted filesystem with ordered data mode.
[   64.417340] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   64.604905] usb 1-2: configuration #1 chosen from 1 choice
[   64.610919] usbcore: registered new interface driver hiddev
[   64.659858] input: Chicony Saitek Eclipse II Keyboard as /class/input/input1
[   64.659871] input: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:10.0-1
[   64.811626] input: Chicony Saitek Eclipse II Keyboard as /class/input/input2
[   64.811664] input,hiddev96: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:10.0-1
[   64.814626] input: Logitech USB Gaming Mouse as /class/input/input3
[   64.814640] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:10.0-2
[   64.820588] hiddev97: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:10.0-2
[   64.820603] usbcore: registered new interface driver usbhid
[   64.820606] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   73.392214] Velocity is AUTO mode
[   74.894557] NET: Registered protocol family 17
[   75.046387] eth0: Link autonegation speed 100M bps full duplex
[   75.315109] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   75.510665] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   75.726915] input: PC Speaker as /class/input/input4
[   75.769022] parport: PnPBIOS parport detected.
[   75.769063] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   75.823182] nvidia: module license 'NVIDIA' taints kernel.
[   76.114748] usbcore: registered new interface driver xpad
[   76.114753] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   76.221296] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   76.221486] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9631  Thu Nov  9 17:35:27 PST 2006
[   76.462817] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   76.462827] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[   76.463169] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   77.124236] fuse init (API version 7.8)
[   77.154006] lp0: using parport0 (interrupt-driven).
[   77.214457] Adding 1646620k swap on /dev/disk/by-uuid/790bd820-a10a-4c8f-a6bc-ae87642fd7f9.  Priority:-1 extents:1 across:1646620k
[   77.324207] EXT3 FS on hdc1, internal journal
[   77.841091] NET: Registered protocol family 10
[   77.841178] lo: Disabled Privacy Extensions
[   83.779921] No dock devices found.
[   83.833376] ibm_acpi: ec object not found
[   83.881879] input: Power Button (FF) as /class/input/input5
[   83.885747] ACPI: Power Button (FF) [PWRF]
[   83.909385] input: Power Button (CM) as /class/input/input6
[   83.913196] ACPI: Power Button (CM) [PWRB]
[   83.965298] Using specific hotkey driver
[   84.114103] pcc_acpi: loading...
[   84.286748] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
[   84.286794] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
[   84.286797] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2
[   84.286799] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6
[   84.286801] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   84.286803] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   87.311880] ppdev: user-space parallel port driver
[   88.363922] Bluetooth: Core ver 2.11
[   88.363976] NET: Registered protocol family 31
[   88.363978] Bluetooth: HCI device and connection manager initialized
[   88.363982] Bluetooth: HCI socket layer initialized
[   88.449227] Bluetooth: L2CAP ver 2.8
[   88.449232] Bluetooth: L2CAP socket layer initialized
[   88.553931] Bluetooth: RFCOMM socket layer initialized
[   88.553948] Bluetooth: RFCOMM TTY layer initialized
[   88.553950] Bluetooth: RFCOMM ver 1.8
[   89.325648] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   89.325905] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   89.326086] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   97.389884] eth0: no IPv6 routers present

---

### Post by imablackhat on 2007-07-27
Anyone have any thoughts?

---

