---
title: "How can se if my computer is AMD 64 platform ?"
date: 2009-02-17
forum: x86 64-bit Users
---

### Post by hoboy on 2009-02-17
Please forgive me for this newbie question, i have just bought a new 
Fujitsu Siemens stationary PC
they told me at the shop that it was 64 bits.
The pc is 
AMILPI3620E01,
Intel Core?2 Quad Q8200.
NVIDIA® 9500GS grafikcard,
Chipset  NVIDIA nForce 630i 
 I want to know because I have tried to install an oracle db with failed because of it, is this a x8664bits ?

---

### Post by cdtech on 2009-02-17
Look through your hardware for the cpu specs:
```
lshw
```

---

### Post by hoboy on 2009-02-17
> **cdtech said:**
> Look through your hardware for the cpu specs:
```
lshw
```

I have done it 
here is an extrat of it
 *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2003MHz
          capacity: 2003MHz
          width: 64 bits
          clock: 333MHz
Does that means that it is 8664 bits amd ?


And the hole output here
ubuntu                    
    description: Desktop Computer
    product: Amilo Desktop Pi3620A
    vendor: FUJITSU SIEMENS
    version: 10601011270
    serial: YSWF004969
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: chassis=desktop uuid=00000000-0000-0000-0000-00242110EDAF
  *-core
       description: Motherboard
       product: MS-7504VP-PV
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: 1.1
       serial: MS-7504B0811024812
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V3.0L (09/17/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2003MHz
          capacity: 2003MHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: 64T256020EU2.5C2
             vendor: Qimonda
             physical id: 0
             serial: 143C1805
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: 64T256020EU2.5C2
             vendor: Qimonda
             physical id: 1
             serial: 103E1805
             slot: DIMM1
             size: 2GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: MCP73 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP73 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: MCP73 SMBus
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP73 Co-processor
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: GeForce 7100/nForce 630i
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: MCP73 [nForce 630i] USB 2.0 Controller (EHCI)
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: MCP73 High Definition Audio
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 9
                bus info: pci@0000:01:09.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-pci:1
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:2
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide
             description: IDE interface
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: scsi0
             logical name: scsi1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD6400AAKS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WMASY5431844
                size: 596GiB (640GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=eceacad2
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 9a102070-ca6f-de42-a556-0bea86574992
                   size: 8998MiB
                   capacity: 9000MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-10-07 09:43:59 filesystem=ntfs label=WinRE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: aa910c83-150d-064c-a286-1ca71f99815e
                   size: 75GiB
                   capacity: 76GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-07 09:44:03 filesystem=ntfs label=SYSTEM state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /host
                   logical name: /boot
                   version: 3.1
                   serial: d8600b77-05d4-cf4c-9ac9-97c19c813dda
                   size: 511GiB
                   capacity: 511GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-10-07 09:44:10 filesystem=ntfs label=DATA mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7200S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.83
                serial: [Optiarc DVD RW AD-7200S 1.83 Dec07,2007
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-network
             description: Ethernet interface
             product: MCP73 Ethernet
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth0
             version: a2
             serial: 00:24:21:10:ed:af
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.2 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 1
          bus info: usb@1:9
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:8f:e6:9e:2a:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by cdtech on 2009-02-17
> width: 64 bits
Yes.....

---

### Post by hoboy on 2009-02-17
> **cdtech said:**
> Yes.....
Thanks for your help
so, from now if i am looking for software like oracle db to install I should look for 8664bits. yesterday I tried to install oracle-xe-universal_10.2.0.1-1.0_i386.deb but got architecture error.

---

### Post by cdtech on 2009-02-17
> architecture error. 
Yes, you'll get that error if you have 64 installed and try to install a 32 bit program. Good luck.

---

### Post by jespdj on 2009-02-17
I don't think the output of lshw is telling you if you are running 32-bit or 64-bit Ubuntu. It only tells you the capabilities of the processor; not the Ubuntu variant that you're using.

To find out if you are running 32- or 64-bit Ubuntu:
```
uname -m
```
If it says **i686** (or i386) you're running 32-bit Ubuntu; if it says **x86_64** you're running 64-bit Ubuntu.

Note that 32-bit software also runs on 64-bit Ubuntu. Do some searching in the forums to find out how.

---

### Post by Clancy_s on 2009-02-17
> **jespdj said:**
> Note that 32-bit software also runs on 64-bit Ubuntu. Do some searching in the forums to find out how.

For things that don't have a how-to check out getlibs

---

### Post by cdtech on 2009-02-17
> they told me at the shop that it was 64 bits.
I was thinking the OP wanted to be sure it was a 64 processor, my bad if I miss understood.....

---

