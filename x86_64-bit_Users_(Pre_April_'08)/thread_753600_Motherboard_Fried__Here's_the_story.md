---
title: "Motherboard Fried  Here's the story"
date: 2008-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dive4Life on 2008-04-12
Somehow I managed to fry my previous motherboard.  I went ahead and replaced everything and virtually have a new machine.  Ubuntu was on the previous HD and booted with no issues.  Unfortunately, the DVD drives won't mount.  To say the least this is annoying. 

Mount  

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=94efe7bb-db9b-4da0-8c72-2720c3385427 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=2e7c69d7-4509-4567-ba0a-705637129d7c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


Overall INFO
dabomb                    
    description: Desktop Computer
    product: A780GM-A
    vendor: ECS
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: A780GM-A
       vendor: ECS
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014 (01/21/2008)
          size: 64KB
          capacity: 960KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
 *-cpu
          description: CPU
          product: AMD Phenom(tm) 9500 Quad-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) 9500 Quad-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy altmovcr8 abm sse4a misalignsse 3dnowprefetch osvw
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MB
             capacity: 2MB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 2MB
             capacity: 2MB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM SDRAM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM Synchronous 400 MHz (2.5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM Synchronous 400 MHz (2.5 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: b0
                serial: 00:1e:90:8a:3c:d2
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 duplex=full firmware=N/A ip=10.0.1.200 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
        *-storage
             description: SATA controller
             product: SB700 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk:0
                description: SCSI Disk
                product: WDC WD2500JS-60M
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WMANK1265249
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 230GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2941MB
                   capacity: 2941MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2941MB
                      capabilities: nofs
           *-disk:1
                description: SCSI Disk
                product: ST3300831AS
                vendor: ATA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 3.03
                serial: 3NF0Q3J3
                size: 279GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 279GB
                   capabilities: primary bootable
        *-usb:0
             description: USB Controller
             product: SB700 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB700 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB700 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB700 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:03:05.0
                logical name: wlan0
                version: 20
                serial: 00:14:d1:49:04:ba
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g
        *-usb:6
             description: USB Controller
             product: SB700 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
     *-pci:1
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

I would appreciate any and all help.  TY

---

### Post by Epic Plecostomus on 2008-04-12
Ok, just to be 100% sure... did you hook them up right?   

...I spent two hours troubleshooting only to find out I didn't plug in my CDROM.  ;)

---

### Post by felker2 on 2008-04-13
Do you see the DVD drives in your BIOS when booting?
If not, it's a hardware/BIOS thing, not a Linux thing.

If yes, can you put in a Ubuntu Live CD and boot from the DVD drive?

---

### Post by Dive4Life on 2008-04-13
They are both hooked up properly and detected in both BIOS and in Linux.  I have the two drives sitting on my desktop.  Its just that Ubuntu says that it is unable to mount.  It also sees them as just CD-ROM drives and not as DVD Writer and DVD ROM.  Yes, it is possible for me to boot to the live CD.  This seems to be the OS doesn't know what to do with the drives.  The only thing I remember changing when I replaced the MOBO was taking them off of Cable Select and making a Master/Slave Combo.

---

