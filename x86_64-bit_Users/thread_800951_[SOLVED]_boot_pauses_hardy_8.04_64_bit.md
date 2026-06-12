---
title: "[SOLVED] boot pauses hardy 8.04 64 bit"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by istblacken on 2008-05-20
hi i am using hardy 8.04 and for a few days i have been experiencing boot pauses. boot process pauses when it says Starting MTA then after a few minutes it continues normally. during the pause it does nothing, no hdd activity. my dmesg output. Any idea how to fix this???


```
[   12.908107] net_namespace: 120 bytes
[   12.908493] Time: 15:53:49  Date: 05/20/08
[   12.908516] NET: Registered protocol family 16
[   12.908702] ACPI: bus type pci registered
[   12.908776] PCI: Using configuration type 1
[   12.911982] ACPI: EC: EC description table is found, configuring boot EC
[   13.027037] ACPI: Interpreter enabled
[   13.027040] ACPI: (supports S0 S1 S3 S4 S5)
[   13.027060] ACPI: Using IOAPIC for interrupt routing
[   13.028761] Error attaching device data
[   13.028802] Error attaching device data
[   13.037786] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   13.037789] ACPI: EC: driver started in poll mode
[   13.038207] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.038985] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   13.038989] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   13.040171] PCI: Transparent bridge - 0000:00:1e.0
[   13.040220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.040458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   13.040586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   13.040711] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   13.040835] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   13.040967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   13.041099] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   13.041251] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   13.041383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   13.064814] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[   13.064996] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[   13.065175] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[   13.065354] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 12)
[   13.065533] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)
[   13.065710] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 12)
[   13.065888] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 12)
[   13.066067] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[   13.066248] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] -  F2, should be 59 [20070126]
[   13.066255] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.066286] pnp: PnP ACPI init
[   13.066294] ACPI: bus type pnp registered
[   13.069014] pnp: PnP ACPI: found 13 devices
[   13.069016] ACPI: ACPI bus type pnp unregistered
[   13.069245] PCI: Using ACPI for IRQ routing
[   13.069247] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.083284] NET: Registered protocol family 8
[   13.083286] NET: Registered protocol family 20
[   13.083319] PCI-GART: No AMD northbridge found.
[   13.083323] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.083327] hpet0: 3 64-bit timers, 14318180 Hz
[   13.084362] AppArmor: AppArmor Filesystem Enabled
[   13.087258] Time: tsc clocksource has been installed.
[   13.087265] Switched to high resolution mode on CPU 0
[   13.087691] Switched to high resolution mode on CPU 1
[   13.095246] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   13.095255] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   13.095257] system 00:08: ioport range 0x800-0x87f has been reserved
[   13.095259] system 00:08: ioport range 0x400-0x41f has been reserved
[   13.095262] system 00:08: ioport range 0x500-0x53f has been reserved
[   13.095264] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   13.095267] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   13.095269] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[   13.095272] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   13.095274] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   13.095280] system 00:0a: ioport range 0x250-0x253 has been reserved
[   13.095282] system 00:0a: ioport range 0x256-0x25f has been reserved
[   13.095285] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   13.095287] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.095292] system 00:0b: iomem range 0xc0000000-0xcfffffff has been reserved
[   13.095297] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   13.095299] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[   13.095302] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   13.095304] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[   13.095307] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   13.095695] PCI: Bridge: 0000:00:01.0
[   13.095698]   IO window: b000-bfff
[   13.095701]   MEM window: f7f00000-fdffffff
[   13.095704]   PREFETCH window: d5e00000-f5dfffff
[   13.095707] PCI: Bridge: 0000:00:1c.0
[   13.095708]   IO window: disabled.
[   13.095712]   MEM window: fe000000-fe0fffff
[   13.095716]   PREFETCH window: disabled.
[   13.095720] PCI: Bridge: 0000:00:1c.1
[   13.095721]   IO window: disabled.
[   13.095725]   MEM window: fe100000-fe1fffff
[   13.095728]   PREFETCH window: disabled.
[   13.095732] PCI: Bridge: 0000:00:1c.2
[   13.095733]   IO window: disabled.
[   13.095737]   MEM window: disabled.
[   13.095740]   PREFETCH window: disabled.
[   13.095744] PCI: Bridge: 0000:00:1c.3
[   13.095746]   IO window: disabled.
[   13.095750]   MEM window: disabled.
[   13.095753]   PREFETCH window: disabled.
[   13.095757] PCI: Bridge: 0000:00:1c.4
[   13.095759]   IO window: c000-cfff
[   13.095763]   MEM window: fe200000-fe9fffff
[   13.095767]   PREFETCH window: f5e00000-f7dfffff
[   13.095771] PCI: Bridge: 0000:00:1c.5
[   13.095772]   IO window: disabled.
[   13.095776]   MEM window: disabled.
[   13.095779]   PREFETCH window: disabled.
[   13.095784] PCI: Bridge: 0000:00:1e.0
[   13.095785]   IO window: disabled.
[   13.095789]   MEM window: fea00000-feafffff
[   13.095792]   PREFETCH window: disabled.
[   13.095808] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.095813] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.095829] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.095833] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.095850] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   13.095855] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.095872] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.095877] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.095893] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   13.095898] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.095914] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   13.095919] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   13.095935] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   13.095940] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   13.095950] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.095958] NET: Registered protocol family 2
[   13.131271] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   13.131709] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   13.132644] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.133375] TCP: Hash tables configured (established 131072 bind 65536)
[   13.133378] TCP reno registered
[   13.143358] checking if image is initramfs... it is
[   13.949779] Freeing initrd memory: 8177k freed
[   13.955424] Simple Boot Flag at 0x52 set to 0x1
[   13.956232] audit: initializing netlink socket (disabled)
[   13.956253] audit(1211298829.596:1): initialized
[   13.958237] VFS: Disk quotas dquot_6.5.1
[   13.958301] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.958415] io scheduler noop registered
[   13.958417] io scheduler anticipatory registered
[   13.958418] io scheduler deadline registered
[   13.958522] io scheduler cfq registered (default)
[   14.186862] Boot video device is 0000:01:00.0
[   14.187023] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.187058] assign_interrupt_mode Found MSI capability
[   14.187086] Allocate Port Service[0000:00:01.0:pcie00]
[   14.187119] Allocate Port Service[0000:00:01.0:pcie02]
[   14.187189] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.187227] assign_interrupt_mode Found MSI capability
[   14.187258] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.187339] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.187376] assign_interrupt_mode Found MSI capability
[   14.187408] Allocate Port Service[0000:00:1c.1:pcie00]
[   14.187483] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.187521] assign_interrupt_mode Found MSI capability
[   14.187553] Allocate Port Service[0000:00:1c.2:pcie00]
[   14.187630] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   14.187668] assign_interrupt_mode Found MSI capability
[   14.187699] Allocate Port Service[0000:00:1c.3:pcie00]
[   14.187775] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   14.187814] assign_interrupt_mode Found MSI capability
[   14.187845] Allocate Port Service[0000:00:1c.4:pcie00]
[   14.187875] Allocate Port Service[0000:00:1c.4:pcie02]
[   14.187950] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   14.187988] assign_interrupt_mode Found MSI capability
[   14.188020] Allocate Port Service[0000:00:1c.5:pcie00]
[   14.188049] Allocate Port Service[0000:00:1c.5:pcie02]
[   14.210919] Real Time Clock Driver v1.12ac
[   14.211118] hpet_resources: 0xfed00000 is busy
[   14.211164] Linux agpgart interface v0.102
[   14.211166] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.212220] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.212282] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.212370] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   14.214659] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.215450] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.215454] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.215456] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.215458] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.215461] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.231609] mice: PS/2 mouse device common for all mice
[   14.231644] cpuidle: using governor ladder
[   14.231645] cpuidle: using governor menu
[   14.231772] NET: Registered protocol family 1
[   14.231825] registered taskstats version 1
[   14.231945]   Magic number: 8:426:892
[   14.231998]   hash matches device ptyy2
[   14.232053] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   14.232056] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.232058] EDD information not available.
[   14.232066] Freeing unused kernel memory: 316k freed
[   14.267543] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   15.434685] fuse init (API version 7.9)
[   15.476588] ACPI: SSDT 3FFB63A0, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[   15.476890] ACPI: SSDT 3FFB6680, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[   15.477758] Monitor-Mwait will be used to enter C-1 state
[   15.477761] Monitor-Mwait will be used to enter C-2 state
[   15.477763] Monitor-Mwait will be used to enter C-3 state
[   15.477879] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.477884] ACPI: Processor [P001] (supports 8 throttling states)
[   15.478129] ACPI: SSDT 3FFB62D0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[   15.478410] ACPI: SSDT 3FFB65F0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[   15.479448] Marking TSC unstable due to TSC halts in idle
[   15.479552] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   15.479558] ACPI: Processor [P002] (supports 8 throttling states)
[   15.480557] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.482433] ACPI: Thermal Zone [THRM] (35 C)
[   15.482786] Time: hpet clocksource has been installed.
[   15.741731] usbcore: registered new interface driver usbfs
[   15.741754] usbcore: registered new interface driver hub
[   15.742536] usbcore: registered new device driver usb
[   15.751719] USB Universal Host Controller Interface driver v3.0
[   15.751786] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.751800] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   15.751803] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   15.752069] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   15.752098] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e080
[   15.752228] usb usb1: configuration #1 chosen from 1 choice
[   15.752252] hub 1-0:1.0: USB hub found
[   15.752257] hub 1-0:1.0: 2 ports detected
[   15.857714] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   15.857726] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   15.857730] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   15.857751] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   15.857777] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e000
[   15.857876] usb usb2: configuration #1 chosen from 1 choice
[   15.857898] hub 2-0:1.0: USB hub found
[   15.857905] hub 2-0:1.0: 2 ports detected
[   15.861928] SCSI subsystem initialized
[   15.897419] libata version 3.00 loaded.
[   15.961695] ACPI: PCI Interrupt 0000:09:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.014801] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   16.023424] ahci 0000:00:1f.2: version 3.0
[   16.023463] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 20 (level, low) -> IRQ 20
[   16.097460] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   16.299932] usb 1-2: configuration #1 chosen from 1 choice
[   16.428791] Clocksource tsc unstable (delta = -397321580 ns)
[   16.464673] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   16.464678] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   16.464684] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   16.465474] scsi0 : ahci
[   16.465693] scsi1 : ahci
[   16.465847] scsi2 : ahci
[   16.465965] ata1: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff900 irq 504
[   16.465968] ata2: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff980 irq 504
[   16.465971] ata3: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebffa00 irq 504
[   16.521199] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800039c5887]
[   16.565249] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.565617] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
[   16.565620] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   16.566105] ata1.00: configured for UDMA/100
[   16.629263] ata2: SATA link down (SStatus 0 SControl 300)
[   16.696829] ata3: SATA link down (SStatus 0 SControl 300)
[   16.696960] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[   16.697081] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   16.697596] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   16.697602] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   16.697649] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[   16.701559] ehci_hcd 0000:00:1a.7: debug port 1
[   16.701566] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   16.701576] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfebff400
[   16.705486] Driver 'sd' needs updating - please use bus_type methods
[   16.707184] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.707199] sd 0:0:0:0: [sda] Write Protect is off
[   16.707203] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.707225] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.707275] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.707283] sd 0:0:0:0: [sda] Write Protect is off
[   16.707285] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.707300] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.707303]  sda:<6>ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.707986] usb usb3: configuration #1 chosen from 1 choice
[   16.708018] hub 3-0:1.0: USB hub found
[   16.708024] hub 3-0:1.0: 4 ports detected
[   16.724172] usb 1-2: USB disconnect, address 2
[   16.735900] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   16.736521] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   16.736527] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   16.736575] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   16.740498] ehci_hcd 0000:00:1d.7: debug port 1
[   16.740504] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   16.740513] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebff000
[   16.745271] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.745400] usb usb4: configuration #1 chosen from 1 choice
[   16.745431] hub 4-0:1.0: USB hub found
[   16.745436] hub 4-0:1.0: 6 ports detected
[   16.773061] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   16.773072] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.773076] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.773099] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   16.773123] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[   16.773233] usb usb5: configuration #1 chosen from 1 choice
[   16.773255] hub 5-0:1.0: USB hub found
[   16.773260] hub 5-0:1.0: 2 ports detected
[   16.819282] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   16.819293] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   16.819297] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   16.819319] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   16.819345] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[   16.819442] usb usb6: configuration #1 chosen from 1 choice
[   16.819464] hub 6-0:1.0: USB hub found
[   16.819468] hub 6-0:1.0: 2 ports detected
[   16.834422]  sda1 sda2 sda3 < sda5<6>usb 3-2: new high speed USB device using ehci_hcd and address 2
[   16.846176] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.846186] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   16.846190] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   16.846220] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   16.846242] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[   16.846336] usb usb7: configuration #1 chosen from 1 choice
[   16.846358] hub 7-0:1.0: USB hub found
[   16.846363] hub 7-0:1.0: 2 ports detected
[   16.854059]  sda6 > sda4
[   16.877524] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.881506] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.950275] ata_piix 0000:00:1f.1: version 2.12
[   16.950296] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   16.950331] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.950568] scsi3 : ata_piix
[   16.950613] scsi4 : ata_piix
[   16.951269] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   16.951271] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   16.987672] usb 3-2: configuration #1 chosen from 1 choice
[   17.174702] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WR02, max UDMA/33
[   17.215619] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   17.240971] Attempting manual resume
[   17.240974] swsusp: Resume From Partition 8:4
[   17.240975] PM: Checking swsusp image.
[   17.241105] PM: Resume from disk failed.
[   17.246998] JFS: nTxBlock = 8037, nTxLock = 64298
[   17.247575] ata4.00: configured for UDMA/33
[   17.247622] ata5: port disabled. ignoring.
[   17.251386] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WR02 PQ: 0 ANSI: 5
[   17.251502] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   17.258988] Driver 'sr' needs updating - please use bus_type methods
[   17.273443] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   17.273447] Uniform CD-ROM driver Revision: 3.20
[   17.273492] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   17.342142] usb 5-2: configuration #1 chosen from 1 choice
[   19.598332] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.619677] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.825060] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   19.982364] input: Power Button (FF) as /devices/virtual/input/input3
[   20.002000] ACPI: Power Button (FF) [PWRF]
[   20.002126] input: Sleep Button (CM) as /devices/virtual/input/input4
[   20.033982] ACPI: Sleep Button (CM) [SLPB]
[   20.034077] input: Lid Switch as /devices/virtual/input/input5
[   20.035016] ACPI: Lid Switch [LID]
[   20.078763] asus-laptop: Asus Laptop Support version 0.42
[   20.079058] asus-laptop:   F3Sc model detected
[   20.081398] Registered led device: asus:mail
[   20.222918] iTCO_vendor_support: vendor-support=0
[   20.248659] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.248783] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
[   20.248831] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.379122] ACPI: AC Adapter [AC0] (on-line)
[   20.500124] ACPI: Battery Slot [BAT0] (battery present)
[   20.592514] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input6
[   20.612577] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.803628] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.803641] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   20.804125] atl1 0000:02:00.0: version 2.0.7
[   20.824554] ricoh-mmc: Ricoh MMC Controller disabling driver
[   20.824558] ricoh-mmc: Copyright(c) Philip Langdale
[   20.853112] nvidia: module license 'NVIDIA' taints kernel.
[   20.921444] ricoh-mmc: Ricoh MMC controller found at 0000:09:01.2 [1180:0843] (rev 12)
[   20.921457] ricoh-mmc: Controller is now disabled.
[   21.110838] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.110848] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   21.110974] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   21.708584] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   21.709126] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.832315] sdhci: Secure Digital Host Controller Interface driver
[   21.832318] sdhci: Copyright(c) Pierre Ossman
[   21.846999] sdhci: SDHCI controller found at 0000:09:01.1 [1180:0822] (rev 22)
[   21.847020] ACPI: PCI Interrupt 0000:09:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[   21.848503] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   21.850575] mmc0: SDHCI at 0xfeaff400 irq 17 DMA
[   21.945511] Linux video capture interface: v2.00
[   21.972087] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   21.972091] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   21.972182] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   21.972191] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   21.972694] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   21.980318] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   21.990017] usbcore: registered new interface driver hiddev
[   22.002698] input: Logitech Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input7
[   22.020700] uvcvideo: Found UVC 1.00 device USB2.0 1.3M UVC WebCam  (04f2:b012)
[   22.021173] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   22.104770] input,hidraw0: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:1d.0-2
[   22.104790] usbcore: registered new interface driver usbhid
[   22.104793] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   22.104808] usbcore: registered new interface driver uvcvideo
[   22.104812] USB Video Class driver (v0.1.0)
[   23.029255] iwl4965: Radio disabled by HW RF Kill switch
[   24.124610] lp: driver loaded but no devices found
[   24.232160] Adding 1341416k swap on /dev/sda4.  Priority:-1 extents:1 across:1341416k
[   24.514344] NET: Registered protocol family 10
[   24.514571] lo: Disabled Privacy Extensions
[   24.514876] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.529168] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.156125] No dock devices found.
[   28.972245] ppdev: user-space parallel port driver
[   29.315038] audit(1211288055.327:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5256 profile="/usr/sbin/cupsd" namespace="default"
[   92.390302] Bluetooth: Core ver 2.11
[   92.390462] NET: Registered protocol family 31
[   92.390466] Bluetooth: HCI device and connection manager initialized
[   92.390473] Bluetooth: HCI socket layer initialized
[   92.455395] Bluetooth: L2CAP ver 2.9
[   92.455404] Bluetooth: L2CAP socket layer initialized
[   92.528452] Bluetooth: RFCOMM socket layer initialized
[   92.528464] Bluetooth: RFCOMM TTY layer initialized
[   92.528465] Bluetooth: RFCOMM ver 1.8
[  103.314386] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[  103.317516] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  107.326014] CPU0 attaching NULL sched-domain.
[  107.326027] CPU1 attaching NULL sched-domain.
[  107.331553] CPU0 attaching sched-domain:
[  107.331566]  domain 0: span 03
[  107.331569]   groups: 01 02
[  107.331576]   domain 1: span 03
[  107.331579]    groups: 03
[  107.331584] CPU1 attaching sched-domain:
[  107.331587]  domain 0: span 03
[  107.331591]   groups: 02 01
[  107.331597]   domain 1: span 03
[  107.331600]    groups: 03
[  109.887781] eth0: no IPv6 routers present
[  140.188314] iwl4965: Radio disabled by HW RF Kill switch

```

---

### Post by istblacken on 2008-05-21
i still have this problem any idea?:confused:

---

### Post by fogcat on 2008-05-21
I had boot pauses when I first tried Hardy 64 as a RC.  It turned out that I had a bad CD!
Have you tried a reinstallation/ (or am I way off base)?

Have you tried safe mode from the gdm session manager?

These are just a couple of troubleshooting steps that I don't know if ypu have done.  If you have; sorry bout that.

fogcat

---

### Post by istblacken on 2008-05-22
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637/comments/23](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637/comments/23)

this solved my problem. thanks anyway.

---

