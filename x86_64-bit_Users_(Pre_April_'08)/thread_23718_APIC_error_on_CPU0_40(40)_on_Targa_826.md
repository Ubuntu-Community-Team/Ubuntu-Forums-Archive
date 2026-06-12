---
title: "APIC error on CPU0: 40(40) on Targa 826"
date: 2005-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by artimess on 2005-04-03
I am trying to install Hoary on Targa Traveller 826, which is an AMD64 with Readon X700 graphics card;  I am getting lots of APIC ERROR on CPU0 : 40(40)
Could someone help please.  here is a complete listing of dmesg output:
artimess@ubuntu:~$ dmesg
Bootdata ok (command line is root=/dev/hda1 ro console=tty0 quiet splash)
Linux version 2.6.10-5-amd64-generic (buildd@yellow) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Mar 24 14:53:03 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001ff40000 (usable)
 BIOS-e820: 000000001ff40000 - 000000001ff50000 (ACPI data)
 BIOS-e820: 000000001ff50000 - 0000000020000000 (ACPI NVS)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
No mptable found.
On node 0 totalpages: 130880
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 126784 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
ACPI: RSDP (v000 MSI                                   ) @ 0x00000000000f8310
ACPI: RSDT (v001 MSI    1029     0x03092005 MSFT 0x00000097) @ 0x000000001ff40000
ACPI: FADT (v002 MSI    1029     0x03092005 MSFT 0x00000097) @ 0x000000001ff40200
ACPI: MADT (v001 MSI    OEMAPIC  0x03092005 MSFT 0x00000097) @ 0x000000001ff40300
ACPI: WDRT (v001 MSI    MSI_OEM  0x03092005 MSFT 0x00000097) @ 0x000000001ff40360
ACPI: MCFG (v001 MSI    OEMMCFG  0x03092005 MSFT 0x00000097) @ 0x000000001ff403b0
ACPI: SSDT (v001 OEM_ID OEMTBLID 0x00000001 INTL 0x02002026) @ 0x000000001ff434b0
ACPI: OEMB (v001 MSI    MSI_OEM  0x03092005 MSFT 0x00000097) @ 0x000000001ff50040
ACPI: DSDT (v001    MSI     1029 0x03092005 INTL 0x02002026) @ 0x0000000000000000
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:12 APIC version 16
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
Setting APIC routing to flat
Using ACPI (MADT) for SMP configuration information
Checking aperture...
CPU 0: aperture @ 3fd4000000 size 32 MB
Aperture from northbridge cpu 0 too small (32 MB)
No AGP bridge found
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro console=tty0 quiet splash
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 65536 bytes)
time.c: Using 1.193182 MHz PIT timer.
time.c: Detected 1989.869 MHz processor.
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Memory: 506960k/523520k available (1584k kernel code, 15880k reserved, 1008k data, 132k init)
Calibrating delay loop... 3907.58 BogoMIPS (lpj=1953792)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 256 (order: 0, 4096 bytes)
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: Mobile AMD Athlon(tm) 64 Processor 3000+ stepping 00
ACPI: Looking for DSDT in initrd... not found!
Using local APIC NMI watchdog using perfctr0
Using local APIC timer interrupts.
Detected 12.436 MHz APIC timer.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
NET: Registered protocol family 16
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
PCI: Transparent bridge - 0000:00:14.4
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Embedded Controller [EC] (gpe 6)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP2._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 *7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 10 devices
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
PCI-DMA: Disabling IOMMU.
IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
audit: initializing netlink socket (disabled)
audit(1112567098.222:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Linux agpgart interface v0.100 (c) Dave Jones
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ACPI: PCI interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, khubd not stopped
 Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
POP2  RTL AC97 MC97
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 3988KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 132k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Thermal Zone [THRM] (70 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: HTS548080M9AT00, ATA DISK drive
Probing IDE interface ide1...
hdc: PIONEER DVD-RW DVR-K15, ATAPI CD/DVD-ROM drive
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 128KiB
hda: 156301488 sectors (80026 MB) w/7877KiB Cache, CHS=65535/16/63
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Stopping tasks: ===|
Freeing memory... done (515 pages freed)
Restarting tasks... done
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1485972k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio2
APIC error on CPU0: 00(40)
ts: Compaq touchscreen protocol output
APIC error on CPU0: 40(40)
Real Time Clock Driver v1.12
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
APIC error on CPU0: 40(40)
input: PC Speaker
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
ohci_hcd 0000:00:13.0: PCI device 1002:4374 (ATI Technologies Inc)
ohci_hcd 0000:00:13.0: irq 19, pci mem 0xfbdfd000
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
ACPI: PCI interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies Inc)
ohci_hcd 0000:00:13.1: irq 19, pci mem 0xfbdfe000
ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 4 ports detected
ACPI: PCI interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies Inc)
ehci_hcd 0000:00:13.2: irq 19, pci mem 0xfbdff000
ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 8 ports detected
ACPI: PCI interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 18
eth0: RealTek RTL8139 at 0xffffff00000f4c00, 00:0c:76:f7:38:c1, IRQ 18
eth0:  Identified 8139 chip type 'RTL-8101'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 19
Yenta: CardBus bridge found at 0000:02:04.0 [1462:0291]
Yenta: ISA IRQ mask 0x04b8, PCI irq 19
Socket status: 30000006
ACPI: PCI interrupt 0000:02:04.1[B] -> GSI 20 (level, low) -> IRQ 20
Yenta: CardBus bridge found at 0000:02:04.1 [1462:0291]
Yenta: ISA IRQ mask 0x04b8, PCI irq 20
Socket status: 30000006
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:04.2[C] -> GSI 21 (level, low) -> IRQ 21
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fbfff000-fbfff7ff]  Max Packet=[2048]
NET: Registered protocol family 17
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00007e6634]
NET: Registered protocol family 10
Disabled Privacy Extensions on device ffffffff80350dc0(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [ADP1] (on-line)
eth0: no IPv6 routers present
ACPI: Battery Slot [BAT1] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
APIC error on CPU0: 40(40)
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8:    0 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa (1300 mV)
powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x4 (1450 mV)
cpu_init done, current fid 0xc, vid 0x2
powernow-k8: ph2 null fid transition 0xc
powernow-k8: vid trans failed, vid 0x1, curr 0x2
powernow-k8: transition frequency failed
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
psmouse.c: Wheel Mouse at isa0060/serio2/input0 lost synchronization, throwing 1 bytes away.
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)
APIC error on CPU0: 40(40)

---

### Post by Aurels on 2005-04-10
I got the same on a debian sarge but the debs seems to be installed.
But I cannot configure X with the X700 grphics card (no server).  :twisted: 
At the moment I've only found a rpm for this card.

---

### Post by StephenTidey on 2005-05-27
Hiya,

Yea, I get this msg on my targa as well.  Do you still have XP on there or has it been 'removed'?  I just ask because I notice both my dad (he bought one as well) and I get the msg "Embedded Controller has not responded within the timeout period" (or something close) under XP - they seem to run fine so it looks like something that happens with all of them, unless our four come from the same batch...

Oops didn't make the above very clear about why I am mentioning XP -  I think the EC XP is referring to IS the APIC, hence why we get error msgs reported about it under both OS's.

---

### Post by Capodastro on 2005-08-06
Hi guys,
I am a new acquisition in the forum. I am also attempting to install Sarge AMD64 on a Targa 826. I prepared a “vanilla” configuration leaving just a C: Drive with DOS and ME and deleting the preinstalled QuickMedia. During the installation process I got an already constant cpu0 error 40. I know Windows very well, as developer, but I never saw Linux before, just no idea about…
I had the impression that Debian was installing properly despite the reported error: I assumed that perhaps the reason could be in a new and very nasty “security” feature by the cpu, in accord with the MS wishes. Under Windows it can be disabled from boot.ini by changing “/noexecute=optin” to /noexecute=AlwaysOff. Linux doesn’t have a reason to react on such error messages. In effect they disappeared after rebooting, further installing and rebooting again. Finally I got a login with a console shell, no X: unrecognized graphic card!. I don’t feel concerned at this subject because the QuickMedia installation must contain at least: graphic, audio, USB and remote control drivers. It is certainly possible to extract them from the installation.
My big concern is about wireless: I need it really!!!
At this point still no idea about Linux and its interface commands: I am looking for some starting documentation for beginners, after restoring temporarily my original installation and leaving empty space for Linux.
Please let me know about what I should know!
Regards,
Capodastro

---

### Post by tseliot on 2005-08-06
I don't think your problem depends on the "APIC ERROR on CPU0 : 40(40)". I've always had it (it appeared several times) but it has never affected the functioning of my computer. My CPU is an AMD64, just like yours. Don't you worry.

---

### Post by Capodastro on 2005-08-06
Thanks for your help, tseliot: anyway my cpu is a Turion 64. As soon as I get something of interesting I will post it.
Have a great time, indeed
Capodastro

---

### Post by Capodastro on 2005-08-07
Hallo guys,
So, the new Traveller is shipped with a preinstalled Linux partition equipped with an own hardware start button starting a "PowerCinema" program. At this time you can also get an update by Targa.

On this laptop XP starts very fast but according with the user guide the additional hardware start button is there just to power up a DVD program even faster. It doesn't make any sense! On the other hand, the Laptop is declared as specific for XP. 

I will need time to learn Linux, anyway I went for a walk in the preinstalled QuickMedia partition. For this pourpose I used Partition Magic. In all discretion, I found all the laptops drivers preinstalled and also a preinstalled copy of Windows X! The specific AMD64 files are also included.

I don't need to say more, you know now what to do.

Have fun,
Capodastro

---

