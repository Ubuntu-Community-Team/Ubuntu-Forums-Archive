---
title: "Need help with the error messages i am getting...."
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by amyfan on 2008-05-01
i do dmesg in the terminal and all this pops up..
[http://paste.ubuntu.com/9328/](http://paste.ubuntu.com/9328/)
i posted in #ubuntu in irc and Stefg said my cd/dvd drive is not working or if it is the optical lense is not working.
but the funny thing is i can play dvd's just fine with no probs and i can also play cd's just fine as well as burn music to cd's, or movies as data.
to dvd's.
also not sure if it has anything to do with the usb ports but they do not work. also for some reason when i try to run a dvd in wine it does not work.
also when i do this in the terminal espeak hello\ david!
i get these errors...
[http://paste.ubuntu.com/9329/](http://paste.ubuntu.com/9329/)

---

### Post by amyfan on 2008-05-01
sorry i forgot to say i was using hardy btw. 64bit

---

### Post by Yellow Pasque on 2008-05-01
The dmesg output appears to be caused by VLC not being able to read parts of an encrypted DVD.

What is espeak?
Also, can you run some commands so we know what sound hardware you have?

```
cd /dev
ls -la | grep dsp
aplay -l
sudo lshw -C multimedia
```

---

### Post by amyfan on 2008-05-02
here is the outlook of those commands in order 
[http://paste.ubuntu.com/9478/](http://paste.ubuntu.com/9478/)
espeak is you type it in term and type what u want ur comp will say it back to you but mine wont work.

---

### Post by Yellow Pasque on 2008-05-02
Try the espeak command with sudo prefixed to it:
```
sudo espeak hello\ david!
```

As for your usb ports, try this command to see if they're recognized and have drivers loaded:
```
sudo lshw
```

---

### Post by amyfan on 2008-05-02
here is sudoed 
[http://paste.ubuntu.com/9530/](http://paste.ubuntu.com/9530/)
as for the other out put here you go
[http://paste.ubuntu.com/9531/](http://paste.ubuntu.com/9531/)

---

### Post by soxs on 2008-05-02
Post the output in [CODE]-tags.. it's nasty having to click 100 links just to get some info what isworng with your box -.-

---

### Post by amyfan on 2008-05-02
sorry new to the post thing im on my cousins account . i will do that from now on.

---

### Post by amyfan on 2008-05-02
```
:~$ sudo espeak hello\ david!
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

```

```
:~$ sudo lshw
doug                      
    description: Desktop Computer
    product: GC660AA-ABA SR5123WM
    vendor: Compaq-Presario
    serial: CNX7190ZBH
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0 uuid=804FA056-976C-1210-9AAA-991CE35738C8
  *-core
       description: Motherboard
       product: Nettle2
       vendor: ECS
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.07 (04/04/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          slot: Socket M2
          size: 2100MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache:0
          description: L1 cache
          physical id: 6
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: f
          slot: External Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A2
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A4
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A6
             size: 1GiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
        *-network
             description: Ethernet interface
             product: VT6105 [Rhine-III]
             vendor: VIA Technologies, Inc.
             physical id: 6
             bus info: pci@0000:01:06.0
             logical name: eth1
             version: 86
             serial: 00:1c:f0:15:ec:dc
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.64 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1b:b9:53:ef:95
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: WDC WD3200AAJS-6
             vendor: Western Digital
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 12.0
             serial: WD-WMAPZ0471755
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=1549f232
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                logical name: /home/doug/Desktop/stuff
                version: 1.0
                serial: d2ee46b6-d10a-4e30-8dd2-825889f5fafe
                size: 49GiB
                capacity: 49GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-04-22 23:46:55 filesystem=ext3 modified=2008-04-28 22:15:30 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-04-28 22:15:30 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                size: 10GiB
                capacity: 10GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5530MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 5530MiB
                   capabilities: nofs
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@3:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: 7bfe331e-c804-451a-a840-d63971790fbc
                size: 237GiB
                capacity: 237GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-04-22 16:04:55 filesystem=ext3 modified=2008-04-28 22:15:29 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-04-28 22:15:29 state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW TS-H653L
             vendor: TSSTcorp
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0514
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: GeForce 6100 nForce 430
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 10
          bus info: usb@2:9
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB SD Reader
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB CF Reader
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 1.01
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB SM Reader
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             version: 1.02
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB MS Reader
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
             version: 1.03
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde

```


also please anyone else do not bother with it as for now i give up. on the usb ports the sound works fine but not in terminal but eh i dont rly care for that thank you so much Temüjin for your help....

---

### Post by kantor on 2008-09-28
Maybe do you have a music player running?
If you have a player running the /dev/dsp is busy and espeak cannot run ^^

---

