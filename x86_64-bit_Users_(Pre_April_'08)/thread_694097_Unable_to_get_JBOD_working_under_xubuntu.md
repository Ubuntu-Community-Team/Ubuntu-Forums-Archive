---
title: "Unable to get JBOD working under xubuntu"
date: 2008-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by porphiron on 2008-02-11
lo folks,

am having great difficulty in getting a JBOD array working under linux, its setup and working properly under xp, but am having no luck in getting it working under xubuntu

I have used 2 160gb SATA drives and set up as a logical partiton (i read in a previous post this had worked for someone else!)

the mobo is an ASUS k8u-x with raid/jbod onboard, so its a fakeraid board, on booting i all i get is this with dmesg | tail:

[  391.608759] sda: rw=0, want=312584773, limit=312581808
[  391.608976] attempt to access beyond end of device
[  391.608978] sda: rw=0, want=312584774, limit=312581808
[  391.609197] attempt to access beyond end of device
[  391.609200] sda: rw=0, want=312584775, limit=312581808
[  391.609416] attempt to access beyond end of device
[  391.609419] sda: rw=0, want=312584776, limit=312581808

I have had a look at the modules and found that sata_sil wasnt being loaded so added it,

now lsmod | grep sata gets me

sata_uli                9860  1 
sata_sil               14472  0 
libata                138928  3 sata_uli,ata_generic,sata_sil

so the module(s) are now up and running but still no joy,

I've also tried

 mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda5 /dev/sdb

and
 
mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda /dev/sdb

which gets me

mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: create aborted

anyone any ideas??

there is an icon for the partition on the desktop but this results in

"unable to mount "games":
failed to determine the mount point for /dev/hda5

and

ntfs_att_pread failed: input/output error failed and then a load of stuff about checking it via windows....and its a new formatted drive

any help in this would reeeeeely be appreciated as Ive now been at this for a couple of weeks now!

ta!

Porph!

---

### Post by porphiron on 2008-02-11
sorry forgot to mention am using the x64 vers of xubuntu!!

---

### Post by Yellow Pasque on 2008-02-11
I'm not an expert on RAID, but if you could run some commands for us, it might help others.
```
sudo fdisk -l
sudo lshw -businfo -C disk
```

---

### Post by porphiron on 2008-02-12
Many thanks for the reply Temüjin!

right....

sudo fdisk -l gives me:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x663c56db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       38914   312568672+   f  W95 Ext'd (LBA)
/dev/sda5               2       38914   312568641    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a5c0563

sda and sdb are the two sata drives in question, tho looking at this surely if I'm using JBOD the second disk wont contain the partition table as that will be on the bootblock of the first drive?? or should it be on both??


anyways, sudo lshw -businfo -C disk gives me:

Bus info          Device      Class       Description
=====================================================
ide@0.0           /dev/hda    disk        115GB IC35L120AVV207-0
ide@0.1           /dev/hdb    disk        LITE-ON DVDRW SOHW-1693S
                  /dev/hdb    disk        
ide@1.0           /dev/hdc    disk        _NEC DVD_RW ND-3520AW
ide@1.1           /dev/hdd    disk        DVDRW DRW-6S160P
scsi@1:0.0.0      /dev/sda    disk        149GB SAMSUNG HD160JJ
scsi@2:0.0.0      /dev/sdb    disk        149GB SAMSUNG HD160JJ
scsi@0:0.0.0      /dev/sdc    disk        298GB HDT725032VLAT80

hope this helps,

here is also the output from dmesg, sorry about the length, but didn't know if i should crop any bits out........


[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Jan 31 23:33:13 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] Command line: root=UUID=896ab41d-66b8-436e-af0e-9ed404d62a3b ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffdf000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524240) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FA7F0 checksum 0
[    0.000000] ACPI: RSDP 000FA7F0, 0021 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7FFD0100, 003C (r1 A M I  OEMXSDT   8000617 MSFT       97)
[    0.000000] ACPI: FACP 7FFD0290, 00F4 (r3 A M I  OEMFACP   8000617 MSFT       97)
[    0.000000] ACPI: DSDT 7FFD03F0, 3F45 (r1  A0158 A0158000        0 INTL  2002026)
[    0.000000] ACPI: FACS 7FFDF000, 0040
[    0.000000] ACPI: APIC 7FFD0390, 0054 (r1 A M I  OEMAPIC   8000617 MSFT       97)
[    0.000000] ACPI: OEMB 7FFDF040, 0040 (r1 A M I  AMI_OEM   8000617 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ffd0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524240) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffd0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524240
[    0.000000] On node 0 totalpages: 524143
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1126 pages reserved
[    0.000000]   DMA zone: 2817 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513033 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f780000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515850
[    0.000000] Kernel command line: root=UUID=896ab41d-66b8-436e-af0e-9ed404d62a3b ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   22.932029] time.c: Detected 2353.357 MHz processor.
[   22.933916] Console: colour VGA+ 80x25
[   22.933930] Checking aperture...
[   22.933933] CPU 0: aperture @ d0000000 size 256 MB
[   22.964426] Memory: 2055564k/2096960k available (2274k kernel code, 41008k reserved, 1181k data, 296k init)
[   22.964477] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   23.042002] Calibrating delay using timer specific routine.. 4709.40 BogoMIPS (lpj=9418806)
[   23.042040] Security Framework v1.0.0 initialized
[   23.042048] SELinux:  Disabled at boot.
[   23.042200] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.044278] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.045291] Mount-cache hash table entries: 256
[   23.045446] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.045448] CPU: L2 Cache: 1024K (64 bytes/line)
[   23.045451] CPU 0/0 -> Node 0
[   23.045470] SMP alternatives: switching to UP code
[   23.045670] Freeing SMP alternatives: 24k freed
[   23.046508] Early unpacking initramfs... done
[   23.317179] ACPI: Core revision 20070126
[   23.317227] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.359494] Using local APIC timer interrupts.
[   23.401977] result 13371346
[   23.401979] Detected 13.371 MHz APIC timer.
[   23.405950] Brought up 1 CPUs
[   23.406218] NET: Registered protocol family 16
[   23.406291] ACPI: bus type pci registered
[   23.406296] PCI: Using configuration type 1
[   23.407441] ACPI: EC: Look up EC in DSDT
[   23.410274] ACPI: Interpreter enabled
[   23.410276] ACPI: (supports S0 S1 S3 S4 S5)
[   23.410289] ACPI: Using IOAPIC for interrupt routing
[   23.415444] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.415451] PCI: Probing PCI hardware (bus 00)
[   23.415625] PCI quirk: region 0800-083f claimed by ali7101 ACPI
[   23.416159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.416231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   23.416278] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
[   23.422359] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   23.422460] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   23.422559] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   23.422658] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   23.422757] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   23.422856] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   23.422955] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   23.423055] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   23.423154] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   23.423210] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.423218] pnp: PnP ACPI init
[   23.423229] ACPI: bus type pnp registered
[   23.426095] pnp: PnP ACPI: found 12 devices
[   23.426097] ACPI: ACPI bus type pnp unregistered
[   23.426139] PCI: Using ACPI for IRQ routing
[   23.426142] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.426149] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   23.426253] NET: Registered protocol family 8
[   23.426254] NET: Registered protocol family 20
[   23.426297] agpgart: Detected AGP bridge 0
[   23.426302] Setting up ULi AGP.
[   23.437812] agpgart: AGP aperture is 256M @ 0xd0000000
[   23.437886] pnp: 00:08: ioport range 0xc00-0xc0f has been reserved
[   23.437889] pnp: 00:08: ioport range 0xd00-0xd0f has been reserved
[   23.437891] pnp: 00:08: ioport range 0xa20-0xa2f has been reserved
[   23.437897] pnp: 00:08: ioport range 0xa30-0xa3f has been reserved
[   23.437900] Time: tsc clocksource has been installed.
[   23.437930] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   23.437933] pnp: 00:09: iomem range 0xffb00000-0xffbbffff could not be reserved
[   23.437938] pnp: 00:0a: iomem range 0xffbc0000-0xffbfffff could not be reserved
[   23.437941] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   23.437944] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   23.437948] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   23.437951] pnp: 00:0b: iomem range 0xc0000-0xdffff has been reserved
[   23.437953] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   23.437956] pnp: 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
[   23.438167] PCI: Bridge: 0000:00:01.0
[   23.438170]   IO window: d000-dfff
[   23.438174]   MEM window: f9000000-fbefffff
[   23.438178]   PREFETCH window: e0000000-f7ffffff
[   23.438182] PCI: Bridge: 0000:00:02.0
[   23.438184]   IO window: e000-efff
[   23.438188]   MEM window: fbf00000-fbffffff
[   23.438191]   PREFETCH window: disabled.
[   23.438201] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.438207] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.438240] NET: Registered protocol family 2
[   23.477950] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   23.478512] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   23.484666] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   23.485713] TCP: Hash tables configured (established 262144 bind 65536)
[   23.485715] TCP reno registered
[   23.494024] checking if image is initramfs... it is
[   24.017509] Freeing initrd memory: 7668k freed
[   24.025471] audit: initializing netlink socket (disabled)
[   24.025484] audit(1202847290.052:1): initialized
[   24.026993] VFS: Disk quotas dquot_6.5.1
[   24.027036] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.027109] io scheduler noop registered
[   24.027111] io scheduler anticipatory registered
[   24.027113] io scheduler deadline registered
[   24.027182] io scheduler cfq registered (default)
[   24.113977] Boot video device is 0000:01:00.0
[   24.133102] Real Time Clock Driver v1.12ac
[   24.133182] Linux agpgart interface v0.102 (c) Dave Jones
[   24.133184] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.134035] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.134231] input: Macintosh mouse button emulation as /class/input/input0
[   24.134285] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   24.136551] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.136556] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.136687] mice: PS/2 mouse device common for all mice
[   24.136796] TCP cubic registered
[   24.136854] NET: Registered protocol family 1
[   24.137031] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.137038] Freeing unused kernel memory: 296k freed
[   24.192309] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.277684] SCSI subsystem initialized
[   25.281584] libata version 2.21 loaded.
[   25.292945] AppArmor: AppArmor initialized<5>audit(1202847291.320:2):  type=1505 info="AppArmor initialized" pid=1178
[   25.297275] fuse init (API version 7.8)
[   25.300948] Failure registering capabilities with primary security module.
[   25.320780] md: linear personality registered for level -1
[   25.323387] md: multipath personality registered for level -4
[   25.325707] md: raid0 personality registered for level 0
[   25.328402] md: raid1 personality registered for level 1
[   25.330598] raid5: automatically using best checksumming function: generic_sse
[   25.349419]    generic_sse:  7578.000 MB/sec
[   25.349421] raid5: using function: generic_sse (7578.000 MB/sec)
[   25.417422] raid6: int64x1   1934 MB/s
[   25.485387] raid6: int64x2   2948 MB/s
[   25.553375] raid6: int64x4   2968 MB/s
[   25.621351] raid6: int64x8   1987 MB/s
[   25.689352] raid6: sse2x1    2453 MB/s
[   25.757316] raid6: sse2x2    3869 MB/s
[   25.825302] raid6: sse2x4    4221 MB/s
[   25.825304] raid6: using algorithm sse2x4 (4221 MB/s)
[   25.825306] md: raid6 personality registered for level 6
[   25.825307] md: raid5 personality registered for level 5
[   25.825309] md: raid4 personality registered for level 4
[   25.838722] md: raid10 personality registered for level 10
[   26.283138] usbcore: registered new interface driver usbfs
[   26.283159] usbcore: registered new interface driver hub
[   26.283179] usbcore: registered new device driver usb
[   26.283746] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.283778] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 20 (level, low) -> IRQ 20
[   26.284107] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[   26.284250] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 1
[   26.284272] ohci_hcd 0000:00:0f.0: irq 20, io mem 0xf8ff3000
[   26.351435] usb usb1: configuration #1 chosen from 1 choice
[   26.351459] hub 1-0:1.0: USB hub found
[   26.351471] hub 1-0:1.0: 3 ports detected
[   26.457211] ACPI: PCI Interrupt 0000:00:0f.1[B] -> GSI 21 (level, low) -> IRQ 21
[   26.457509] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[   26.457572] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 2
[   26.457593] ohci_hcd 0000:00:0f.1: irq 21, io mem 0xf8ffc000
[   26.461093] FDC 0 is a post-1991 82077
[   26.519127] usb usb2: configuration #1 chosen from 1 choice
[   26.519153] hub 2-0:1.0: USB hub found
[   26.519165] hub 2-0:1.0: 3 ports detected
[   26.625054] ACPI: PCI Interrupt 0000:00:0f.2[C] -> GSI 22 (level, low) -> IRQ 22
[   26.625527] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   26.625581] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 3
[   26.625604] ohci_hcd 0000:00:0f.2: irq 22, io mem 0xf8ffd000
[   26.687271] usb usb3: configuration #1 chosen from 1 choice
[   26.687403] hub 3-0:1.0: USB hub found
[   26.687410] hub 3-0:1.0: 3 ports detected
[   26.764945] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   26.793230] ACPI: PCI Interrupt 0000:00:0f.3[D] -> GSI 23 (level, low) -> IRQ 23
[   26.793360] ehci_hcd 0000:00:0f.3: EHCI Host Controller
[   26.793417] ehci_hcd 0000:00:0f.3: new USB bus registered, assigned bus number 4
[   26.793454] ehci_hcd 0000:00:0f.3: debug port 1
[   26.820946] ehci_hcd 0000:00:0f.3: irq 23, io mem 0xf8ffe800
[   26.932903] ehci_hcd 0000:00:0f.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.932981] usb usb4: configuration #1 chosen from 1 choice
[   26.933003] hub 4-0:1.0: USB hub found
[   26.933009] hub 4-0:1.0: 8 ports detected
[   27.041208] ACPI: PCI Interrupt 0000:02:07.2[C] -> GSI 22 (level, low) -> IRQ 22
[   27.041342] ehci_hcd 0000:02:07.2: EHCI Host Controller
[   27.041675] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 5
[   27.068861] ehci_hcd 0000:02:07.2: irq 22, io mem 0xfbfffc00
[   27.068869] ehci_hcd 0000:02:07.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   27.069249] usb usb5: configuration #1 chosen from 1 choice
[   27.069425] hub 5-0:1.0: USB hub found
[   27.069430] hub 5-0:1.0: 5 ports detected
[   27.181292] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.181298] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.183056] ALI15X3: IDE controller at PCI slot 0000:00:0e.0
[   27.183078] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 19
[   27.183088] ALI15X3: chipset revision 199
[   27.183090] ALI15X3: not 100% native mode: will probe irqs later
[   27.183105]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[   27.183118]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[   27.183128] Probing IDE interface ide0...
[   27.348777] usb 1-1: device not accepting address 2, error -62
[   27.472911] hda: IC35L120AVV207-0, ATA DISK drive
[   27.900618] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   27.924779] hdb: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive
[   27.984597] hda: selected mode 0x45
[   27.984769] hdb: selected mode 0x44
[   27.985043] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.993453] Probing IDE interface ide1...
[   28.041928] usb 4-1: configuration #1 chosen from 1 choice
[   28.042143] hub 4-1:1.0: USB hub found
[   28.042494] hub 4-1:1.0: 4 ports detected
[   28.388480] usb 4-4: new high speed USB device using ehci_hcd and address 3
[   28.529813] usb 4-4: configuration #1 chosen from 1 choice
[   28.732547] hdc: _NEC DVD_RW ND-3520AW, ATAPI CD/DVD-ROM drive
[   28.752674] usb 4-1.1: new high speed USB device using ehci_hcd and address 4
[   28.857704] usb 4-1.1: configuration #1 chosen from 1 choice
[   28.857921] hub 4-1.1:1.0: USB hub found
[   28.858269] hub 4-1.1:1.0: 4 ports detected
[   28.967379] usbcore: registered new interface driver libusual
[   28.971200] Initializing USB Mass Storage driver...
[   28.971319] scsi0 : SCSI emulation for USB Mass Storage devices
[   28.971362] usb-storage: device found at 3
[   28.971363] usb-storage: waiting for device to settle before scanning
[   28.971378] usbcore: registered new interface driver usb-storage
[   28.971380] USB Mass Storage support registered.
[   29.520319] hdd: DVDRW DRW-6S160P, ATAPI CD/DVD-ROM drive
[   29.576141] hdc: selected mode 0x42
[   29.576371] hdd: selected mode 0x44
[   29.576674] ide1 at 0x170-0x177,0x376 on irq 15
[   29.590652] sata_uli 0000:00:0e.1: version 1.2
[   29.590661] ACPI: PCI Interrupt 0000:00:0e.1[A] -> GSI 19 (level, low) -> IRQ 19
[   29.590750] scsi1 : sata_uli
[   29.590906] scsi2 : sata_uli
[   29.591052] ata1: SATA max UDMA/133 cmd 0x000000000001cc00 ctl 0x000000000001c082 bmdma 0x000000000001b880 irq 19
[   29.591056] ata2: SATA max UDMA/133 cmd 0x000000000001c000 ctl 0x000000000001bc02 bmdma 0x000000000001b888 irq 19
[   29.595705] hda: max request size: 512KiB
[   29.606604] hda: 241254720 sectors (123522 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
[   29.606835] hda: cache flushes supported
[   29.606882]  hda: hda1 hda2 hda3 < hda5 hda6 hda7 hda8 hda9 hda10 hda11 hda12 >
[   29.711848] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   29.711856] Uniform CD-ROM driver Revision: 3.20
[   29.743827] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.747095] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   30.060010] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   30.068264] ata1.00: ATA-7: SAMSUNG HD160JJ, ZM100-41, max UDMA7
[   30.068266] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.112277] ata1.00: configured for UDMA/133
[   30.583853] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   30.592107] ata2.00: ATA-7: SAMSUNG HD160JJ, ZM100-41, max UDMA7
[   30.592110] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.636090] ata2.00: configured for UDMA/133
[   30.636175] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[   30.636513] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[   30.636890] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 20 (level, low) -> IRQ 20
[   30.637236] ohci_hcd 0000:02:07.0: OHCI Host Controller
[   30.637569] ohci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 6
[   30.637585] ohci_hcd 0000:02:07.0: irq 20, io mem 0xfbffd000
[   30.647405] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   30.647419] sd 1:0:0:0: [sda] Write Protect is off
[   30.647421] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.647432] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.647485] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   30.647491] sd 1:0:0:0: [sda] Write Protect is off
[   30.647493] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.647503] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.647505]  sda: sda1 < sda5 >
[   30.657552]  sda: p5 exceeds device capacity
[   30.658027] sd 1:0:0:0: [sda] Attached SCSI disk
[   30.658217] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   30.658224] sd 2:0:0:0: [sdb] Write Protect is off
[   30.658226] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.658235] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.658260] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   30.658266] sd 2:0:0:0: [sdb] Write Protect is off
[   30.658268] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.658277] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   30.658279]  sdb: unknown partition table
[   30.669051] sd 2:0:0:0: [sdb] Attached SCSI disk
[   30.672256] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   30.672273] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   31.209508] usb usb6: configuration #1 chosen from 1 choice
[   31.209542] hub 6-0:1.0: USB hub found
[   31.209552] hub 6-0:1.0: 3 ports detected
[   31.287651] attempt to access beyond end of device
[   31.287658] sda: rw=0, want=625153282, limit=312581808
[   31.287661] Buffer I/O error on device sda5, logical block 312568576
[   31.287665] attempt to access beyond end of device
[   31.287667] sda: rw=0, want=625153284, limit=312581808
[   31.287670] Buffer I/O error on device sda5, logical block 312568577
[   31.287672] attempt to access beyond end of device
[   31.287674] sda: rw=0, want=625153286, limit=312581808
[   31.287676] Buffer I/O error on device sda5, logical block 312568578
[   31.287678] attempt to access beyond end of device
[   31.287681] sda: rw=0, want=625153288, limit=312581808
[   31.287683] Buffer I/O error on device sda5, logical block 312568579
[   31.287686] attempt to access beyond end of device
[   31.287688] sda: rw=0, want=625153282, limit=312581808
[   31.287690] Buffer I/O error on device sda5, logical block 312568576
[   31.287692] attempt to access beyond end of device
[   31.287694] sda: rw=0, want=625153284, limit=312581808
[   31.287696] Buffer I/O error on device sda5, logical block 312568577
[   31.287699] attempt to access beyond end of device
[   31.287701] sda: rw=0, want=625153286, limit=312581808
[   31.287703] Buffer I/O error on device sda5, logical block 312568578
[   31.287705] attempt to access beyond end of device
[   31.287707] sda: rw=0, want=625153288, limit=312581808
[   31.287709] Buffer I/O error on device sda5, logical block 312568579
[   31.287716] attempt to access beyond end of device
[   31.287718] sda: rw=0, want=625153394, limit=312581808
[   31.287720] Buffer I/O error on device sda5, logical block 312568632
[   31.287723] attempt to access beyond end of device
[   31.287725] sda: rw=0, want=625153396, limit=312581808
[   31.287727] Buffer I/O error on device sda5, logical block 312568633
[   31.287729] attempt to access beyond end of device
[   31.287731] sda: rw=0, want=625153398, limit=312581808
[   31.287733] attempt to access beyond end of device
[   31.287735] sda: rw=0, want=625153400, limit=312581808
[   31.287738] attempt to access beyond end of device
[   31.287740] sda: rw=0, want=625153394, limit=312581808
[   31.287742] attempt to access beyond end of device
[   31.287744] sda: rw=0, want=625153396, limit=312581808
[   31.287747] attempt to access beyond end of device
[   31.287749] sda: rw=0, want=625153398, limit=312581808
[   31.287751] attempt to access beyond end of device
[   31.287753] sda: rw=0, want=625153400, limit=312581808
[   31.289019] attempt to access beyond end of device
[   31.289023] sda: rw=0, want=625153410, limit=312581808
[   31.289026] attempt to access beyond end of device
[   31.289028] sda: rw=0, want=625153410, limit=312581808
[   31.289034] attempt to access beyond end of device
[   31.289036] sda: rw=0, want=625153410, limit=312581808
[   31.289041] attempt to access beyond end of device
[   31.289043] sda: rw=0, want=625153410, limit=312581808
[   31.289047] attempt to access beyond end of device
[   31.289050] sda: rw=0, want=625153410, limit=312581808
[   31.289054] attempt to access beyond end of device
[   31.289056] sda: rw=0, want=625153410, limit=312581808
[   31.289061] attempt to access beyond end of device
[   31.289063] sda: rw=0, want=625153410, limit=312581808
[   31.289069] attempt to access beyond end of device
[   31.289071] sda: rw=0, want=625153346, limit=312581808
[   31.289073] attempt to access beyond end of device
[   31.289076] sda: rw=0, want=625153348, limit=312581808
[   31.289078] attempt to access beyond end of device
[   31.289080] sda: rw=0, want=625153350, limit=312581808
[   31.289082] attempt to access beyond end of device
[   31.289084] sda: rw=0, want=625153352, limit=312581808
[   31.289088] attempt to access beyond end of device
[   31.289091] sda: rw=0, want=625153394, limit=312581808
[   31.289093] attempt to access beyond end of device
[   31.289095] sda: rw=0, want=625153396, limit=312581808
[   31.289097] attempt to access beyond end of device
[   31.289099] sda: rw=0, want=625153398, limit=312581808
[   31.289101] attempt to access beyond end of device
[   31.289103] sda: rw=0, want=625153400, limit=312581808
[   31.289108] attempt to access beyond end of device
[   31.289110] sda: rw=0, want=625153410, limit=312581808
[   31.289115] attempt to access beyond end of device
[   31.289117] sda: rw=0, want=625153410, limit=312581808
[   31.727639] ACPI: PCI Interrupt 0000:02:07.1[B] -> GSI 21 (level, low) -> IRQ 21
[   31.727975] ohci_hcd 0000:02:07.1: OHCI Host Controller
[   31.728033] ohci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 7
[   31.728051] ohci_hcd 0000:02:07.1: irq 21, io mem 0xfbffe000
[   32.298049] usb usb7: configuration #1 chosen from 1 choice
[   32.298224] hub 7-0:1.0: USB hub found
[   32.298232] hub 7-0:1.0: 2 ports detected
[   32.918468] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   33.136323] Attempting manual resume
[   33.136327] swsusp: Resume From Partition 3:2
[   33.136328] PM: Checking swsusp image.
[   33.147013] PM: Resume from disk failed.
[   33.166657] kjournald starting.  Commit interval 5 seconds
[   33.166668] EXT3-fs: mounted filesystem with ordered data mode.
[   33.971255] usb-storage: device scan complete
[   33.971873] scsi 0:0:0:0: Direct-Access     Hitachi  HDT725032VLAT80  0811 PQ: 0 ANSI: 0
[   33.972853] sd 0:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   33.974103] sd 0:0:0:0: [sdc] Test WP failed, assume Write Enabled
[   33.974105] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[   33.974978] sd 0:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   33.976226] sd 0:0:0:0: [sdc] Test WP failed, assume Write Enabled
[   33.976228] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[   33.976231]  sdc: sdc1
[   33.986517] sd 0:0:0:0: [sdc] Attached SCSI disk
[   33.986544] sd 0:0:0:0: Attached scsi generic sg2 type 0
[   37.742315] attempt to access beyond end of device
[   37.742321] sda: rw=0, want=625153282, limit=312581808
[   37.742324] printk: 23 messages suppressed.
[   37.742327] Buffer I/O error on device sda5, logical block 312568576
[   37.742331] attempt to access beyond end of device
[   37.742333] sda: rw=0, want=625153284, limit=312581808
[   37.742336] attempt to access beyond end of device
[   37.742338] sda: rw=0, want=625153286, limit=312581808
[   37.742340] attempt to access beyond end of device
[   37.742342] sda: rw=0, want=625153288, limit=312581808
[   37.742345] attempt to access beyond end of device
[   37.742347] sda: rw=0, want=625153282, limit=312581808
[   37.742350] attempt to access beyond end of device
[   37.742352] sda: rw=0, want=625153284, limit=312581808
[   37.742354] attempt to access beyond end of device
[   37.742356] sda: rw=0, want=625153286, limit=312581808
[   37.742358] attempt to access beyond end of device
[   37.742360] sda: rw=0, want=625153288, limit=312581808
[   37.742367] attempt to access beyond end of device
[   37.742369] sda: rw=0, want=625153394, limit=312581808
[   37.742372] attempt to access beyond end of device
[   37.742374] sda: rw=0, want=625153396, limit=312581808
[   37.742376] attempt to access beyond end of device
[   37.742378] sda: rw=0, want=625153398, limit=312581808
[   37.742380] attempt to access beyond end of device
[   37.742382] sda: rw=0, want=625153400, limit=312581808
[   37.742385] attempt to access beyond end of device
[   37.742387] sda: rw=0, want=625153394, limit=312581808
[   37.742389] attempt to access beyond end of device
[   37.742391] sda: rw=0, want=625153396, limit=312581808
[   37.742394] attempt to access beyond end of device
[   37.742396] sda: rw=0, want=625153398, limit=312581808
[   37.742398] attempt to access beyond end of device
[   37.742400] sda: rw=0, want=625153400, limit=312581808
[   37.753288] attempt to access beyond end of device
[   37.753295] sda: rw=0, want=625153410, limit=312581808
[   37.753301] attempt to access beyond end of device
[   37.753303] sda: rw=0, want=625153410, limit=312581808
[   37.753311] attempt to access beyond end of device
[   37.753313] sda: rw=0, want=625153410, limit=312581808
[   37.753318] attempt to access beyond end of device
[   37.753320] sda: rw=0, want=625153410, limit=312581808
[   37.753325] attempt to access beyond end of device
[   37.753327] sda: rw=0, want=625153410, limit=312581808
[   37.753332] attempt to access beyond end of device
[   37.753334] sda: rw=0, want=625153410, limit=312581808
[   37.753339] attempt to access beyond end of device
[   37.753341] sda: rw=0, want=625153410, limit=312581808
[   37.753348] attempt to access beyond end of device
[   37.753350] sda: rw=0, want=625153346, limit=312581808
[   37.753352] attempt to access beyond end of device
[   37.753355] sda: rw=0, want=625153348, limit=312581808
[   37.753357] attempt to access beyond end of device
[   37.753359] sda: rw=0, want=625153350, limit=312581808
[   37.753361] attempt to access beyond end of device
[   37.753363] sda: rw=0, want=625153352, limit=312581808
[   37.753369] attempt to access beyond end of device
[   37.753371] sda: rw=0, want=625153394, limit=312581808
[   37.753373] attempt to access beyond end of device
[   37.753375] sda: rw=0, want=625153396, limit=312581808
[   37.753378] attempt to access beyond end of device
[   37.753380] sda: rw=0, want=625153398, limit=312581808
[   37.753382] attempt to access beyond end of device
[   37.753384] sda: rw=0, want=625153400, limit=312581808
[   37.753389] attempt to access beyond end of device
[   37.753391] sda: rw=0, want=625153410, limit=312581808
[   37.753396] attempt to access beyond end of device
[   37.753398] sda: rw=0, want=625153410, limit=312581808
[   38.925722] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.928067] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.181348] ali1535_smbus 0000:00:03.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   39.181364] ali1535_smbus 0000:00:03.1: ALI1535 not detected, module not inserted.
[   39.185071] ali15x3_smbus 0000:00:03.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   39.185075] ali15x3_smbus 0000:00:03.1: ALI15X3 not detected, module not inserted.
[   39.233373] ali1563_smbus 0000:00:03.0: Found ALi1563 SMBus at 0x0400
[   39.426129] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[   39.426188] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 17
[   39.447716] eth0: ULi M5263 at pci0000:00:0d.0, 00:17:31:79:f1:50, irq 17.
[   39.696604] input: PC Speaker as /class/input/input2
[   40.068195] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   40.068224] nvidiafb: Device ID: 10de0045 
[   40.085106] nvidiafb: CRTC0 analog found
[   40.105107] nvidiafb: CRTC1 analog not found
[   40.373034] nvidiafb: EDID found from BUS1
[   40.414946] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   40.472683] i2c-adapter i2c-2: unable to read EDID block.
[   40.628629] i2c-adapter i2c-2: unable to read EDID block.
[   40.784581] i2c-adapter i2c-2: unable to read EDID block.
[   40.840878] nvidiafb: CRTC 0 appears to have a CRT attached
[   40.840881] nvidiafb: Using CRT on CRTC 0
[   40.841415] nvidiafb: MTRR set to ON
[   40.968007] Console: switching to colour frame buffer device 128x48
[   40.968014] nvidiafb: PCI nVidia NV4 framebuffer (64MB @ 0xE0000000)
[   40.968168] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   41.072808] AC'97 0 analog subsections not ready
[   41.140792] intel8x0_measure_ac97_clock: measured 58531 usecs
[   41.140794] intel8x0: clocking to 48000
[   41.799764] loop: module loaded
[   41.859264] lp: driver loaded but no devices found
[   41.933709] Adding 1951888k swap on /dev/hda2.  Priority:-1 extents:1 across:1951888k
[   42.049292] EXT3 FS on hda6, internal journal
[   42.801707] kjournald starting.  Commit interval 5 seconds
[   42.801816] EXT3 FS on hda5, internal journal
[   42.801821] EXT3-fs: mounted filesystem with ordered data mode.
[   42.825573] kjournald starting.  Commit interval 5 seconds
[   42.825690] EXT3 FS on hda10, internal journal
[   42.825693] EXT3-fs: mounted filesystem with ordered data mode.
[   42.862522] kjournald starting.  Commit interval 5 seconds
[   42.862640] EXT3 FS on hda9, internal journal
[   42.862642] EXT3-fs: mounted filesystem with ordered data mode.
[   42.884184] kjournald starting.  Commit interval 5 seconds
[   42.884298] EXT3 FS on hda11, internal journal
[   42.884300] EXT3-fs: mounted filesystem with ordered data mode.
[   42.912845] kjournald starting.  Commit interval 5 seconds
[   42.912955] EXT3 FS on hda7, internal journal
[   42.912958] EXT3-fs: mounted filesystem with ordered data mode.
[   42.941909] kjournald starting.  Commit interval 5 seconds
[   42.942024] EXT3 FS on hda8, internal journal
[   42.942026] EXT3-fs: mounted filesystem with ordered data mode.
[   43.068555] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
[   45.390986] No dock devices found.
[   45.474288] input: Power Button (FF) as /class/input/input4
[   45.477731] ACPI: Power Button (FF) [PWRF]
[   45.499602] input: Power Button (CM) as /class/input/input5
[   45.502974] ACPI: Power Button (CM) [PWRB]
[   45.672094] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3400+ processors (version 2.00.00)
[   45.674333] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   46.919305] ppdev: user-space parallel port driver
[   47.087051] audit(1202847313.349:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4864 profile="/usr/sbin/cupsd"
[   47.250795] Failure registering capabilities with primary security module.
[   48.777423] attempt to access beyond end of device
[   48.777431] sda: rw=0, want=625153282, limit=312581808
[   48.777433] printk: 32 messages suppressed.
[   48.777436] Buffer I/O error on device sda5, logical block 312568576
[   48.777979] attempt to access beyond end of device
[   48.777982] sda: rw=0, want=625153284, limit=312581808
[   48.777984] Buffer I/O error on device sda5, logical block 312568577
[   48.778330] attempt to access beyond end of device
[   48.778333] sda: rw=0, want=625153286, limit=312581808
[   48.778611] attempt to access beyond end of device
[   48.778614] sda: rw=0, want=625153288, limit=312581808
[   48.778851] attempt to access beyond end of device
[   48.778854] sda: rw=0, want=625153282, limit=312581808
[   48.779086] attempt to access beyond end of device
[   48.779088] sda: rw=0, want=625153284, limit=312581808
[   48.779327] attempt to access beyond end of device
[   48.779329] sda: rw=0, want=625153286, limit=312581808
[   48.779564] attempt to access beyond end of device
[   48.779567] sda: rw=0, want=625153288, limit=312581808
[   48.779816] attempt to access beyond end of device
[   48.779819] sda: rw=0, want=625153394, limit=312581808
[   48.780058] attempt to access beyond end of device
[   48.780061] sda: rw=0, want=625153396, limit=312581808
[   48.780300] attempt to access beyond end of device
[   48.780303] sda: rw=0, want=625153398, limit=312581808
[   48.780541] attempt to access beyond end of device
[   48.780544] sda: rw=0, want=625153400, limit=312581808
[   48.780783] attempt to access beyond end of device
[   48.780785] sda: rw=0, want=625153394, limit=312581808
[   48.781024] attempt to access beyond end of device
[   48.781027] sda: rw=0, want=625153396, limit=312581808
[   48.781276] attempt to access beyond end of device
[   48.781279] sda: rw=0, want=625153398, limit=312581808
[   48.781517] attempt to access beyond end of device
[   48.781520] sda: rw=0, want=625153400, limit=312581808
[   48.789398] attempt to access beyond end of device
[   48.789403] sda: rw=0, want=625153410, limit=312581808
[   48.789701] attempt to access beyond end of device
[   48.789704] sda: rw=0, want=625153410, limit=312581808
[   48.789954] attempt to access beyond end of device
[   48.789957] sda: rw=0, want=625153410, limit=312581808
[   48.790206] attempt to access beyond end of device
[   48.790208] sda: rw=0, want=625153410, limit=312581808
[   48.790455] attempt to access beyond end of device
[   48.790458] sda: rw=0, want=625153410, limit=312581808
[   48.790770] attempt to access beyond end of device
[   48.790773] sda: rw=0, want=625153410, limit=312581808
[   48.791022] attempt to access beyond end of device
[   48.791025] sda: rw=0, want=625153410, limit=312581808
[   48.791364] attempt to access beyond end of device
[   48.791367] sda: rw=0, want=625153346, limit=312581808
[   48.791869] attempt to access beyond end of device
[   48.791873] sda: rw=0, want=625153348, limit=312581808
[   48.792256] attempt to access beyond end of device
[   48.792259] sda: rw=0, want=625153350, limit=312581808
[   48.792907] attempt to access beyond end of device
[   48.792910] sda: rw=0, want=625153352, limit=312581808
[   48.793382] attempt to access beyond end of device
[   48.793386] sda: rw=0, want=625153394, limit=312581808
[   48.795160] attempt to access beyond end of device
[   48.795163] sda: rw=0, want=625153396, limit=312581808
[   48.797262] attempt to access beyond end of device
[   48.797265] sda: rw=0, want=625153398, limit=312581808
[   48.797952] attempt to access beyond end of device
[   48.797955] sda: rw=0, want=625153400, limit=312581808
[   48.798239] attempt to access beyond end of device
[   48.798242] sda: rw=0, want=625153410, limit=312581808
[   48.798572] attempt to access beyond end of device
[   48.798578] sda: rw=0, want=625153410, limit=312581808
[  320.206557] attempt to access beyond end of device
[  320.206564] sda: rw=0, want=312584769, limit=312581808
[  320.206567] printk: 31 messages suppressed.
[  320.206569] Buffer I/O error on device sda5, logical block 312568640
[  320.207124] attempt to access beyond end of device
[  320.207127] sda: rw=0, want=312584770, limit=312581808
[  320.207130] Buffer I/O error on device sda5, logical block 312568641
[  320.207483] attempt to access beyond end of device
[  320.207486] sda: rw=0, want=312584771, limit=312581808
[  320.207488] Buffer I/O error on device sda5, logical block 312568642
[  320.207845] attempt to access beyond end of device
[  320.207847] sda: rw=0, want=312584772, limit=312581808
[  320.207850] Buffer I/O error on device sda5, logical block 312568643
[  320.208232] attempt to access beyond end of device
[  320.208235] sda: rw=0, want=312584773, limit=312581808
[  320.208237] Buffer I/O error on device sda5, logical block 312568644
[  320.208583] attempt to access beyond end of device
[  320.208586] sda: rw=0, want=312584774, limit=312581808
[  320.208588] Buffer I/O error on device sda5, logical block 312568645
[  320.208944] attempt to access beyond end of device
[  320.208946] sda: rw=0, want=312584775, limit=312581808
[  320.208949] Buffer I/O error on device sda5, logical block 312568646
[  320.209294] attempt to access beyond end of device
[  320.209296] sda: rw=0, want=312584776, limit=312581808
[  320.209298] Buffer I/O error on device sda5, logical block 312568647
[  320.209655] attempt to access beyond end of device
[  320.209658] sda: rw=0, want=312584769, limit=312581808
[  320.209660] Buffer I/O error on device sda5, logical block 312568640
[  320.210005] attempt to access beyond end of device
[  320.210008] sda: rw=0, want=312584770, limit=312581808
[  320.210010] Buffer I/O error on device sda5, logical block 312568641
[  320.210385] attempt to access beyond end of device
[  320.210388] sda: rw=0, want=312584771, limit=312581808
[  320.210617] attempt to access beyond end of device
[  320.210620] sda: rw=0, want=312584772, limit=312581808
[  320.210856] attempt to access beyond end of device
[  320.210858] sda: rw=0, want=312584773, limit=312581808
[  320.211087] attempt to access beyond end of device
[  320.211090] sda: rw=0, want=312584774, limit=312581808
[  320.211327] attempt to access beyond end of device
[  320.211330] sda: rw=0, want=312584775, limit=312581808
[  320.211562] attempt to access beyond end of device
[  320.211564] sda: rw=0, want=312584776, limit=312581808
[  327.715916] NET: Registered protocol family 10
[  327.716064] lo: Disabled Privacy Extensions
[  338.170932] eth0: no IPv6 routers present

Again thanks again for replying, have ran checkdisk as per instructed by the error log, but still the problem persists......


Porph!

---

### Post by Yellow Pasque on 2008-02-12
You should probably edit your post so that your output is between [ code ][ /code ] blocks (no spaces between the brackets). That would make it scrollable and a lot easier to read.
Good luck with your issue.

---

