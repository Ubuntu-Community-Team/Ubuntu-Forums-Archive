---
title: "Lost wired network after kernal upgrade"
date: 2008-10-27
forum: x86 64-bit Users
---

### Post by no_bikes on 2008-10-27
I have a HP quad core machine. I had the network card working in the original 8.04 kernel, but when i upgraded to the new kernel ubuntu could no longer access my network card.

 Also, windows xp (within Virtual machine) will no longer boot.

---

### Post by felker2 on 2008-10-28
Which ethernet card do you have? (Hopefully not the Intel e1000e)
Which kernel are you using (uname -a)?
How did you upgrade to that kernel?
What does lspci show?
What does dmesg show?

---

### Post by no_bikes on 2008-10-28
the kernel upgrade was from -19 to -21 in ubuntu 8.04 64 bit, i updated using the ubuntu update manager that appears in the top right hand corner of the desktop. I believe the eithernet card is a realtek  rtl 8111/8168b 

thank you 






[COLOR="Red"][SIZE="6"] lspci shows the following[/SIZE][/COLOR]

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Multimedia video controller: Conexant Unknown device 8880 (rev 0f)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e0 (rev a1)


[COLOR="Red"]
[SIZE="6"]dmesg said the following [/SIZE]
[/COLOR]


[   44.134748] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   44.134826] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   44.134904] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[   44.134993] Linux Plug and Play Support v0.97 (c) Adam Belay
[   44.135013] pnp: PnP ACPI init
[   44.135017] ACPI: bus type pnp registered
[   44.136652] pnp: PnP ACPI: found 16 devices
[   44.136653] ACPI: ACPI bus type pnp unregistered
[   44.136812] PCI: Using ACPI for IRQ routing
[   44.136814] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   44.147910] NET: Registered protocol family 8
[   44.147912] NET: Registered protocol family 20
[   44.147948] PCI-GART: No AMD northbridge found.
[   44.147954] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   44.147958] hpet0: 4 64-bit timers, 14318180 Hz
[   44.148986] AppArmor: AppArmor Filesystem Enabled
[   44.151859] Time: tsc clocksource has been installed.
[   44.151866] Switched to high resolution mode on CPU 0
[   44.152305] Switched to high resolution mode on CPU 1
[   44.152452] Switched to high resolution mode on CPU 3
[   44.152454] Switched to high resolution mode on CPU 2
[   44.159874] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   44.159882] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   44.159885] system 00:06: ioport range 0x800-0x87f has been reserved
[   44.159887] system 00:06: ioport range 0x480-0x4bf has been reserved
[   44.159890] system 00:06: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   44.159893] system 00:06: iomem range 0xfed20000-0xfed8ffff has been reserved
[   44.159899] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[   44.159902] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   44.159908] system 00:0b: ioport range 0xa00-0xadf has been reserved
[   44.159914] system 00:0d: iomem range 0xffc00000-0xffefffff has been reserved
[   44.159919] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   44.159925] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   44.159927] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[   44.159930] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   44.159933] system 00:0f: iomem range 0x100000-0xcfffffff could not be reserved
[   44.159936] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   44.160210] PCI: Bridge: 0000:00:01.0
[   44.160212]   IO window: d000-dfff
[   44.160214]   MEM window: fa000000-feafffff
[   44.160216]   PREFETCH window: d0000000-dfffffff
[   44.160218] PCI: Bridge: 0000:00:1c.0
[   44.160219]   IO window: disabled.
[   44.160222]   MEM window: disabled.
[   44.160225]   PREFETCH window: disabled.
[   44.160229] PCI: Bridge: 0000:00:1c.1
[   44.160230]   IO window: disabled.
[   44.160234]   MEM window: f9e00000-f9ffffff
[   44.160237]   PREFETCH window: disabled.
[   44.160241] PCI: Bridge: 0000:00:1c.2
[   44.160243]   IO window: e000-efff
[   44.160247]   MEM window: feb00000-febfffff
[   44.160250]   PREFETCH window: f8f00000-f8ffffff
[   44.160255] PCI: Bridge: 0000:00:1e.0
[   44.160257]   IO window: c000-cfff
[   44.160261]   MEM window: f9d00000-f9dfffff
[   44.160264]   PREFETCH window: disabled.
[   44.160275] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.160279] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   44.160295] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   44.160299] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   44.160315] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   44.160319] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   44.160336] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   44.160340] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   44.160350] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   44.160356] NET: Registered protocol family 2
[   44.195980] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   44.196763] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   44.200079] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   44.200579] TCP: Hash tables configured (established 524288 bind 65536)
[   44.200581] TCP reno registered
[   44.211996] checking if image is initramfs... it is
[   44.722144] Freeing initrd memory: 7550k freed
[   44.726521] audit: initializing netlink socket (disabled)
[   44.726541] audit(1225214943.368:1): initialized
[   44.729142] VFS: Disk quotas dquot_6.5.1
[   44.729207] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   44.729325] io scheduler noop registered
[   44.729327] io scheduler anticipatory registered
[   44.729329] io scheduler deadline registered
[   44.729449] io scheduler cfq registered (default)
[   44.732704] Boot video device is 0000:05:00.0
[   44.732871] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   44.732894] assign_interrupt_mode Found MSI capability
[   44.732913] Allocate Port Service[0000:00:01.0:pcie00]
[   44.733000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   44.733049] assign_interrupt_mode Found MSI capability
[   44.733088] Allocate Port Service[0000:00:1c.0:pcie00]
[   44.733124] Allocate Port Service[0000:00:1c.0:pcie02]
[   44.733219] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   44.733278] assign_interrupt_mode Found MSI capability
[   44.733311] Allocate Port Service[0000:00:1c.1:pcie00]
[   44.733354] Allocate Port Service[0000:00:1c.1:pcie02]
[   44.733446] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   44.733488] assign_interrupt_mode Found MSI capability
[   44.733521] Allocate Port Service[0000:00:1c.2:pcie00]
[   44.733559] Allocate Port Service[0000:00:1c.2:pcie02]
[   44.762451] Real Time Clock Driver v1.12ac
[   44.762627] hpet_resources: 0xfed00000 is busy
[   44.762655] Linux agpgart interface v0.102
[   44.762657] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   44.763932] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   44.764125] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   44.764223] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   44.766304] serio: i8042 KBD port at 0x60,0x64 irq 1
[   44.766308] serio: i8042 AUX port at 0x60,0x64 irq 12
[   44.784887] mice: PS/2 mouse device common for all mice
[   44.784943] cpuidle: using governor ladder
[   44.784945] cpuidle: using governor menu
[   44.785064] NET: Registered protocol family 1
[   44.785185] registered taskstats version 1
[   44.785291]   Magic number: 12:857:492
[   44.785335] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   44.785338] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   44.785339] EDD information not available.
[   44.785349] Freeing unused kernel memory: 320k freed
[   44.786341] Write protecting the kernel read-only data: 1036k
[   44.810565] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   45.922243] fuse init (API version 7.9)
[   45.936018] ACPI: SSDT CFFC0270, 02B9 (r1 HPQOEM SLIC-CPC       11 INTL 20051117)
[   45.936345] ACPI: SSDT CFFC0700, 02B9 (r1 HPQOEM SLIC-CPC       12 INTL 20051117)
[   45.936635] ACPI: SSDT CFFC0B90, 02B9 (r1 HPQOEM SLIC-CPC       12 INTL 20051117)
[   45.936927] ACPI: SSDT CFFC1020, 02B9 (r1 HPQOEM SLIC-CPC       12 INTL 20051117)
[   45.996476] usbcore: registered new interface driver usbfs
[   45.996494] usbcore: registered new interface driver hub
[   45.996512] usbcore: registered new device driver usb
[   45.997062] USB Universal Host Controller Interface driver v3.0
[   45.997106] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.997113] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   45.997116] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   45.997312] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   45.997341] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a400
[   45.997428] usb usb1: configuration #1 chosen from 1 choice
[   45.997443] hub 1-0:1.0: USB hub found
[   45.997446] hub 1-0:1.0: 2 ports detected
[   46.089888] SCSI subsystem initialized
[   46.101281] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   46.101290] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   46.101293] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   46.101317] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   46.101343] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a480
[   46.101418] usb usb2: configuration #1 chosen from 1 choice
[   46.101433] hub 2-0:1.0: USB hub found
[   46.101437] hub 2-0:1.0: 2 ports detected
[   46.106340] libata version 3.00 loaded.
[   46.205279] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   46.205286] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   46.205289] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   46.205303] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   46.205329] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a800
[   46.205397] usb usb3: configuration #1 chosen from 1 choice
[   46.205412] hub 3-0:1.0: USB hub found
[   46.205416] hub 3-0:1.0: 2 ports detected
[   46.309243] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   46.309250] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   46.309253] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   46.309269] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   46.309296] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a880
[   46.309369] usb usb4: configuration #1 chosen from 1 choice
[   46.309383] hub 4-0:1.0: USB hub found
[   46.309387] hub 4-0:1.0: 2 ports detected
[   46.341186] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   46.413262] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   46.413271] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   46.413275] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   46.413296] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   46.413325] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ac00
[   46.413393] usb usb5: configuration #1 chosen from 1 choice
[   46.413406] hub 5-0:1.0: USB hub found
[   46.413410] hub 5-0:1.0: 2 ports detected
[   46.487463] usb 1-2: configuration #1 chosen from 1 choice
[   46.490401] hub 1-2:1.0: USB hub found
[   46.492373] hub 1-2:1.0: 4 ports detected
[   46.517239] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   46.517248] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   46.517251] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   46.517271] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 6
[   46.517298] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b000
[   46.517363] usb usb6: configuration #1 chosen from 1 choice
[   46.517376] hub 6-0:1.0: USB hub found
[   46.517379] hub 6-0:1.0: 2 ports detected
[   46.621258] ahci 0000:00:1f.2: version 3.0
[   46.621300] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   46.839735] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   47.014448] usb 2-1: configuration #1 chosen from 1 choice
[   47.255613] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   47.577383] usb 4-2: configuration #1 chosen from 1 choice
[   47.623626] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[   47.623630] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part 
[   47.623635] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   47.623898] scsi0 : ahci
[   47.623931] scsi1 : ahci
[   47.623958] scsi2 : ahci
[   47.623984] scsi3 : ahci
[   47.624009] scsi4 : ahci
[   47.624033] scsi5 : ahci
[   47.624102] ata1: SATA max UDMA/133 abar m2048@0xf9cff000 port 0xf9cff100 irq 507
[   47.624105] ata2: SATA max UDMA/133 abar m2048@0xf9cff000 port 0xf9cff180 irq 507
[   47.624107] ata3: SATA max UDMA/133 abar m2048@0xf9cff000 port 0xf9cff200 irq 507
[   47.624109] ata4: SATA max UDMA/133 abar m2048@0xf9cff000 port 0xf9cff280 irq 507
[   47.624111] ata5: SATA max UDMA/133 abar m2048@0xf9cff000 port 0xf9cff300 irq 507
[   47.624114] ata6: SATA max UDMA/133 abar m2048@0xf9cff000 port 0xf9cff380 irq 507
[   47.819603] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   47.996406] usb 5-1: configuration #1 chosen from 1 choice
[   48.099550] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   48.118650] ata1.00: ATA-8: Hitachi HDP725050GLA360, GM4OA57A, max UDMA/133
[   48.118653] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   48.119381] ata1.00: configured for UDMA/133
[   48.251617] usb 6-2: new full speed USB device using uhci_hcd and address 2
[   48.416378] usb 6-2: configuration #1 chosen from 1 choice
[   48.419509] usbcore: registered new interface driver libusual
[   48.422258] Initializing USB Mass Storage driver...
[   48.422327] scsi6 : SCSI emulation for USB Mass Storage devices
[   48.422364] usbcore: registered new interface driver usb-storage
[   48.422366] USB Mass Storage support registered.
[   48.422442] usb-storage: device found at 2
[   48.422443] usb-storage: waiting for device to settle before scanning
[   48.591597] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   48.751010] ata2.00: ATAPI: HL-DT-ST DVD-RAM GH10L, FC09, max UDMA/100
[   48.910816] ata2.00: configured for UDMA/100
[   49.383447] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   49.395668] ata3.00: ATA-8: Hitachi HDP725050GLA360, GM4OA57A, max UDMA/133
[   49.395671] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   49.396392] ata3.00: configured for UDMA/133
[   49.707417] ata4: SATA link down (SStatus 0 SControl 300)
[   50.019391] ata5: SATA link down (SStatus 0 SControl 300)
[   50.335409] ata6: SATA link down (SStatus 0 SControl 300)
[   50.335509] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDP72505 GM4O PQ: 0 ANSI: 5
[   50.338469] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH10L    FC09 PQ: 0 ANSI: 5
[   50.338601] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDP72505 GM4O PQ: 0 ANSI: 5
[   50.338752] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[   50.339018] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   50.339713] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   50.339718] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   50.339762] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   50.343668] ehci_hcd 0000:00:1a.7: debug port 1
[   50.343673] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   50.343678] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9cfec00
[   50.359371] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.359447] usb usb7: configuration #1 chosen from 1 choice
[   50.359462] hub 7-0:1.0: USB hub found
[   50.359467] hub 7-0:1.0: 4 ports detected
[   50.390857] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[f9dff000-f9dff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   50.399195] Driver 'sd' needs updating - please use bus_type methods
[   50.399262] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   50.399270] sd 0:0:0:0: [sda] Write Protect is off
[   50.399272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.399283] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.399314] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   50.399320] sd 0:0:0:0: [sda] Write Protect is off
[   50.399321] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.399331] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.399333]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   50.426208]  sda1 sda2 sda3 sda4
[   50.451411] usb 1-2: USB disconnect, address 2
[   50.452794] sd 0:0:0:0: [sda] Attached SCSI disk
[   50.452840] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   50.452847] sd 2:0:0:0: [sdb] Write Protect is off
[   50.452849] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   50.452863] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.452898] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   50.452904] sd 2:0:0:0: [sdb] Write Protect is off
[   50.452906] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   50.452916] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.452918]  sdb:<6>ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   50.464302] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   50.464308] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   50.464350] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   50.468269] ehci_hcd 0000:00:1d.7: debug port 1
[   50.468273] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   50.468278] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9cff800
[   50.478426]  sdb1
[   50.478485] sd 2:0:0:0: [sdb] Attached SCSI disk
[   50.481495] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   50.481509] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   50.481521] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   50.487343] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.487424] usb usb8: configuration #1 chosen from 1 choice
[   50.487441] hub 8-0:1.0: USB hub found
[   50.487447] hub 8-0:1.0: 8 ports detected
[   50.579359] usb 2-1: USB disconnect, address 2
[   50.896627] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   50.896632] Uniform CD-ROM driver Revision: 3.20
[   50.896682] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   50.947362] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   51.079778] usb 7-2: configuration #1 chosen from 1 choice
[   51.079873] hub 7-2:1.0: USB hub found
[   51.079970] hub 7-2:1.0: 4 ports detected
[   51.663255] usb 8-4: new high speed USB device using ehci_hcd and address 2
[   51.667858] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001297065]
[   51.956761] usb 8-4: configuration #1 chosen from 1 choice
[   52.195239] usb 8-5: new high speed USB device using ehci_hcd and address 3
[   52.345003] usb 8-5: configuration #1 chosen from 1 choice
[   52.345631] scsi7 : SCSI emulation for USB Mass Storage devices
[   52.345678] usb-storage: device found at 3
[   52.345680] usb-storage: waiting for device to settle before scanning
[   52.583182] usb 8-8: new high speed USB device using ehci_hcd and address 4
[   52.716617] usb 8-8: configuration #1 chosen from 1 choice
[   52.716951] usb 4-2: USB disconnect, address 2
[   52.843199] usb 5-1: USB disconnect, address 2
[   52.971177] usb 6-2: USB disconnect, address 2
[   53.339119] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   53.522298] usb 2-1: configuration #1 chosen from 1 choice
[   55.281378] Attempting manual resume
[   55.281381] swsusp: Resume From Partition 8:4
[   55.281381] PM: Checking swsusp image.
[   55.281485] PM: Resume from disk failed.
[   55.307958] kjournald starting.  Commit interval 5 seconds
[   55.307971] EXT3-fs: mounted filesystem with ordered data mode.
[   57.343491] usb-storage: device scan complete
[   57.349966] scsi 7:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   57.356466] scsi 7:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   57.363082] scsi 7:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   57.369710] scsi 7:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   57.371101] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   57.371123] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   57.372228] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[   57.372256] sd 7:0:0:1: Attached scsi generic sg4 type 0
[   57.373348] sd 7:0:0:2: [sde] Attached SCSI removable disk
[   57.373377] sd 7:0:0:2: Attached scsi generic sg5 type 0
[   57.374474] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[   57.374506] sd 7:0:0:3: Attached scsi generic sg6 type 0
[   62.070659] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   62.250958] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   62.270593] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   62.277048] iTCO_vendor_support: vendor-support=0
[   62.278339] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   62.278398] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0860)
[   62.278428] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   62.313250] input: Power Button (FF) as /devices/virtual/input/input3
[   62.371916] ACPI: Power Button (FF) [PWRF]
[   62.371977] input: Power Button (CM) as /devices/virtual/input/input4
[   62.479922] ACPI: Power Button (CM) [PWRB]
[   62.724785] lirc_dev: IR Remote Control driver registered, at major 61 
[   62.812364] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2504
[   62.812376] usbcore: registered new interface driver usblp
[   62.897196] nvidia: module license 'NVIDIA' taints kernel.
[   63.150421] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   63.150432] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   63.150522] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   63.257990] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   63.364560] 
[   63.364561] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   63.364563] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   63.618328] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[   63.762985] cx23885 driver version 0.0.1 loaded
[   63.763045] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   63.763055] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   63.768029] lirc_dev: lirc_register_plugin: sample_rate: 0
[   63.772022] lirc_mceusb2[3]:   BB+ Dongle(e.d) on usb2:3
[   63.772042] usbcore: registered new interface driver lirc_mceusb2
[   63.863212] cx23885[0]: i2c bus 0 registered
[   63.863225] cx23885[0]: i2c bus 1 registered
[   63.863238] cx23885[0]: i2c bus 2 registered
[   63.890824] tveeprom 0-0050: Hauppauge model 78521, rev C1E9, serial# 4936513
[   63.890826] tveeprom 0-0050: MAC address is 00-0D-FE-4B-53-41
[   63.890827] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 4)
[   63.890829] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   63.890831] tveeprom 0-0050: audio processor is CX23887 (idx 42)
[   63.890832] tveeprom 0-0050: decoder processor is CX23887 (idx 37)
[   63.890833] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   63.890835] cx23885[0]: hauppauge eeprom: model=78521
[   63.890836] cx23885[0]: cx23885 based dvb card
[   63.981067] MT2131: successfully identified at address 0x61
[   63.981070] DVB: registering new adapter (cx23885[0])
[   63.981073] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   63.981280] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xf9e00000
[   63.981286] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   64.133268] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   64.134068] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   64.164051] phy0: Selected rate control algorithm 'simple'
[   64.164480] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   64.288007] usbcore: registered new interface driver rt73usb
[   64.546051] lp: driver loaded but no devices found
[   64.627627] Adding 9767512k swap on /dev/sda4.  Priority:-1 extents:1 across:9767512k
[  238.315512] EXT3 FS on sda2, internal journal
[  239.074293] ip_tables: (C) 2000-2006 Netfilter Core Team
[  239.259384] No dock devices found.
[  240.137957] ppdev: user-space parallel port driver
[  240.283147] audit(1225240339.861:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8090 profile="/usr/sbin/cupsd" namespace="default"
[  240.339461] QEMU Accelerator Module version 1.3.0, Copyright (c) 2005-2007 Fabrice Bellard
[  240.339492] KQEMU installed, max_locked_mem=2027300kB.
[  240.361434] kvm: disabled by bios
[  241.288924] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  241.288930] vboxdrv: Successfully done.
[  241.288931] vboxdrv: Found 4 processor cores.
[  241.289034] vboxdrv: fAsync=0 offMin=0xa14 offMax=0x2760
[  241.289039] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  241.289041] vboxdrv: Successfully loaded version 2.0.4 (interface 0x00090000).
[  242.772135] Bluetooth: Core ver 2.11
[  242.772327] NET: Registered protocol family 31
[  242.772330] Bluetooth: HCI device and connection manager initialized
[  242.772333] Bluetooth: HCI socket layer initialized
[  242.809685] Bluetooth: L2CAP ver 2.9
[  242.809690] Bluetooth: L2CAP socket layer initialized
[  242.887556] Bluetooth: RFCOMM socket layer initialized
[  242.887571] Bluetooth: RFCOMM TTY layer initialized
[  242.887573] Bluetooth: RFCOMM ver 1.8
[  279.048198] NET: Registered protocol family 10
[  279.048445] lo: Disabled Privacy Extensions
[  279.049000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  285.901641] NET: Registered protocol family 17
[  287.062283] wlan0: Initial auth_alg=0
[  287.062291] wlan0: authenticate with AP 00:14:d1:37:df:bc
[  287.064426] wlan0: RX authentication from 00:14:d1:37:df:bc (alg=0 transaction=2 status=0)
[  287.064428] wlan0: authenticated
[  287.064430] wlan0: associate with AP 00:14:d1:37:df:bc
[  287.066791] wlan0: RX AssocResp from 00:14:d1:37:df:bc (capab=0x421 status=0 aid=1)
[  287.066794] wlan0: associated
[  287.066796] wlan0: switched to short barker preamble (BSSID=00:14:d1:37:df:bc)
[  287.071335] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  303.339141] wlan0: no IPv6 routers present

---

### Post by no_bikes on 2008-10-28
Problem fixed, When the kernal upgraded it rolled back to Ubutus default driver. I installed a new driver from 

[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

Stupid of me not to figure it out, That is how i got the card working in the first place 

Thanks, Travis

---

