---
title: "Problems that arrived after the second 8.04 update"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by phlembob on 2008-05-09
HDDs - one SATA and one IDE, The IDE doesn't mount and shows up as SCSI on Places/Computer.  Picking on its icon it now states "Unable to mount."  Before the last update I used the IDE for storage only and it has NTFS formate under Windows XP Pro x64.  I have read and responded to another person before this happen to me with a similar problem when my gear worked fine.

DVDs do not play with Totem so I downloaded Kaffine and it will see DVDs but soon errors once started to read them.

I'd appreciate any feedbacks to find solutions.  Thanks

---

### Post by Yellow Pasque on 2008-05-09
Please post output of these commands:
```
sudo fdisk -l
sudo lshw -C disk
cat /etc/fstab
```

For DVD's, I recommend and use VLC. Also, make sure to get the necessary decryption libs. (sudo apt-get install ubuntu-restricted-extras).

---

### Post by wootah on 2008-05-09
For the DVD issue, have you tried the following:

sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

Try it in Totem to see if things work alright, then try Kaffine.

**Note**: This does install support of decryption of CSS (Content Scrambling System) for DVDs which **may or may not be legal** in your country. Make sure to check before continuing!

[EDIT] As Temüjin mentioned, VLC is an excellent program for many types of media. Also, don't forget to enable the restricted repositories. You can do so in Synaptic Package Manager.

---

### Post by Kernel_Krunch on 2008-05-09
sudo fdisk -l
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e7b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            1276        1403     1028160   82  Linux swap / Solaris
/dev/sda3            1404       11574    81698557+  83  Linux
/dev/sda4           11575       24321   102390277+   5  Extended
/dev/sda5           11575       14124    20482843+  83  Linux
/dev/sda6           14125       16673    20474811   83  Linux
/dev/sda7           16674       20498    30724281   83  Linux
/dev/sda8           20499       24321    30708216   83  Linux

Disk /dev/sdb: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cd8fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+  82  Linux swap / Solaris

Disk /dev/sdc: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000171cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3816      976880   82  Linux swap / Solaris

Disk /dev/sdd: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00015a24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          62      497983+  82  Linux swap / Solaris

Disk /dev/sde: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075352

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          62      497983+  82  Linux swap / Solaris

```
sudo lshw -C disk
```

  *-disk                  
       description: ATA Disk
       product: WDC WD2000JB-00R
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 20.0
       serial: WD-WCANK7901072
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007e7b0
  *-cdrom
       description: DVD writer
       product: DVD Writer 630c
       vendor: HP
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CH16
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: Cruzer Titanium
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       version: 0.5
       size: 488MiB (512MB)
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdb
          size: 488MiB (512MB)
          capabilities: partitioned partitioned:dos
          configuration: signature=000cd8fb
  *-disk
       description: SCSI Disk
       product: DataTraveler 2.0
       vendor: Kingston
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: PMAP
       size: 954MiB (1GB)
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
          size: 954MiB (1GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=000171cd
  *-disk
       description: SCSI Disk
       product: Cruzer Titanium
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdd
       version: 0.5
       size: 488MiB (512MB)
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdd
          size: 488MiB (512MB)
          capabilities: partitioned partitioned:dos
          configuration: signature=00015a24
  *-disk
       description: SCSI Disk
       product: Cruzer Titanium
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sde
       version: 0.5
       size: 488MiB (512MB)
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sde
          size: 488MiB (512MB)
          capabilities: partitioned partitioned:dos
          configuration: signature=00075352


```
dmesg
```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=572ee1a2-e36a-41fe-96d5-e75158fd6746 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffb0000 - 000000001ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 130992) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FA7C0 checksum 0
[    0.000000] ACPI: RSDP 000FA7C0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FFB0000, 0030 (r1 A M I  OEMRSDT  11000514 MSFT       97)
[    0.000000] ACPI: FACP 1FFB0200, 0081 (r1 A M I  OEMFACP  11000514 MSFT       97)
[    0.000000] ACPI: DSDT 1FFB03F0, 3A3E (r1  A0036 A0036001        1 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFC0000, 0040
[    0.000000] ACPI: APIC 1FFB0390, 0052 (r1 A M I  OEMAPIC  11000514 MSFT       97)
[    0.000000] ACPI: OEMB 1FFC0040, 003F (r1 A M I  OEMBIOS  11000514 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 130992) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   130992
[    0.000000] On node 0 totalpages: 130895
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1207 pages reserved
[    0.000000]   DMA zone: 2736 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1734 pages used for memmap
[    0.000000]   DMA32 zone: 125162 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:df780000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 127898
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=572ee1a2-e36a-41fe-96d5-e75158fd6746 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   36.918770] time.c: Detected 2403.064 MHz processor.
[   36.920114] Console: colour VGA+ 80x25
[   36.920117] console [tty0] enabled
[   36.920130] Checking aperture...
[   36.920132] CPU 0: aperture @ d0000000 size 256 MB
[   36.925150] Memory: 503928k/523968k available (2466k kernel code, 19652k reserved, 1309k data, 316k init)
[   36.925184] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   37.004741] Calibrating delay using timer specific routine.. 4811.70 BogoMIPS (lpj=9623417)
[   37.004771] Security Framework initialized
[   37.004779] SELinux:  Disabled at boot.
[   37.004792] AppArmor: AppArmor initialized
[   37.004796] Failure registering capabilities with primary security module.
[   37.004843] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   37.005187] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   37.005356] Mount-cache hash table entries: 256
[   37.005487] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   37.005489] CPU: L2 Cache: 512K (64 bytes/line)
[   37.005491] CPU 0/0 -> Node 0
[   37.005513] SMP alternatives: switching to UP code
[   37.006106] Early unpacking initramfs... done
[   37.266271] ACPI: Core revision 20070126
[   37.266313] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   37.308815] Using local APIC timer interrupts.
[   37.350420] APIC timer calibration result 12515950
[   37.350422] Detected 12.515 MHz APIC timer.
[   37.350471] Brought up 1 CPUs
[   37.350695] CPU0 attaching sched-domain:
[   37.350697]  domain 0: span 01
[   37.350699]   groups: 01
[   37.350832] net_namespace: 120 bytes
[   37.351197] Time:  0:55:27  Date: 05/10/08
[   37.351224] NET: Registered protocol family 16
[   37.351373] ACPI: bus type pci registered
[   37.351433] PCI: Using configuration type 1
[   37.353130] ACPI: EC: Look up EC in DSDT
[   37.356260] ACPI: Interpreter enabled
[   37.356263] ACPI: (supports S0 S1 S3 S4 S5)
[   37.356277] ACPI: Using IOAPIC for interrupt routing
[   37.361557] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   37.362203] PCI: enabled onboard AC97/MC97 devices
[   37.362404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   37.368927] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   37.369004] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   37.369079] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   37.369154] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.369228] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.369304] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.369379] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.369454] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.369537] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  08, should be 05 [20070126]
[   37.369541] Linux Plug and Play Support v0.97 (c) Adam Belay
[   37.369563] pnp: PnP ACPI init
[   37.369570] ACPI: bus type pnp registered
[   37.372351] pnp: PnP ACPI: found 13 devices
[   37.372353] ACPI: ACPI bus type pnp unregistered
[   37.372535] PCI: Using ACPI for IRQ routing
[   37.372537] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   37.372545] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   37.382451] NET: Registered protocol family 8
[   37.382452] NET: Registered protocol family 20
[   37.382504] agpgart: Detected AGP bridge 0
[   37.392213] agpgart: AGP aperture is 256M @ 0xd0000000
[   37.392270] AppArmor: AppArmor Filesystem Enabled
[   37.394426] Time: tsc clocksource has been installed.
[   37.406455] system 00:07: ioport range 0x680-0x6ff has been reserved
[   37.406457] system 00:07: ioport range 0x290-0x297 has been reserved
[   37.406462] system 00:08: ioport range 0x3e1-0x3e7 has been reserved
[   37.406464] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   37.406466] system 00:08: ioport range 0x800-0x87f has been reserved
[   37.406468] system 00:08: ioport range 0x400-0x41f has been reserved
[   37.406474] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   37.406476] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   37.406478] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   37.406484] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   37.406486] system 00:0c: iomem range 0xc0000-0xdffff has been reserved
[   37.406488] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   37.406491] system 00:0c: iomem range 0x100000-0x1ffeffff could not be reserved
[   37.406493] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   37.406784] PCI: Bridge: 0000:00:01.0
[   37.406786]   IO window: disabled.
[   37.406789]   MEM window: faf00000-fbffffff
[   37.406791]   PREFETCH window: e0000000-f9ffffff
[   37.406808] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   37.406837] NET: Registered protocol family 2
[   37.442467] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   37.442637] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[   37.442770] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[   37.442906] TCP: Hash tables configured (established 16384 bind 16384)
[   37.442908] TCP reno registered
[   37.454538] checking if image is initramfs... it is
[   37.910279] Switched to high resolution mode on CPU 0
[   37.962518] Freeing initrd memory: 7509k freed
[   37.967709] audit: initializing netlink socket (disabled)
[   37.967720] audit(1210380927.016:1): initialized
[   37.969184] VFS: Disk quotas dquot_6.5.1
[   37.969243] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   37.969351] io scheduler noop registered
[   37.969353] io scheduler anticipatory registered
[   37.969355] io scheduler deadline registered
[   37.969435] io scheduler cfq registered (default)
[   37.969446] PCI: VIA PCI bridge detected. Disabling DAC.
[   45.963479] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   45.963679] Boot video device is 0000:01:00.0
[   45.984264] Real Time Clock Driver v1.12ac
[   45.984331] Linux agpgart interface v0.102
[   45.984333] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.984431] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.984528] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.984926] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.985130] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.985647] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.985695] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   45.985765] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   45.986124] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.986127] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.987853] mice: PS/2 mouse device common for all mice
[   45.987882] cpuidle: using governor ladder
[   45.987884] cpuidle: using governor menu
[   45.988008] NET: Registered protocol family 1
[   45.988057] registered taskstats version 1
[   45.988166]   Magic number: 
[   45.988228]   hash matches device ptyz6
[   45.988284] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   45.988286] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   45.988288] EDD information not available.
[   45.988294] Freeing unused kernel memory: 316k freed
[   46.006532] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   47.141730] fuse init (API version 7.9)
[   47.157351] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   47.551033] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
[   47.551045] PCI: Disallowing DAC for device 0000:00:0a.0


[   47.631103] SCSI subsystem initialized
[   47.674639] libata version 3.00 loaded.
[   47.683204] usbcore: registered new interface driver usbfs
[   47.683223] usbcore: registered new interface driver hub
[   47.683278] sata_via 0000:00:0f.0: version 2.3
[   47.683298] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   47.683331] sata_via 0000:00:0f.0: routed to hard irq line 10
[   47.692422] usbcore: registered new device driver usb
[   47.698913] scsi0 : sata_via
[   47.714340] scsi1 : sata_via
[   47.714387] ata1: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xb800 irq 20
[   47.714390] ata2: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb808 irq 20
[   47.718940] USB Universal Host Controller Interface driver v3.0
[   47.914849] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   48.126774] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   48.137545] pata_via 0000:00:0f.1: version 0.3.3
[   48.137575] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   48.138436] scsi2 : pata_via
[   48.139194] scsi3 : pata_via
[   48.140325] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   48.140327] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   48.317446] ata3.00: ATA-7: WDC WD2000JB-00REA0, 20.00K20, max UDMA/100
[   48.317451] ata3.00: 390721968 sectors, multi 16: LBA48 
[   48.323005] ata3.00: configured for UDMA/100
[   48.799094] ata4.00: ATAPI: HP  DVD Writer 630, CH16, max UDMA/33
[   48.970898] ata4.00: configured for UDMA/33
[   48.971006] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JB-00R 20.0 PQ: 0 ANSI: 5
[   48.973340] scsi 3:0:0:0: CD-ROM            HP       DVD Writer 630c  CH16 PQ: 0 ANSI: 5
[   48.975195] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   48.975207] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   48.975384] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   48.975414] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[   48.975517] usb usb1: configuration #1 chosen from 1 choice
[   48.975537] hub 1-0:1.0: USB hub found
[   48.975542] hub 1-0:1.0: 2 ports detected
[   49.078513] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   49.078525] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   49.078543] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   49.078563] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[   49.078649] usb usb2: configuration #1 chosen from 1 choice
[   49.078668] hub 2-0:1.0: USB hub found
[   49.078672] hub 2-0:1.0: 2 ports detected
[   49.182473] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   49.182485] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   49.182504] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   49.182525] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[   49.182608] usb usb3: configuration #1 chosen from 1 choice
[   49.182625] hub 3-0:1.0: USB hub found
[   49.182630] hub 3-0:1.0: 2 ports detected
[   49.286435] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   49.286447] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   49.286466] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   49.286487] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
[   49.286580] usb usb4: configuration #1 chosen from 1 choice
[   49.286597] hub 4-0:1.0: USB hub found
[   49.286601] hub 4-0:1.0: 2 ports detected
[   49.318326] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   49.390697] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   49.390807] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   49.390865] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   49.390899] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfae00000
[   49.446280] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   49.446376] usb usb5: configuration #1 chosen from 1 choice
[   49.446395] hub 5-0:1.0: USB hub found
[   49.446401] hub 5-0:1.0: 8 ports detected
[   49.560571] Driver 'sd' needs updating - please use bus_type methods
[   49.560649] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   49.560659] sd 2:0:0:0: [sda] Write Protect is off
[   49.560661] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   49.560672] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.560706] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   49.560712] sd 2:0:0:0: [sda] Write Protect is off
[   49.560713] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   49.560723] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.560726]  sda: sda1 sda2 sda3 sda4 <<4>Driver 'sr' needs updating - please use bus_type methods
[   49.583308]  sda5 sda6 sda7 sda8 >
[   49.633251] sd 2:0:0:0: [sda] Attached SCSI disk
[   49.638042] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   49.638058] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   49.649166] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   49.649171] Uniform CD-ROM driver Revision: 3.20
[   49.649216] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   49.846141] usb 1-1: device not accepting address 2, error -71
[   51.037736] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   51.170793] usb 5-1: configuration #1 chosen from 1 choice
[   51.409605] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   51.544054] usb 5-2: configuration #1 chosen from 1 choice
[   51.781478] usb 5-3: new high speed USB device using ehci_hcd and address 4
[   51.914433] usb 5-3: configuration #1 chosen from 1 choice
[   52.153351] usb 5-4: new high speed USB device using ehci_hcd and address 5
[   52.286315] usb 5-4: configuration #1 chosen from 1 choice
[   52.525221] usb 5-5: new high speed USB device using ehci_hcd and address 6
[   52.658204] usb 5-5: configuration #1 chosen from 1 choice
[   52.897188] usbcore: registered new interface driver libusual
[   52.902514] Initializing USB Mass Storage driver...
[   53.137012] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   53.324985] usb 3-2: configuration #1 chosen from 1 choice
[   53.342587] scsi4 : SCSI emulation for USB Mass Storage devices
[   53.348976] usb-storage: device found at 3
[   53.348980] usb-storage: waiting for device to settle before scanning
[   53.352151] scsi5 : SCSI emulation for USB Mass Storage devices
[   53.352891] usb-storage: device found at 4
[   53.352894] usb-storage: waiting for device to settle before scanning
[   53.353748] scsi6 : SCSI emulation for USB Mass Storage devices
[   53.353823] usb-storage: device found at 5
[   53.353825] usb-storage: waiting for device to settle before scanning
[   53.354595] scsi7 : SCSI emulation for USB Mass Storage devices
[   53.355185] usbcore: registered new interface driver usb-storage
[   53.355190] USB Mass Storage support registered.
[   53.355276] usb-storage: device found at 6
[   53.355277] usb-storage: waiting for device to settle before scanning
[   55.196604] kjournald starting.  Commit interval 5 seconds
[   55.196617] EXT3-fs: mounted filesystem with ordered data mode.
[   58.347337] usb-storage: device scan complete
[   58.347434] usb-storage: device scan complete
[   58.347812] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Titanium  0.5  PQ: 0 ANSI: 2
[   58.348027] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[   58.348797] sd 5:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[   58.349423] sd 5:0:0:0: [sdb] Write Protect is off
[   58.349425] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   58.349427] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   58.351307] usb-storage: device scan complete
[   58.351343] usb-storage: device scan complete
[   58.351674] sd 5:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[   58.351691] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer Titanium  0.5  PQ: 0 ANSI: 2
[   58.351859] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Titanium  0.5  PQ: 0 ANSI: 2
[   58.352171] sd 5:0:0:0: [sdb] Write Protect is off
[   58.352173] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   58.352175] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   58.352228]  sdb: sdb1
[   58.353834] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   58.353856] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   58.354794] sd 4:0:0:0: [sdc] 1953792 512-byte hardware sectors (1000 MB)
[   58.355419] sd 4:0:0:0: [sdc] Write Protect is off
[   58.355422] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   58.355423] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   58.358043] sd 4:0:0:0: [sdc] 1953792 512-byte hardware sectors (1000 MB)
[   58.358669] sd 4:0:0:0: [sdc] Write Protect is off
[   58.358671] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   58.358672] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   58.358725]  sdc: sdc1
[   58.361319] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   58.361338] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   58.362291] sd 7:0:0:0: [sdd] 1000944 512-byte hardware sectors (512 MB)
[   58.362917] sd 7:0:0:0: [sdd] Write Protect is off
[   58.362919] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[   58.362920] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[   58.365291] sd 7:0:0:0: [sdd] 1000944 512-byte hardware sectors (512 MB)
[   58.365916] sd 7:0:0:0: [sdd] Write Protect is off
[   58.365918] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[   58.365920] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[   58.365972]  sdd: sdd1
[   58.367569] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[   58.367587] sd 7:0:0:0: Attached scsi generic sg4 type 0
[   58.368540] sd 6:0:0:0: [sde] 1000944 512-byte hardware sectors (512 MB)
[   58.369164] sd 6:0:0:0: [sde] Write Protect is off
[   58.369166] sd 6:0:0:0: [sde] Mode Sense: 03 00 00 00
[   58.369168] sd 6:0:0:0: [sde] Assuming drive cache: write through
[   58.371914] sd 6:0:0:0: [sde] 1000944 512-byte hardware sectors (512 MB)
[   58.372540] sd 6:0:0:0: [sde] Write Protect is off
[   58.372541] sd 6:0:0:0: [sde] Mode Sense: 03 00 00 00
[   58.372543] sd 6:0:0:0: [sde] Assuming drive cache: write through
[   58.372595]  sde: sde1
[   58.373942] sd 6:0:0:0: [sde] Attached SCSI removable disk
[   58.373963] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   61.734092] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   61.778168] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   61.806173] input: Power Button (FF) as /devices/virtual/input/input2
[   61.822028] ACPI: Power Button (FF) [PWRF]
[   61.822146] input: Power Button (CM) as /devices/virtual/input/input3
[   61.842017] ACPI: Power Button (CM) [PWRB]
[   61.842122] input: Sleep Button (CM) as /devices/virtual/input/input4
[   61.854003] ACPI: Sleep Button (CM) [SLPB]
[   62.900550] nvidia: module license 'NVIDIA' taints kernel.
[   63.575884] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   63.761283] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   63.761294] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   64.224615] Linux video capture interface: v2.00
[   64.349169] usbcore: registered new interface driver snd-usb-audio
[   64.390990] input: PS2++ Logitech MX Mouse as /devices/platform/i8042/serio1/input/input6
[   64.391057] /build/buildd/linux-2.6.24/drivers/media/video/usbvideo/quickcam_messenger.c: Logitech Quickcam Messenger USB v0.01
[   64.433169] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4117
[   64.444906] videodev: "QCM USB Camera" has no release callback. Please fix your driver for proper sysfs support, see http://lwn.net/Articles/36850/
[   64.444911] /build/buildd/linux-2.6.24/drivers/media/video/usbvideo/usbvideo.c: QCM on /dev/video0: canvas=320x240 videosize=320x240
[   64.444953] input: QCM button as /devices/pci0000:00/0000:00:10.2/usb3/3-2/input/input7
[   64.444974] usbcore: registered new interface driver QCM
[   64.445100] usbcore: registered new interface driver usblp
[   64.513100] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   65.017159] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   65.017175] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   65.017334] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   65.017468] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   65.533498] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   65.533705] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   66.989005] loop: module loaded
[   67.037605] lp: driver loaded but no devices found
[   67.226326] Adding 497972k swap on /dev/sde1.  Priority:-1 extents:1 across:497972k
[   67.240865] Adding 497972k swap on /dev/sdb1.  Priority:-2 extents:1 across:497972k
[   67.255486] Adding 497972k swap on /dev/sdd1.  Priority:-3 extents:1 across:497972k
[   67.575784] EXT3 FS on sda1, internal journal
[   68.194346] ip_tables: (C) 2000-2006 Netfilter Core Team

```
edit: udevadm info --attribute-walk --name /dev/sda
```

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sda':
    KERNEL=="sda"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{dev}=="8:0"
    ATTR{range}=="16"
    ATTR{removable}=="0"
    ATTR{size}=="390721968"
    ATTR{stat}=="   41156    12141  1083612   211508    23382    77472   807560   785256        0   362184   996748"
    ATTR{capability}=="12"

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host2/target2:0:0/2:0:0:0':
    KERNELS=="2:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    ATTRS{model}=="WDC WD2000JB-00R"
    ATTRS{rev}=="20.0"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0xfc2e"
    ATTRS{iodone_cnt}=="0xfc2e"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host2/target2:0:0':
    KERNELS=="target2:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host2':
    KERNELS=="host2"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.1':
    KERNELS=="0000:00:0f.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="pata_via"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x0571"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x80ed"
    ATTRS{class}=="0x01018a"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="01"
    ATTRS{modalias}=="pci:v00001106d00000571sv00001043sd000080EDbc01sc01i8a"
    ATTRS{numa_node}=="-1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```
anything else?

---

### Post by phlembob on 2008-05-10
Thanks people for the responses.  New Ubuntu update arrived yesterday and after that update the DVDs now play.

I will take your IDE drive inputs and make the check and fix...hopefully.:lolflag:

---

### Post by phlembob on 2008-05-10
> **Temüjin said:**
> Please post output of these commands:
```
sudo fdisk -l
sudo lshw -C disk
cat /etc/fstab
```

For DVD's, I recommend and use VLC. Also, make sure to get the necessary decryption libs. (sudo apt-get install ubuntu-restricted-extras).
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ca98844

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2109    16940511    7  HPFS/NTFS
/dev/sda2            2110       19457   139347810    5  Extended
/dev/sda5            2110       18747   133644703+  83  Linux
/dev/sda6           18748       19457     5703043+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6edc6ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14945   120045681    7  HPFS/NTFS

Disk /dev/sdc: 2040 MB, 2040528896 bytes
64 heads, 63 sectors/track, 988 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x6254e2d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         988     1991776+   b  W95 FAT32

---

### Post by Kernel_Krunch on 2008-05-14
What make and model is your hard drive and motherboard?

---

