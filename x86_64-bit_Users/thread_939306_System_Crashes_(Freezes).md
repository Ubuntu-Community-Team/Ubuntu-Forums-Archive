---
title: "System Crashes (Freezes)"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by dahshapat on 2008-10-05
Salutations UF community!

I'll try to be as forthcoming as I can, but being that English is not my default (I'm sure there's a better way of saying this) language perhaps I won't be able to, now, moving to the point of interest...

...I installed Ubuntu in my Dell Inspiron 1318 and it's working quite well, so I decided to try it in my desktop computer, but while everything seems to be perfectly fine, from time to time the computer just crashes without any particular reason (at least to my knowledge), and although certain things regularly (but not necessarily always) crash my system (like the OpenOffice or the "System-->Administration-->**Hardware Drivers**")other times it just seems to happen without a discernible pattern, I must say I'm not that familiar with the Linux environment so I'm not quite sure what to do to find the root of the problem, I'll paste my hardware configuration which I obtained through the 'lshw' command hoping perhaps it could help you help my with my problem, because (as you should have probably guessed already) I'm assuming this is a hardware incompatibility problem:

```

dahshapat@dahshapat-desktop:~$ sudo lshw
[sudo] password for dahshapat: 
dahshapat-desktop         
    description: Desktop Computer
    product: A33G
    vendor: PCCHIPS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=0 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: A33G
       vendor: PCCHIPS
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080013 (02/02/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          serial: To Be Filled By O.E.M.
          slot: U
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 1983MiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci:0
          description: Host bridge
          product: 761/M761 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS965 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 48
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0411N
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TW10
                serial: S01JJ10YA40784
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0fffe5d8
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 2502456a-7b92-44de-987b-eed272fd1a2f
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-10-05 11:38:17 filesystem=ext3 modified=2008-10-05 17:55:24 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-10-05 17:52:48 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H54N
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [HL-DT-STDVD-RAM GSA-H54N1.0007/03/07
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network:0
             description: Ethernet interface
             product: 190 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 00
             serial: 00:19:21:ee:32:bf
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
        *-ide:1
             description: IDE interface
             product: 182 SATA/RAID Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=64 module=sata_sis
           *-disk:0
                description: ATA Disk
                product: WDC WD1600AAJS-1
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 05.0
                serial: WD-WMAP92935537
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=01010101
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 9cae3f0a-2bee-c64d-82bd-262ca2cea9e2
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-12-02 13:57:56 filesystem=ntfs label=Documentos state=clean
           *-disk:1
                description: ATA Disk
                product: Hitachi HDS72161
                vendor: Hitachi
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: P22O
                serial: PVF904Z21ZW9AN
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=718b4b21
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: 782b9770-87ae-b74c-9bde-2d5354e571ca
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-02-17 12:20:54 filesystem=ntfs label=Movilidad state=clean
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-network:1
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: wifi0
             version: 01
             serial: 00:15:e9:b7:60:e0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci ip=192.168.1.67 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-pci:3
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress ht msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

```

Should you need more information I'll be more than willing to give it to you, just teach me how to get the it for you.

Thank you for your time reading my post, I'll appreciate any help offered.

[RIGHT]Sincerely yours
Zefasta Atranda-Exagran.[/RIGHT]

---

