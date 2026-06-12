---
title: "Im thinking of &quot;the big switch&quot; to 64..."
date: 2009-07-29
forum: x86 64-bit Users
---

### Post by j7%&lt;RmUg on 2009-07-29
NOTE: This is not another "Should i get 64-bit?" question.

I had some spare time thismorning, so i thought id see if my (old) processor supports 64-bit or not. What i did what run this:

```
sudo lshw
```

It displays detailed info about your cpu, ram, hdds, etc. Here is mine:

```

    ryan-desktop              
    description: Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=45F49FE3-8B6C-11DB-9A4A-000EA68F7369
  *-core
       description: Motherboard
       product: D946GZIS
       vendor: Intel Corporation
       physical id: 0
       version: AAD83227-401
       serial: LAIS650000K0
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          size: 3066MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 3
          version: TS94610J.86A.0047.2006.0911.0110 (09/11/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x000000000000000000000000000000000000
             vendor: 0x0000000000000000
             physical id: 0
             serial: 0x00000000
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6H2
        *-bank:2
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 2
             serial: NO DIMM
             slot: J6J1
        *-bank:3
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J6J2
     *-pci
          description: Host bridge
          product: 82946GZ/PL/GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82946GZ/PL/GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8500 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network:0
                description: Wireless interface
                product: RT2561/RT61 rev B 802.11g
                vendor: RaLink
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: wmaster0
                version: 00
                serial: 00:15:e9:a8:d7:36
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci ip=192.168.0.2 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
           *-network:1
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth2
                version: 01
                serial: 00:19:d1:20:b3:1b
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVR-112D
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.28
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: SAMSUNG SP2014N
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: VC10
                serial: S088J1LLA01436
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f021f021
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3ca1ac6d-cfb3-4c27-a021-49e399b4fe0e
                   size: 183GiB
                   capacity: 183GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-07-10 11:23:06 filesystem=ext3 modified=2009-07-29 12:09:20 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-07-29 19:55:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sda2
                   size: 2886MiB
                   capacity: 2886MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2886MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:8
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 6400AAV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.65
             serial: WD-WCAUF0562899
             size: 596GiB (640GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=44fdfe06
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/HDD
                version: 3.1
                serial: 5a812a97-afe1-4d11-a420-e9f5cee683b6
                size: 596GiB
                capacity: 596GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-07-11 09:03:32 filesystem=ntfs label=HDD modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:3f:73:ec:50:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Now note under the cpu section near the top it says "width: 64-bits" does this indicate that my cpu supports 64 bit?

It is an Intel P4 Celeron 3.06 Ghz and if it does support 64-bit i am considering going up to 64 when karmic comes out in october.

Thanks in advance.

---

### Post by kerry_s on 2009-07-29
yes, its 64 so go for it.

---

### Post by j7%&lt;RmUg on 2009-07-29
Thanks, i thought it might be but its good to be sure. Now im desparate for some karmic!

---

### Post by sanderj on 2009-07-29
> **kerry_s said:**
> yes, its 64 so go for it.

Are you sure? My check for 64-bitness is to look for " lm " (note the spaces) in the /proc/cpuinfo . The CPU capabilities posted ```

          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
```

do not contain " lm " (note the spaces). I must say I don't know the meaning of lahf_lm nor the 64-bit-width.

So, looking at the other specs: Celeron 3066 Mhz 256 kB cache. On [http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors) I found 3 processors with those specs.:


```

Celeron D

"Prescott-256" (90 nm)


    * Intel 64: supported by 3x1, 3x6, 355
    * XD bit (an NX bit implementation): supported by 3x0J, 3x5J, and all Intel64-compatible models
    * Steppings: C0, D0, E0, G0 & G1

Model Number 	Frequency 	L2-Cache 	Front Side Bus 	Mult 	Voltage 	TDP 	Socket 	Release Date 	Part Number(s)

Celeron D 345 	3066 MHz 	256 KiB 	533 MT/s 	23x 	1.25/1.4 V 	73 W 	Socket 478 	November 2004 	RK80546RE083256
Celeron D 345J 	3066 MHz 	256 KiB 	533 MT/s 	23x 	1.25/1.4 V 	84 W 	LGA775 	October 2004 	JM80547RE083256
Celeron D 346 	3066 MHz 	256 KiB 	533 MT/s 	23x 	1.25/1.4 V 	84 W 	LGA775 	October 2004 	JM80547RE083CN


```

So of these 3, only the "Celeron D 346" is 64-bit.


So I hope the OP downloads 9.04 64-bit (why wait for 9.10?), live-boots it, and tells us whether it works.

---

### Post by kerry_s on 2009-07-29
> Are you sure?


look at the capabilities you'll see x86-64

```
capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8
 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht
 tm pbe nx **x86-64** constant_tsc up pebs bts pni dtes64 monitor ds_cpl
 tm2 cid cx16 xtpr lahf_lm
```

---

### Post by sanderj on 2009-07-29
> **kerry_s said:**
> look at the capabilities you'll see x86-64

```
capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **x86-64** constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
```

OK, I see. THanks!

---

### Post by rannable on 2009-07-29
Once you go 64bit you will never go back :)

---

### Post by niw_uk1964 on 2009-07-29
> **rannable said:**
> Once you go 64bit you will never go back :)

Aye. Having access to 8GB of RAM here alters the way I do things. I run quite a few vm's, Windows stuff I can't do without runs within them and all the while I stay within the stable confines of Linux :-)

---

### Post by Jimmyfj on 2009-07-29
From search results on intel.com for the Intel(R) Celeron(R) CPU 3.06GHz - Here goes:

CPU 345 D:
Processor
Essentials
Status	Launched
Processor Number	345
# of Cores	1
Clock Speed	3.06 GHz
L2 Cache	256 KB
FSB Speed	533 MHz
FSB Parity	No
Instruction Set	32-bit
Embedded	No
Supplemental SKU	No
Lithography	90 nm
Max TDP	73 W
VID Voltage Range	1.25-1.4V

346 D
Processor
Essentials
Status	Launched
Processor Number	346
# of Cores	1
Clock Speed	3.06 GHz
L2 Cache	256 KB
FSB Speed	533 MHz
FSB Parity	No
Instruction Set	64-bit
Embedded	No
Supplemental SKU	No
Lithography	90 nm
Max TDP	84 W
VI

347 D


Processor
Essentials
Status	Launched
Processor Number	347
# of Cores	1
Clock Speed	3.06 GHz
L2 Cache	512 KB
FSB Speed	533 MHz
FSB Parity	No
Instruction Set	64-bit
Embedded	No
Supplemental SKU	No
Lithography	65 nm
Max TDP	86 W
VI

Actually two of the Celeron D processors are 64 bit

---

### Post by j7%&lt;RmUg on 2009-07-30
Thanks for all the input, i think mine is a 346 D since i searched the intel website for my motherboard and it came up with an LGA775 socket, also would it damage my rig if it just happened not to be 64-bit? even though it says it is.

Good idea, ill probably live-cd it first.

I cant be bothered setting up jaunty AGAIN since i currently have a really nice desktop.

---

