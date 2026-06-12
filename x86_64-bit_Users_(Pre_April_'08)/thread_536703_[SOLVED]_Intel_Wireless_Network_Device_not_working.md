---
title: "[SOLVED] Intel Wireless Network Device not working"
date: 2007-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by very_japi on 2007-08-28
Sorry if my english is bad... but i have not spoken english sice i was like 7 or 8.

Back when i had windows all my hardware worked like a charm... those where so happy days, although Vista ate like 1.5Gb of RAM without me running anything so i decided to go the linux way.

Now my system resources are 95% free on boot which would be good if my DVD-RW, MIDI, headphones (soundtrack not working), and wireless weren't dead.  BUT  I'm not going back to Vista without putting up a fight! (there, I have said it,  up yurs Bill!)

SO my problem is basically described like this: Ubuntu does not beleave me when i say i have a wireless network device.

It does not appear on "Network settings" so... it's asically like it does not exist at all.

I've look on heaven, earth and hell for a solution by my self,  so i though why not look for help?

Im on a Centrino core 2 duo laptop, and the name of the wireless card is: 
Intel(R) PRO/Wireless 4965AGN Network Connection and Bluetooth(TM)
Bluetooth does not run either, by the way. Bluetooth used to work when i had Debian... but bluetooth was the only thing working so i switched to Ubuntu. Well... i switched to Ubuntu because of that, and because i did not like have an IceWeasel lazying around on my desktop, I mean... a Fire Fox could beat the crap out of an Ice Weasel any time. Ice Weasel has got to be the worst name a browser could have... but back to the point:

this is my sudo lshw
```
 description: Notebook
    product: HP Pavilion dv2500 Notebook PC
    vendor: Hewlett-Packard
    version: F.0A
    serial: 2CE7281VCR
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=28162820-31BA-11DC-B311-89A789AE2CB9
  *-core
       description: Motherboard
       product: 30CD
       vendor: Wistron
       physical id: 0
       version: 80.27
       slot: @
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: F.0A (05/28/2007)
          size: 102KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T5250
          slot: U2E1
          size: 1500MHz
          capacity: 1500MHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capacity: 4MB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 0c
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:f4000000-f40fffff iomemory:d0000000-dfffffff ioport:1800-1807 irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 0c
             size: 1MB
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:f4100000-f41fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Fingerprint Sensor
                   physical id: 1
                   bus info: usb@4:1
                   version: 6.23
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:f4705c00-f4705fff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:f4500000-f4503fff irq:22
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@04:00.0
                logical name: eth0
                version: 14
                serial: 00:16:d3:a5:b8:45
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.68 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:f4200000-f4203fff ioport:3000-30ff irq:17
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@06:00.0
                version: 61
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: iomemory:f4300000-f4301fff irq:11
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1880-189f irq:23
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:18a0-18bf irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft 3-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@6:2
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:18c0-18df irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Bluetooth wireless interface
                   product: HP Integrated Module
                   vendor: Broadcom Corp
                   physical id: 2
                   bus info: usb@7:2
                   version: 1.00
                   capabilities: bluetooth usb-2.00
                   configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:f4706000-f47063ff irq:23
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Video
                   product: HP Webcam
                   vendor: Chicony Electronics Co., Ltd.
                   physical id: 5
                   bus info: usb@2:5
                   version: 6.04
                   serial: SN0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@07:09.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: iomemory:f4400000-f44007ff irq:16
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@07:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=32
                resources: iomemory:f4400800-f44008ff irq:18
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@07:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
                resources: iomemory:f4400c00-f4400cff irq:10
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@07:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
                resources: iomemory:f4401000-f44010ff irq:10
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.4
                bus info: pci@07:09.4
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
                resources: iomemory:f4401400-f44014ff irq:10
        *-isa
             description: ISA bridge
             product: Mobile LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide UNCLAIMED
             description: IDE interface
             product: Mobile IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1830-183f irq:255
        *-storage
             description: SATA controller
             product: Mobile SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:18f8-18ff ioport:18ec-18ef ioport:18f0-18f7 ioport:18e8-18eb ioport:1c00-1c1f iomemory:f4705000-f47057ff irq:20
           *-disk
                description: SCSI Disk
                product: FUJITSU MHW2160B
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 891F
                serial: K10NT762DJ0M
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 13GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2588MB
                   capacity: 2588MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2588MB
                      capabilities: nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 132GB
                   capabilities: primary
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:88000000-880000ff ioport:1c20-1c3f irq:11
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0.0V
```

and this is mi dmseg

```
[    0.000000] Command line: root=UUID=ca53e1b3-6595-45ac-a0c0-7565ef65e778 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6c0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6c0000 - 000000007f6df000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6df000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 521920) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 PTLTD                                 ) @ 0x00000000000f7e10
[    0.000000] ACPI: XSDT (v001 HPQOEM SLIC-MPC 0x06040000  LTP 0x00000000) @ 0x000000007f6d0767
[    0.000000] ACPI: FADT (v003 INTEL  CRESTLNE 0x06040000 ALAN 0x00000001) @ 0x000000007f6dbbd2
[    0.000000] ACPI: MADT (v001 INTEL  CRESTLNE 0x06040000 LOHR 0x0000005a) @ 0x000000007f6dbcc6
[    0.000000] ACPI: HPET (v001 INTEL  CRESTLNE 0x06040000 LOHR 0x0000005a) @ 0x000000007f6dbd2e
[    0.000000] ACPI: MCFG (v001 INTEL  CRESTLNE 0x06040000 LOHR 0x0000005a) @ 0x000000007f6dbd66
[    0.000000] ACPI: TCPA (v001 Intel   CRESTLN 0x06040000  0x00005a52) @ 0x000000007f6dbda2
[    0.000000] ACPI: TMOR (v001 PTLTD           0x06040000 PTL  0x00000003) @ 0x000000007f6dbdd4
[    0.000000] ACPI: SLIC (v001 HPQOEM SLIC-MPC 0x06040000 HPQ  0x00000001) @ 0x000000007f6dbdfa
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x000000007f6dbf70
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000007f6dbfd8
[    0.000000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20060912) @ 0x000000007f6d127e
[    0.000000] ACPI: SSDT (v001 BrtRef  DD01BRT 0x00001000 INTL 0x20060912) @ 0x000000007f6d10e1
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20060912) @ 0x000000007f6d07eb
[    0.000000] ACPI: DSDT (v002 INTEL  CRESTLNE 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007f6c0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 521920) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007f6c0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   521920
[    0.000000] On node 0 totalpages: 521823
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2856 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7079 pages used for memmap
[    0.000000]   DMA32 zone: 510745 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
[    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 513601
[    0.000000] Kernel command line: root=UUID=ca53e1b3-6595-45ac-a0c0-7565ef65e778 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   19.875404] Console: colour VGA+ 80x25
[   19.876587] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   19.877621] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.877826] Checking aperture...
[   19.877840] Calgary: detecting Calgary via BIOS EBDA area
[   19.877843] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   19.899616] Memory: 2044344k/2087680k available (2217k kernel code, 42948k reserved, 1162k data, 304k init)
[   19.979086] Calibrating delay using timer specific routine.. 2997.10 BogoMIPS (lpj=5994203)
[   19.979148] Security Framework v1.0.0 initialized
[   19.979154] SELinux:  Disabled at boot.
[   19.979181] Mount-cache hash table entries: 256
[   19.979350] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.979353] CPU: L2 cache: 2048K
[   19.979356] CPU 0/0 -> Node 0
[   19.979358] using mwait in idle threads.
[   19.979361] CPU: Physical Processor ID: 0
[   19.979362] CPU: Processor Core ID: 0
[   19.979369] CPU0: Thermal monitoring handled by SMI
[   19.979381] SMP alternatives: switching to UP code
[   19.979673] Early unpacking initramfs... done
[   20.406573] ACPI: Core revision 20060707
[   20.406882] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   20.581407] Using local APIC timer interrupts.
[   20.648207] result 10391713
[   20.648209] Detected 10.391 MHz APIC timer.
[   20.650979] SMP alternatives: switching to SMP code
[   20.651127] Booting processor 1/2 APIC 0x1
[   20.661794] Initializing CPU#1
[   20.738747] Calibrating delay using timer specific routine.. 2992.93 BogoMIPS (lpj=5985865)
[   20.738755] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.738757] CPU: L2 cache: 2048K
[   20.738760] CPU 1/1 -> Node 0
[   20.738762] CPU: Physical Processor ID: 0
[   20.738763] CPU: Processor Core ID: 1
[   20.738770] CPU1: Thermal monitoring enabled (TM2)
[   20.739142] Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz stepping 0d
[   20.742743] CPU 1: Syncing TSC to CPU 0.
[   20.742842] CPU 1: synchronized TSC with CPU 0 (last diff -4 cycles, maxerr 342 cycles)
[   20.742858] Brought up 2 CPUs
[   20.742909] time.c: Using 14.318180 MHz WALL HPET GTOD HPET timer.
[   20.742912] time.c: Detected 1496.408 MHz processor.
[   20.851932] migration_cost=22
[   20.852299] Time: 10:49:09  Date: 07/26/107
[   20.852338] NET: Registered protocol family 16
[   20.852424] ACPI: bus type pci registered
[   20.852432] PCI: Using configuration type 1
[   20.860141] ACPI: Interpreter enabled
[   20.860144] ACPI: Using IOAPIC for interrupt routing
[   20.862165] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.862172] PCI: Probing PCI hardware (bus 00)
[   20.862253] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   20.863287] Boot video device is 0000:00:02.0
[   20.865483] PCI: Transparent bridge - 0000:00:1e.0
[   20.865591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.871834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   20.872175] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   20.872513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   20.872856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   20.873510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   20.874706] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   20.875040] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   20.875368] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   20.875696] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   20.876024] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   20.876357] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   20.876685] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   20.877014] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   20.893558] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.893570] pnp: PnP ACPI init
[   20.898441] pnp: PnP ACPI: found 10 devices
[   20.898499] PCI: Using ACPI for IRQ routing
[   20.898502] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.898638] NET: Registered protocol family 8
[   20.898640] NET: Registered protocol family 20
[   20.898654] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   20.898659] hpet0: 3 64-bit timers, 14318180 Hz
[   20.899697] PCI-GART: No AMD northbridge found.
[   20.900418] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   20.900428] PCI: Bridge: 0000:00:1c.0
[   20.900432]   IO window: 2000-2fff
[   20.900439]   MEM window: f2000000-f3ffffff
[   20.900444]   PREFETCH window: f0000000-f1ffffff
[   20.900451] PCI: Bridge: 0000:00:1c.1
[   20.900455]   IO window: 3000-3fff
[   20.900461]   MEM window: f4200000-f42fffff
[   20.900466]   PREFETCH window: disabled.
[   20.900472] PCI: Bridge: 0000:00:1c.2
[   20.900474]   IO window: disabled.
[   20.900481]   MEM window: disabled.
[   20.900485]   PREFETCH window: disabled.
[   20.900492] PCI: Bridge: 0000:00:1c.3
[   20.900494]   IO window: disabled.
[   20.900501]   MEM window: f4300000-f43fffff
[   20.900505]   PREFETCH window: disabled.
[   20.900512] PCI: Bridge: 0000:00:1e.0
[   20.900514]   IO window: disabled.
[   20.900520]   MEM window: f4400000-f44fffff
[   20.900525]   PREFETCH window: disabled.
[   20.900558] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.900566] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.900592] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 16 (level, low) -> IRQ 16
[   20.900598] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.900622] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.900629] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.900652] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   20.900658] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   20.900672] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.900711] NET: Registered protocol family 2
[   20.942709] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.942969] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   20.945131] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   20.945848] TCP: Hash tables configured (established 262144 bind 65536)
[   20.945852] TCP reno registered
[   20.958825] checking if image is initramfs... it is
[   21.793420] Freeing initrd memory: 6800k freed
[   21.797779] Simple Boot Flag at 0x36 set to 0x1
[   21.798416] audit: initializing netlink socket (disabled)
[   21.798434] audit(1188125349.736:1): initialized
[   21.798627] VFS: Disk quotas dquot_6.5.1
[   21.798651] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.798710] io scheduler noop registered
[   21.798713] io scheduler anticipatory registered
[   21.798716] io scheduler deadline registered
[   21.798731] io scheduler cfq registered (default)
[   21.799090] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.799154] assign_interrupt_mode Found MSI capability
[   21.799158] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.799196] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.799334] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.799398] assign_interrupt_mode Found MSI capability
[   21.799401] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.799436] Allocate Port Service[0000:00:1c.1:pcie02]
[   21.799571] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.799635] assign_interrupt_mode Found MSI capability
[   21.799637] Allocate Port Service[0000:00:1c.2:pcie00]
[   21.799673] Allocate Port Service[0000:00:1c.2:pcie02]
[   21.799809] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   21.799872] assign_interrupt_mode Found MSI capability
[   21.799875] Allocate Port Service[0000:00:1c.3:pcie00]
[   21.799909] Allocate Port Service[0000:00:1c.3:pcie02]
[   21.824122] Real Time Clock Driver v1.12ac
[   21.824179] Linux agpgart interface v0.102 (c) Dave Jones
[   21.824182] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.824812] mice: PS/2 mouse device common for all mice
[   21.825425] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.825586] input: Macintosh mouse button emulation as /class/input/input0
[   21.825623] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.825628] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.825956] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.826315] i8042.c: Detected active multiplexing controller, rev 1.1.
[   21.826398] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.826402] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   21.826405] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   21.826408] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   21.826411] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   21.826596] TCP cubic registered
[   21.826606] NET: Registered protocol family 1
[   21.826742] ACPI: (supports S0 S3 S4 S5)
[   21.826792]   Magic number: 3:812:831
[   21.826885]   hash matches device ptyqe
[   21.826917] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   21.826993] Freeing unused kernel memory: 304k freed
[   21.829713] input: AT Translated Set 2 keyboard as /class/input/input1
[   23.015958] Capability LSM initialized
[   23.053761] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[   23.054030] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[   23.054487] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   23.055116] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[   23.055377] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[   23.055911] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   23.067894] ACPI: Thermal Zone [TZS0] (48 C)
[   23.072994] ACPI: Thermal Zone [TZS1] (52 C)
[   23.503846] usbcore: registered new interface driver usbfs
[   23.503878] usbcore: registered new interface driver hub
[   23.530059] ieee1394: Initialized config rom entry `ip1394'
[   23.539528] usbcore: registered new device driver usb
[   23.579373] ACPI: PCI Interrupt 0000:07:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.632296] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   23.632315] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   23.632319] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   23.632584] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   23.632625] ehci_hcd 0000:00:1a.7: debug port 1
[   23.632633] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   23.632645] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf4705c00
[   23.636521] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.636537] USB Universal Host Controller Interface driver v3.0
[   23.637792] usb usb1: configuration #1 chosen from 1 choice
[   23.637969] hub 1-0:1.0: USB hub found
[   23.637977] hub 1-0:1.0: 4 ports detected
[   23.638439] SCSI subsystem initialized
[   23.652150] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4400000-f44007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.656280] libata version 2.20 loaded.
[   23.669249] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   23.669286] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.669291] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.669442] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   23.669480] ehci_hcd 0000:00:1d.7: debug port 1
[   23.669487] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.669498] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4706000
[   23.673384] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.673848] usb usb2: configuration #1 chosen from 1 choice
[   23.674020] hub 2-0:1.0: USB hub found
[   23.674027] hub 2-0:1.0: 6 ports detected
[   23.701252] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.701266] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   23.701270] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.701298] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   23.701330] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001840
[   23.701431] usb usb3: configuration #1 chosen from 1 choice
[   23.701462] hub 3-0:1.0: USB hub found
[   23.701468] hub 3-0:1.0: 2 ports detected
[   23.728296] ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 21
[   23.728314] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   23.728320] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.728352] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   23.728392] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001860
[   23.728497] usb usb4: configuration #1 chosen from 1 choice
[   23.728525] hub 4-0:1.0: USB hub found
[   23.728532] hub 4-0:1.0: 2 ports detected
[   23.753871] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   23.753886] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.753892] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.753923] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   23.753957] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[   23.754068] usb usb5: configuration #1 chosen from 1 choice
[   23.754096] hub 5-0:1.0: USB hub found
[   23.754102] hub 5-0:1.0: 2 ports detected
[   23.772405] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
[   23.772420] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.772426] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.772460] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   23.772499] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[   23.772605] usb usb6: configuration #1 chosen from 1 choice
[   23.772635] hub 6-0:1.0: USB hub found
[   23.772641] hub 6-0:1.0: 2 ports detected
[   23.798456] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.798471] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.798478] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.798514] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   23.798547] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[   23.798657] usb usb7: configuration #1 chosen from 1 choice
[   23.798684] hub 7-0:1.0: USB hub found
[   23.798689] hub 7-0:1.0: 2 ports detected
[   23.815353] usb 2-5: new high speed USB device using ehci_hcd and address 3
[   23.830313] ahci 0000:00:1f.2: version 2.1
[   23.830352] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 20 (level, low) -> IRQ 20
[   23.894266] usb 2-5: configuration #1 chosen from 1 choice
[   23.997890] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   24.005058] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[07e40a0036a95026]
[   24.045721] usb 4-1: configuration #1 chosen from 1 choice
[   24.096944] usb 6-2: new low speed USB device using uhci_hcd and address 2
[   24.119137] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.119149] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   24.119156] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   24.119327] ata1: SATA max UDMA/133 cmd 0xffffc20000054100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 20
[   24.119428] ata2: SATA max UDMA/133 cmd 0xffffc20000054180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 20
[   24.119532] ata3: SATA max UDMA/133 cmd 0xffffc20000054200 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 20
[   24.119544] scsi0 : ahci
[   24.157065] usb 6-2: configuration #1 chosen from 1 choice
[   24.238196] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.238629] ata1.00: ATA-7: FUJITSU MHW2160BH PL, 891F, max UDMA/100
[   24.238635] ata1.00: 312581808 sectors, multi 16: LBA48 
[   24.239211] ata1.00: configured for UDMA/100
[   24.239225] scsi1 : ahci
[   24.247187] usb 7-2: new full speed USB device using uhci_hcd and address 2
[   24.305903] usb 7-2: configuration #1 chosen from 1 choice
[   24.307804] usbcore: registered new interface driver hiddev
[   24.322511] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   24.322534] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-2
[   24.322555] usbcore: registered new interface driver usbhid
[   24.322559] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   24.350375] ata2: SATA link down (SStatus 0 SControl 300)
[   24.350417] scsi2 : ahci
[   24.419396] ata3: SATA link down (SStatus 0 SControl 300)
[   24.419561] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 891F PQ: 0 ANSI: 5
[   24.426581] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   24.426594] sda: Write Protect is off
[   24.426597] sda: Mode Sense: 00 3a 00 00
[   24.426613] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.426662] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   24.426672] sda: Write Protect is off
[   24.426674] sda: Mode Sense: 00 3a 00 00
[   24.426690] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.426695]  sda: sda1 sda2 < sda5 > sda3
[   24.530179] sd 0:0:0:0: Attached scsi disk sda
[   24.533338] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.735017] Attempting manual resume
[   24.735021] swsusp: Resume From Partition 8:5
[   24.735023] PM: Checking swsusp image.
[   24.735253] PM: Resume from disk failed.
[   24.782319] kjournald starting.  Commit interval 5 seconds
[   24.782352] EXT3-fs: mounted filesystem with ordered data mode.
[   35.352746] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.363283] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.501487] sdhci: Secure Digital Host Controller Interface driver
[   35.501491] sdhci: Copyright(c) Pierre Ossman
[   35.501531] sdhci: SDHCI controller found at 0000:07:09.1 [1180:0822] (rev 22)
[   35.501553] ACPI: PCI Interrupt 0000:07:09.1[b] -> GSI 18 (level, low) -> IRQ 18
[   35.501617] mmc0: SDHCI at 0xf4400800 irq 18 DMA
[   35.729741] agpgart: Detected an Intel 965GM Chipset.
[   35.730372] agpgart: Detected 7676K stolen memory.
[   35.756887] agpgart: AGP aperture is 256M @ 0xd0000000
[   35.843495] Bluetooth: Core ver 2.11
[   35.843562] NET: Registered protocol family 31
[   35.843564] Bluetooth: HCI device and connection manager initialized
[   35.843567] Bluetooth: HCI socket layer initialized
[   35.884417] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.884434] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   35.884469] sky2 0000:04:00.0: v1.13 addr 0xf4200000 irq 17 Yukon-FE (0xb7) rev 3
[   35.884589] sky2 eth0: addr 00:16:d3:a5:b8:45
[   35.898992] Bluetooth: HCI USB driver ver 2.9
[   35.899474] sky2 eth0: enabling interface
[   35.901685] sky2 eth0: ram buffer 4K
[   35.991093] usbcore: registered new interface driver hci_usb
[   36.010571] input: PS/2 Mouse as /class/input/input3
[   36.019549] Linux video capture interface: v2.00
[   36.030133] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   36.140679] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b016)
[   36.142333] usbcore: registered new interface driver uvcvideo
[   36.142337] USB Video Class driver (v0.1.0)
[   36.235691] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   36.235716] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   36.420910] lp: driver loaded but no devices found
[   36.560392] Adding 2650684k swap on /dev/disk/by-uuid/67eb5dde-9597-4525-bb79-2e0eea1d33e0.  Priority:-1 extents:1 across:2650684k
[   36.701242] EXT3 FS on sda1, internal journal
[   36.873941] NET: Registered protocol family 17
[   36.891581] kjournald starting.  Commit interval 5 seconds
[   36.892174] EXT3 FS on sda3, internal journal
[   36.892182] EXT3-fs: mounted filesystem with ordered data mode.
[   37.437672] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   38.496356] input: Power Button (FF) as /class/input/input5
[   38.496543] ACPI: Power Button (FF) [PWRF]
[   38.524533] input: Lid Switch as /class/input/input6
[   38.524615] ACPI: Lid Switch [LID0]
[   38.524666] input: Sleep Button (CM) as /class/input/input7
[   38.524694] ACPI: Sleep Button (CM) [SLPB]
[   38.620901] ACPI: AC Adapter [ADP1] (on-line)
[   38.636382] No dock devices found.
[   38.705738] ACPI: Battery Slot [BAT0] (battery present)
[   38.796607] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   38.797686] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   38.832690] Using specific hotkey driver
[   38.851865] ibm_acpi: ec object not found
[   38.880648] wmi_add device=ffff81007c6ea800
[   38.880652] calling WQBA
[   38.908212] pcc_acpi: loading...
[   39.209238] NET: Registered protocol family 10
[   39.209379] lo: Disabled Privacy Extensions
[   43.396190] mtrr: no more MTRRs available
[   43.877702] ppdev: user-space parallel port driver
[   44.977975] Bluetooth: L2CAP ver 2.8
[   44.977981] Bluetooth: L2CAP socket layer initialized
[   45.065971] Bluetooth: RFCOMM socket layer initialized
[   45.065988] Bluetooth: RFCOMM TTY layer initialized
[   45.065991] Bluetooth: RFCOMM ver 1.8
[   49.964309] eth0: no IPv6 routers present
```

i Suspect THIS is my wireless card thingy:
```
*-network UNCLAIMED
description: Network controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 0
bus info: pci@06:00.0
version: 61
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: iomemory:f4300000-f4301fff irq:11
```

lspci: (my network devices)
```
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)
06:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)

```

ifconfig: (I don't even think my wreless is even listed in here)
```
eth0      Link encap:Ethernet  HWaddr 00:16:D3:A5:B8:45  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fea5:b845/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11308315 (10.7 MiB)  TX bytes:3266665 (3.1 MiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1668 (1.6 KiB)  TX bytes:1668 (1.6 KiB)


```

iwconfig: (this part really looks bad for me)

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

I'v read everything out there but to no avail. Please help me get this fine OS running.

---

### Post by wjp.reg on 2007-08-28
[This]("http://ubuntuforums.org/showthread.php?t=512059&highlight=dv2000") may help you somewhat.

Good Luck

---

### Post by very_japi on 2007-08-29
> **wjp.reg said:**
> [This]("http://ubuntuforums.org/showthread.php?t=512059&highlight=dv2000") may help you somewhat.

Good Luck

got as far as 

```
make patch_kernel
```

and i get this error:
```

Kernel Makefile not found at '/lib/modules/2.6.22-10-generic/source/' If patch or script failed, check pre/ and post/ for current stage.
```

i tried looking for a place to download the kernel source, but cant fnd it. Although i don't even now if finding the source will make any difference

---

### Post by very_japi on 2007-08-29
i had already tried that, actually... whenever i tried to build the  iwlwifi-0.1.12  got an INSANE amount of errors:

and that's after hours (actually... like 45 mins) spent trying to get t to run.

```
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8812: warning: (near initialization for ‘dev_attr_rate’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8815: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘store_retry_rate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8828: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘show_retry_rate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: error: ‘show_retry_rate’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: warning: (near initialization for ‘dev_attr_retry_rate’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: error: ‘store_retry_rate’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8835: warning: (near initialization for ‘dev_attr_retry_rate’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8838: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘store_power_level’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8878: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘timeout_duration’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8885: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘period_duration’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8893: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘show_power_level’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: error: ‘show_power_level’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: warning: (near initialization for ‘dev_attr_power_level’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: error: ‘store_power_level’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8925: warning: (near initialization for ‘dev_attr_power_level’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:8928: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘show_channels’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: error: ‘show_channels’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: warning: (near initialization for ‘dev_attr_channels’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9000: warning: (near initialization for ‘dev_attr_channels’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9002: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘show_statistics’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: error: ‘show_statistics’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: warning: (near initialization for ‘dev_attr_statistics’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9038: warning: (near initialization for ‘dev_attr_statistics’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9040: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘show_antenna’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9051: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘store_antenna’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: error: ‘show_antenna’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: warning: (near initialization for ‘dev_attr_antenna’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: error: ‘store_antenna’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9076: warning: (near initialization for ‘dev_attr_antenna’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9078: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘show_status’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: error: ‘show_status’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: warning: (near initialization for ‘dev_attr_status’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9087: warning: (near initialization for ‘dev_attr_status’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9089: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_error_log’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: warning: (near initialization for ‘dev_attr_dump_errors’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: error: ‘dump_error_log’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9101: warning: (near initialization for ‘dev_attr_dump_errors’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_event_log’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: error: unknown field ‘mode’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: warning: initialization makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: error: unknown field ‘show’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: warning: (near initialization for ‘dev_attr_dump_events’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: error: unknown field ‘store’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: error: ‘dump_event_log’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9115: warning: (near initialization for ‘dev_attr_dump_events’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c: In function ‘iwl_setup_deferred_work’:
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9125: error: ‘struct iwl_priv’ has no member named ‘workqueue’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9127: error: ‘struct iwl_priv’ has no member named ‘wait_command_queue’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9129: error: ‘struct iwl_priv’ has no member named ‘up’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9129: error: ‘atomic_long_t’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9129: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9129: error: ‘struct iwl_priv’ has no member named ‘up’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9129: error: ‘struct iwl_priv’ has no member named ‘up’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9130: error: ‘struct iwl_priv’ has no member named ‘restart’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9130: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9130: error: ‘struct iwl_priv’ has no member named ‘restart’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9130: error: ‘struct iwl_priv’ has no member named ‘restart’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9131: error: ‘struct iwl_priv’ has no member named ‘rx_replenish’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9131: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9131: error: ‘struct iwl_priv’ has no member named ‘rx_replenish’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9131: error: ‘struct iwl_priv’ has no member named ‘rx_replenish’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9132: error: ‘struct iwl_priv’ has no member named ‘scan_completed’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9132: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9132: error: ‘struct iwl_priv’ has no member named ‘scan_completed’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9132: error: ‘struct iwl_priv’ has no member named ‘scan_completed’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9133: error: ‘struct iwl_priv’ has no member named ‘request_scan’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9133: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9133: error: ‘struct iwl_priv’ has no member named ‘request_scan’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9133: error: ‘struct iwl_priv’ has no member named ‘request_scan’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9134: error: ‘struct iwl_priv’ has no member named ‘abort_scan’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9134: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9134: error: ‘struct iwl_priv’ has no member named ‘abort_scan’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9134: error: ‘struct iwl_priv’ has no member named ‘abort_scan’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9135: error: ‘struct iwl_priv’ has no member named ‘rf_kill’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9135: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9135: error: ‘struct iwl_priv’ has no member named ‘rf_kill’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9135: error: ‘struct iwl_priv’ has no member named ‘rf_kill’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9136: error: ‘struct iwl_priv’ has no member named ‘beacon_update’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9136: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9136: error: ‘struct iwl_priv’ has no member named ‘beacon_update’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9136: error: ‘struct iwl_priv’ has no member named ‘beacon_update’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9137: error: ‘struct iwl_priv’ has no member named ‘post_associate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9137: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9137: error: ‘struct iwl_priv’ has no member named ‘post_associate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9137: error: ‘struct iwl_priv’ has no member named ‘post_associate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9137: error: ‘struct iwl_priv’ has no member named ‘post_associate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9138: error: ‘struct iwl_priv’ has no member named ‘init_alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9138: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9138: error: ‘struct iwl_priv’ has no member named ‘init_alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9138: error: ‘struct iwl_priv’ has no member named ‘init_alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9138: error: ‘struct iwl_priv’ has no member named ‘init_alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9139: error: ‘struct iwl_priv’ has no member named ‘alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9139: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9139: error: ‘struct iwl_priv’ has no member named ‘alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9139: error: ‘struct iwl_priv’ has no member named ‘alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9139: error: ‘struct iwl_priv’ has no member named ‘alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9140: error: ‘struct iwl_priv’ has no member named ‘scan_check’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9140: error: expected ‘;’ before ‘ATOMIC_LONG_INIT’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9140: error: ‘struct iwl_priv’ has no member named ‘scan_check’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9140: error: ‘struct iwl_priv’ has no member named ‘scan_check’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9140: error: ‘struct iwl_priv’ has no member named ‘scan_check’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9144: error: ‘struct iwl_priv’ has no member named ‘irq_tasklet’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c: In function ‘iwl_cancel_deferred_work’:
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9156: error: ‘struct iwl_priv’ has no member named ‘scan_check’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9157: error: ‘struct iwl_priv’ has no member named ‘alive_start’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9158: error: ‘struct iwl_priv’ has no member named ‘post_associate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c: At top level:
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9205: error: unknown field ‘get_tsf’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9205: error: ‘iwl_mac_get_tsf’ undeclared here (not in a function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9206: error: unknown field ‘reset_tsf’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9206: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9206: warning: (near initialization for ‘iwl_hw_ops’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9207: error: unknown field ‘beacon_update’ specified in initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9207: warning: excess elements in struct initializer
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9207: warning: (near initialization for ‘iwl_hw_ops’)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c: In function ‘iwl_pci_probe’:
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9226: error: ‘u32’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9226: error: expected ‘;’ before ‘pci_id’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9227: warning: ISO C90 forbids mixed declarations and code
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9232: error: ‘iwl_debug_level’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9232: error: invalid type argument of ‘->’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9240: error: ‘EINVAL’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9246: warning: implicit declaration of function ‘ieee80211_alloc_hw’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9246: warning: assignment makes pointer from integer without a cast
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9249: error: ‘ENOMEM’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9252: error: ‘struct pci_dev’ has no member named ‘dev’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9254: error: invalid type argument of ‘->’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9258: error: ‘struct iwl_priv’ has no member named ‘pci_dev’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9259: error: ‘struct iwl_priv’ has no member named ‘antenna’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9262: error: ‘struct iwl_priv’ has no member named ‘restrict_refcnt’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9264: error: ‘struct iwl_priv’ has no member named ‘retry_rate’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9266: error: ‘struct iwl_priv’ has no member named ‘ibss_beacon’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9273: error: ‘struct ieee80211_hw’ has no member named ‘max_rssi’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9274: error: ‘struct ieee80211_hw’ has no member named ‘max_noise’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9275: error: ‘struct ieee80211_hw’ has no member named ‘max_signal’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9278: error: ‘struct ieee80211_hw’ has no member named ‘flags’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9281: error: ‘struct ieee80211_hw’ has no member named ‘queues’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9290: error: ‘struct iwl_priv’ has no member named ‘lock’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9291: error: ‘struct iwl_priv’ has no member named ‘power_data’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9292: error: ‘struct iwl_priv’ has no member named ‘sta_lock’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9293: error: ‘struct iwl_priv’ has no member named ‘hcmd_lock’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9299: error: ‘struct iwl_priv’ has no member named ‘ibss_mac_hash’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9303: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9305: error: ‘ENODEV’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9313: error: ‘struct iwl_priv’ has no member named ‘data_retry_limit’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9316: error: ‘struct iwl_priv’ has no member named ‘phymode’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9318: error: too many arguments to function ‘pci_set_dma_mask’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9320: warning: implicit declaration of function ‘pci_set_consistent_dma_mask’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9332: error: too many arguments to function ‘pci_write_config_byte’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9333: error: ‘struct iwl_priv’ has no member named ‘hw_base’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9333: warning: implicit declaration of function ‘pci_iomap’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9334: error: ‘struct iwl_priv’ has no member named ‘hw_base’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9339: error: invalid type argument of ‘->’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9339: error: ‘struct pci_dev’ has no member named ‘resource’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9339: error: ‘struct pci_dev’ has no member named ‘resource’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9339: error: ‘struct pci_dev’ has no member named ‘resource’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9339: error: ‘struct pci_dev’ has no member named ‘resource’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9339: error: ‘struct pci_dev’ has no member named ‘resource’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9341: error: invalid type argument of ‘->’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9341: error: ‘struct iwl_priv’ has no member named ‘hw_base’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9346: error: ‘struct iwl_priv’ has no member named ‘status’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9347: error: invalid type argument of ‘->’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9350: error: ‘struct iwl_priv’ has no member named ‘iw_mode’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9352: error: ‘pci_id’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9353: error: ‘struct iwl_priv’ has no member named ‘pci_dev’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9353: error: ‘struct iwl_priv’ has no member named ‘pci_dev’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9375: error: ‘struct iwl_priv’ has no member named ‘is_abg’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9386: error: ‘struct iwl_priv’ has no member named ‘is_abg’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9392: error: ‘struct iwl_priv’ has no member named ‘is_abg’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9398: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9404: error: ‘struct iwl_priv’ has no member named ‘qos_data’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9405: error: ‘struct iwl_priv’ has no member named ‘qos_data’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9406: error: ‘struct iwl_priv’ has no member named ‘qos_data’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9409: error: too many arguments to function ‘iwl_set_rxon_channel’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9413: error: ‘struct iwl_priv’ has no member named ‘rates_mask’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9415: error: ‘struct iwl_priv’ has no member named ‘power_mode’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9416: error: ‘struct iwl_priv’ has no member named ‘user_txpower_limit’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9418: warning: implicit declaration of function ‘pci_enable_msi’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9420: error: ‘struct pci_dev’ has no member named ‘irq’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9422: error: ‘struct pci_dev’ has no member named ‘irq’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9426: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9428: error: ‘struct pci_dev’ has no member named ‘dev’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9431: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9440: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9444: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9446: error: invalid type argument of ‘->’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9448: error: ‘struct iwl_priv’ has no member named ‘workqueue’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9448: error: ‘struct iwl_priv’ has no member named ‘up’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9455: error: ‘struct pci_dev’ has no member named ‘dev’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9458: error: ‘struct pci_dev’ has no member named ‘irq’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9461: warning: implicit declaration of function ‘pci_disable_msi’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9462: error: ‘struct iwl_priv’ has no member named ‘workqueue’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9463: error: ‘struct iwl_priv’ has no member named ‘workqueue’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9467: warning: implicit declaration of function ‘pci_iounmap’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9467: error: ‘struct iwl_priv’ has no member named ‘hw_base’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c: In function ‘iwl_pci_remove’:
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9488: error: ‘iwl_debug_level’ undeclared (first use in this function)
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9488: error: invalid type argument of ‘->’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9490: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9491: error: ‘struct iwl_priv’ has no member named ‘status’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9493: error: ‘struct iwl_priv’ has no member named ‘mutex’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9497: error: ‘struct iwl_priv’ has no member named ‘ibss_mac_hash’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9497: warning: left-hand operand of comma expression has no effect
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9497: error: ‘struct iwl_priv’ has no member named ‘ibss_mac_hash’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9499: error: ‘struct iwl_ibss_seq’ has no member named ‘list’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9499: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9499: warning: initialization from incompatible pointer type
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9499: error: ‘struct iwl_ibss_seq’ has no member named ‘list’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9503: error: ‘struct pci_dev’ has no member named ‘dev’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9507: error: ‘struct iwl_priv’ has no member named ‘rxq’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9508: error: ‘struct iwl_priv’ has no member named ‘rxq’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9514: error: ‘struct iwl_priv’ has no member named ‘mac80211_registered’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9522: error: ‘struct iwl_priv’ has no member named ‘workqueue’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9523: error: ‘struct iwl_priv’ has no member named ‘workqueue’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9525: error: ‘struct pci_dev’ has no member named ‘irq’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9527: error: ‘struct iwl_priv’ has no member named ‘hw_base’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9532: error: ‘struct iwl_priv’ has no member named ‘channel_info’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9537: error: ‘struct iwl_priv’ has no member named ‘ibss_beacon’
/home/japi/Desktop/iwlwifi-0.1.12/compatible/iwl-base.c:9538: error: ‘struct iwl_priv’ has no member named ‘ibss_beacon’
make[3]: *** [/home/japi/Desktop/iwlwifi-0.1.12/compatible/base-3945.o] Error 1
make[2]: *** [_module_/home/japi/Desktop/iwlwifi-0.1.12/compatible] Error 2
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-10'
make: *** [modules] Error 2

```

---

### Post by very_japi on 2008-03-06
SOlved with Ubutu Sutsy. Aparently the old kernel didnt support my new hardware

---

