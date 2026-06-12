---
title: "CDROM Failed"
date: 2009-03-12
forum: x86 64-bit Users
---

### Post by frunze47 on 2009-03-12
HowTo restore my cdrom drive?

ffelix@ffelix64:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 01:04:16 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] Command line: root=UUID=569b2938-f97e-4cd5-b000-8a25b436e536 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff30000 (usable)
[    0.000000]  BIOS-e820: 000000001ff30000 - 000000001ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff40000 - 000000001fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 130864) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FAAC0 checksum 0
[    0.000000] ACPI: RSDP 000FAAC0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FF30000, 0030 (r1 A M I  OEMRSDT   8000403 MSFT       97)
[    0.000000] ACPI: FACP 1FF30200, 0081 (r1 A M I  OEMFACP   8000403 MSFT       97)
[    0.000000] ACPI: DSDT 1FF303E0, 362A (r1  A0091 A0091006        6 MSFT  100000D)
[    0.000000] ACPI: FACS 1FF40000, 0040
[    0.000000] ACPI: APIC 1FF30390, 004A (r1 A M I  OEMAPIC   8000403 MSFT       97)
[    0.000000] ACPI: OEMB 1FF40040, 003F (r1 A M I  OEMBIOS   8000403 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001ff30000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 130864) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001ff30000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   130864
[    0.000000] On node 0 totalpages: 130767
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1219 pages reserved
[    0.000000]   DMA zone: 2724 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1733 pages used for memmap
[    0.000000]   DMA32 zone: 125035 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 127759
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=569b2938-f97e-4cd5-b000-8a25b436e536 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   26.209358] time.c: Detected 2002.560 MHz processor.
[   26.210799] Console: colour VGA+ 80x25
[   26.210803] console [tty0] enabled
[   26.210819] Checking aperture...
[   26.210822] CPU 0: aperture @ f8000000 size 64 MB
[   26.218104] Memory: 503364k/523456k available (2492k kernel code, 19704k reserved, 1316k data, 320k init)
[   26.218153] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   26.295294] Calibrating delay using timer specific routine.. 4009.76 BogoMIPS (lpj=8019537)
[   26.295336] Security Framework initialized
[   26.295347] SELinux:  Disabled at boot.
[   26.295365] AppArmor: AppArmor initialized
[   26.295369] Failure registering capabilities with primary security module.
[   26.295430] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   26.295977] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   26.296245] Mount-cache hash table entries: 256
[   26.296400] Initializing cgroup subsys ns
[   26.296404] Initializing cgroup subsys cpuacct
[   26.296417] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.296419] CPU: L2 Cache: 1024K (64 bytes/line)
[   26.296421] CPU 0/0 -> Node 0
[   26.296446] SMP alternatives: switching to UP code
[   26.297064] Freeing SMP alternatives: 24k freed
[   26.298019] Early unpacking initramfs... done
[   26.611945] ACPI: Core revision 20070126
[   26.611993] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.654447] Using local APIC timer interrupts.
[   26.704353] APIC timer calibration result 12515996
[   26.704355] Detected 12.515 MHz APIC timer.
[   26.704409] Brought up 1 CPUs
[   26.704638] CPU0 attaching sched-domain:
[   26.704641]  domain 0: span 01
[   26.704642]   groups: 01
[   26.704796] net_namespace: 120 bytes
[   26.705197] Time: 15:38:01  Date: 03/11/09
[   26.705223] NET: Registered protocol family 16
[   26.705392] ACPI: bus type pci registered
[   26.705459] PCI: Using configuration type 1
[   26.707170] ACPI: EC: Look up EC in DSDT
[   26.709829] ACPI: Interpreter enabled
[   26.709831] ACPI: (supports S0 S1 S3 S4 S5)
[   26.709844] ACPI: Using IOAPIC for interrupt routing
[   26.715010] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.715527] PCI: enabled onboard AC97/MC97 devices
[   26.715735] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.721092] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   26.721176] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   26.721258] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   26.721339] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   26.721421] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   26.721502] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   26.721584] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   26.721666] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   26.721751] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.721780] pnp: PnP ACPI init
[   26.721787] ACPI: bus type pnp registered
[   26.724445] pnp: PnP ACPI: found 13 devices
[   26.724447] ACPI: ACPI bus type pnp unregistered
[   26.724644] PCI: Using ACPI for IRQ routing
[   26.724646] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.724654] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   26.740363] NET: Registered protocol family 8
[   26.740365] NET: Registered protocol family 20
[   26.740420] agpgart: Detected AGP bridge 0
[   26.744025] agpgart: AGP aperture is 64M @ 0xf8000000
[   26.744096] AppArmor: AppArmor Filesystem Enabled
[   26.744348] Time: tsc clocksource has been installed.
[   26.752387] system 00:09: ioport range 0x295-0x296 has been reserved
[   26.752390] system 00:09: ioport range 0x3e1-0x3e7 has been reserved
[   26.752392] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   26.752394] system 00:09: ioport range 0x800-0x87f has been reserved
[   26.752397] system 00:09: ioport range 0x400-0x41f has been reserved
[   26.752404] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   26.752407] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   26.752410] system 00:0a: iomem range 0xfff80000-0xffffffff could not be reserved
[   26.752417] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   26.752419] system 00:0c: iomem range 0xc0000-0xdffff has been reserved
[   26.752421] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   26.752424] system 00:0c: iomem range 0x100000-0x1ffeffff could not be reserved
[   26.752426] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   26.752775] PCI: Bridge: 0000:00:01.0
[   26.752776]   IO window: disabled.
[   26.752779]   MEM window: f5500000-f76fffff
[   26.752782]   PREFETCH window: d5400000-f53fffff
[   26.752801] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.752849] NET: Registered protocol family 2
[   26.788377] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   26.788572] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[   26.788695] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[   26.788817] TCP: Hash tables configured (established 16384 bind 16384)
[   26.788819] TCP reno registered
[   26.800420] checking if image is initramfs... it is
[   27.256000] Switched to high resolution mode on CPU 0
[   27.409068] Freeing initrd memory: 7553k freed
[   27.416737] audit: initializing netlink socket (disabled)
[   27.416751] audit(1236785882.164:1): initialized
[   27.418522] VFS: Disk quotas dquot_6.5.1
[   27.418589] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   27.418708] io scheduler noop registered
[   27.418710] io scheduler anticipatory registered
[   27.418712] io scheduler deadline registered
[   27.418803] io scheduler cfq registered (default)
[   27.418810] PCI: VIA PCI bridge detected. Disabling DAC.
[   27.419651] Boot video device is 0000:01:00.0
[   27.443586] Real Time Clock Driver v1.12ac
[   27.443664] Linux agpgart interface v0.102
[   27.443666] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.443778] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.444631] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.445219] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.445276] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.445352] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   27.445719] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.445723] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.455905] mice: PS/2 mouse device common for all mice
[   27.455935] cpuidle: using governor ladder
[   27.455937] cpuidle: using governor menu
[   27.456071] NET: Registered protocol family 1
[   27.456163] registered taskstats version 1
[   27.456273]   Magic number: 1:977:638
[   27.456389] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   27.456392] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.456393] EDD information not available.
[   27.456402] Freeing unused kernel memory: 320k freed
[   27.457368] Write protecting the kernel read-only data: 1036k
[   27.487811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   28.652273] fuse init (API version 7.9)
[   29.038904] SCSI subsystem initialized
[   29.063056] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.063070] PCI: Disallowing DAC for device 0000:00:0a.0
[   29.063386] skge 1.13 addr 0xf7d00000 irq 17 chip Yukon-Lite rev 7
[   29.064818] skge eth0: addr 00:11:2f:89:12:8c
[   29.078734] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.131920] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f7b00000-f7b007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   29.152099] libata version 3.00 loaded.
[   29.169703] usbcore: registered new interface driver usbfs
[   29.169725] usbcore: registered new interface driver hub
[   29.185339] usbcore: registered new device driver usb
[   29.198603] USB Universal Host Controller Interface driver v3.0
[   29.231509] sata_via 0000:00:0f.0: version 2.3
[   29.231535] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   29.231579] sata_via 0000:00:0f.0: routed to hard irq line 10
[   29.231842] scsi0 : sata_via
[   29.232320] scsi1 : sata_via
[   29.232343] ata1: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd400 irq 20
[   29.232345] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xd800 bmdma 0xd408 irq 20
[   29.281347] Floppy drive(s): fd0 is 1.44M
[   29.298364] FDC 0 is a post-1991 82077
[   29.434440] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   29.646260] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   29.660125] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   29.660137] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   29.660432] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   29.660464] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b400
[   29.660586] usb usb1: configuration #1 chosen from 1 choice
[   29.660609] hub 1-0:1.0: USB hub found
[   29.660615] hub 1-0:1.0: 2 ports detected
[   29.762251] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   29.762264] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   29.762291] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   29.762314] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b800
[   29.762410] usb usb2: configuration #1 chosen from 1 choice
[   29.762433] hub 2-0:1.0: USB hub found
[   29.762438] hub 2-0:1.0: 2 ports detected
[   29.866121] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   29.866130] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   29.866146] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.866164] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c000
[   29.866244] usb usb3: configuration #1 chosen from 1 choice
[   29.866261] hub 3-0:1.0: USB hub found
[   29.866265] hub 3-0:1.0: 2 ports detected
[   29.970050] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   29.970058] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   29.970076] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   29.970093] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000c400
[   29.970175] usb usb4: configuration #1 chosen from 1 choice
[   29.970191] hub 4-0:1.0: USB hub found
[   29.970195] hub 4-0:1.0: 2 ports detected
[   30.074246] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   30.074611] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   30.074684] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   30.074722] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf7f00000
[   30.085939] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.086062] usb usb5: configuration #1 chosen from 1 choice
[   30.086084] hub 5-0:1.0: USB hub found
[   30.086091] hub 5-0:1.0: 8 ports detected
[   30.190117] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   30.190180] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   30.193096] pata_via 0000:00:0f.1: version 0.3.3
[   30.193115] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   30.193534] scsi2 : pata_via
[   30.194008] scsi3 : pata_via
[   30.195489] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   30.195492] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   30.405336] ata3.00: ATA-7: ST3250620A, 3.AAE, max UDMA/100
[   30.405340] ata3.00: 488397168 sectors, multi 16: LBA48 
[   30.471706] ata3.00: configured for UDMA/100
[   30.501685] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[1394040710000b3e]
[   30.805715] ata4.00: ATAPI: DVD-RW IDE1108, VER B018, max UDMA/66
[   30.805727] ata4.00: limited to UDMA/33 due to 40-wire cable
[   31.009436] ata4.00: configured for UDMA/33
[   31.009543] scsi 2:0:0:0: Direct-Access     ATA      ST3250620A       3.AA PQ: 0 ANSI: 5
[   31.021534] scsi 3:0:0:0: CD-ROM            DVDRW    IDE1108          B018 PQ: 0 ANSI: 5
[   31.029558] Driver 'sd' needs updating - please use bus_type methods
[   31.029648] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   31.029660] sd 2:0:0:0: [sda] Write Protect is off
[   31.029663] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.029678] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.029722] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   31.029730] sd 2:0:0:0: [sda] Write Protect is off
[   31.029732] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.029745] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.029748]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   31.050507]  sda1 sda2 sda3
[   31.068384] sd 2:0:0:0: [sda] Attached SCSI disk
[   31.073089] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   31.073109] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   31.282252] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   31.282258] Uniform CD-ROM driver Revision: 3.20
[   31.282310] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   72.464727] Attempting manual resume
[   72.464731] swsusp: Resume From Partition 8:2
[   72.464733] PM: Checking swsusp image.
[   72.464927] PM: Resume from disk failed.
[   72.508254] kjournald starting.  Commit interval 5 seconds
[   72.508266] EXT3-fs: mounted filesystem with ordered data mode.
[   78.902180] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   78.926203] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   79.118076] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   79.150104] input: Power Button (FF) as /devices/virtual/input/input3
[   79.161939] ACPI: Power Button (FF) [PWRF]
[   79.162021] input: Power Button (CM) as /devices/virtual/input/input4
[   79.173930] ACPI: Power Button (CM) [PWRB]
[   79.174005] input: Sleep Button (CM) as /devices/virtual/input/input5
[   79.189920] ACPI: Sleep Button (CM) [SLPB]
[   80.149243] nvidia: module license 'NVIDIA' taints kernel.
[   80.552290] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   80.673130] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   80.673143] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   80.721130] parport_pc 00:08: reported by Plug and Play ACPI
[   80.721172] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   81.428296] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   81.932130] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   81.932146] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   81.932280] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   81.932415] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   82.446112] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   82.452483] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   82.458910] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   82.465262] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   82.480299] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   82.480499] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[  160.792858] lp0: using parport0 (interrupt-driven).
[  160.881266] Adding 2000084k swap on /dev/sda2.  Priority:-1 extents:1 across:2000084k
[  161.432175] EXT3 FS on sda1, internal journal
[  162.934139] ip_tables: (C) 2000-2006 Netfilter Core Team
[  163.324413] No dock devices found.
[  163.544510] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[  163.545580] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[  164.404235] ppdev: user-space parallel port driver
[  164.618303] audit(1236786019.911:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4846 profile="/usr/sbin/cupsd" namespace="default"
[  185.962880] skge eth0: enabling interface
[  186.070936] Bluetooth: Core ver 2.11
[  186.071566] NET: Registered protocol family 31
[  186.071569] Bluetooth: HCI device and connection manager initialized
[  186.071573] Bluetooth: HCI socket layer initialized
[  186.102776] Bluetooth: L2CAP ver 2.9
[  186.102781] Bluetooth: L2CAP socket layer initialized
[  186.156292] Bluetooth: RFCOMM socket layer initialized
[  186.156314] Bluetooth: RFCOMM TTY layer initialized
[  186.156316] Bluetooth: RFCOMM ver 1.8
[  187.211515] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  187.211529] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  187.211580] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  187.648628] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[  189.755516] NET: Registered protocol family 17
[  193.523281] NET: Registered protocol family 10
[  193.523691] lo: Disabled Privacy Extensions
[  203.880367] eth0: no IPv6 routers present
ffelix@ffelix64:~$ 
Thank you!
Felix

---

### Post by cariboo on 2009-03-12
What seems to be the problem? From the dmesg output, it looks like it is working.

Jim

---

### Post by frunze47 on 2009-03-12
Drive unable to mount disks, even though the cdrom/dvd drive works hard long time...
Thank you!
Felix

---

### Post by Yellow Pasque on 2009-03-12
Can the drive read any discs (like in another OS or using a BootCD)?

Also, for future reference, please use [ CODE ][ /CODE ] tags when pasting long blocks of output

---

### Post by frunze47 on 2009-03-12
I've just tried another disk and it's mounted now!
Hopefully that's been a mechanical issue...
But why dmesg asks for:
 Driver 'sd' needs updating - please use bus_type methods
and 
 sda:<4>Driver 'sr' needs updating - please use bus_type methods
....
How to update them?
Thank you very much!
Felix

---

### Post by Yellow Pasque on 2009-03-12
> Driver 'sd' needs updating - please use bus_type methods
and
sda:<4>Driver 'sr' needs updating - please use bus_type methods
That's not something you can fix (without updating kernel source code).

---

### Post by frunze47 on 2009-03-13
I thank everyone for the attention and input!
Felix

---

