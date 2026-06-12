---
title: "Ubuntu and MSI K8N Neo4 Platinum SLI Sound Issues"
date: 2005-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurtwisener on 2005-06-08
Hi folks,

I have installed Ubuntu 5.04 AMD 64 and am loving it.  I just can't seem to get any sound at all.  My mainboard is an MSI K8N Neo4 Platinum SLI featuring an onboard 7.1 channel SB Live! setup.  When I was playing around with Slackware on my old P4 I would get the same error as I get now, namely, the "dev/dsp... device cannot be found... using null" error.

When I try to run ALSA Mixer, I get this error:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
``` 

lspci yields:
```
root@kurt:/home/kwisener # lspci
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:06.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
0000:01:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 15)
0000:03:00.0 Unknown mass storage controller: Silicon Image, Inc. (formerly CMD Technology Inc): Unknown device 3132 (rev 01)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0140 (rev a2)
``` 

And finally, the dmesg output:

```
root@kurt:/home/kwisener # dmesg
arent bridge - 0000:00:09.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSMB] (IRQs *3 4 5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 11 *12 14 15)
ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 11 *12 14 15)
ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
PCI: Cannot allocate resource region 0 of device 0000:02:00.0
PCI: Cannot allocate resource region 0 of device 0000:03:00.0
PCI: Cannot allocate resource region 2 of device 0000:03:00.0
PCI: Cannot allocate resource region 3 of device 0000:05:00.0
PCI-DMA: Disabling IOMMU.
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4800-0x487f has been reserved
pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
audit: initializing netlink socket (disabled)
audit(1118226932.236:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Linux agpgart interface v0.100 (c) Dave Jones
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, khubd not stopped
 Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4044KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 132k freed
ACPI: Fan [FAN] (on)
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THRM] (22 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
NFORCE-CK804: chipset revision 162
NFORCE-CK804: not 100% native mode: will probe irqs later
NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
    ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: WDC WD600EB-00DJF0, ATA DISK drive
hdb: ST3200822A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdb: max request size: 1024KiB
hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 p3 < p5 >
Probing IDE interface ide1...
hdc: _NEC DVD_RW ND-3500AG, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ===|
Freeing memory... done (513 pages freed)
Restarting tasks... done
VFS: Can't find ext3 filesystem on dev hdb2.
VFS: Can't find an ext2 filesystem on dev hdb2.
ReiserFS: hdb2: found reiserfs format "3.6" with standard journal
ReiserFS: hdb2: using ordered data mode
ReiserFS: hdb2: journal params: device hdb2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: hdb2: checking transaction log (hdb2)
ReiserFS: hdb2: replayed 19 transactions in 5 seconds
ReiserFS: hdb2: Using r5 hash to sort names
Adding 3004112k swap on /dev/hdb5.  Priority:-1 extents:1
hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Real Time Clock Driver v1.12
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
input: PC Speaker
inserting floppy driver for 2.6.10-5-amd64-generic
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 23 (level, low) -> IRQ 23
ohci_hcd 0000:00:02.0: PCI device 10de:005a (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 23, pci mem 0xfebff000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 10 ports detected
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 22 (level, low) -> IRQ 22
ehci_hcd 0000:00:02.1: PCI device 10de:005b (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ehci_hcd 0000:00:02.1: irq 22, pci mem 0xfebfe000
ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
PCI: cache line size of 64 is not supported by device 0000:00:02.1
ehci_hcd 0000:00:02.1: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 10 ports detected
libata version 1.10 loaded.
sata_nv version 0.5
ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:07.0[A] -> GSI 21 (level, low) -> IRQ 21
PCI: Setting latency timer of device 0000:00:07.0 to 64
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 21
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 21
ata1: no device found (phy stat 00000000)
scsi0 : sata_nv
ata2: no device found (phy stat 00000000)
scsi1 : sata_nv
ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 20 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:08.0 to 64
ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 20
ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 20
usb 1-2: new low speed USB device using ohci_hcd and address 2
ata3: no device found (phy stat 00000000)
scsi2 : sata_nv
usb 1-7: new full speed USB device using ohci_hcd and address 3
ata4: no device found (phy stat 00000000)
scsi3 : sata_nv
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:0a.0 to 64
eth0: forcedeth.c: subsystem: 01462:7100 bound to 0000:00:0a.0
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
shpchp: Address64 -------- Resource unparsed
shpchp: Address64 -------- Resource unparsed
shpchp: Address64 -------- Resource unparsed
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
pciehp: Address64 -------- Resource unparsed
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6204
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
usbcore: registered new driver hiddev
input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-2
input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ts: Compaq touchscreen protocol output
Linux Tulip driver version 1.1.13 (May 11, 2002)
ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
ACPI: PCI interrupt 0000:01:06.0[A] -> GSI 16 (level, low) -> IRQ 16
tulip0:  EEPROM default media type Autosense.
tulip0:  Index #0 - Media 10baseT (#0) described by a 21142 Serial PHY (2) block.
tulip0:  Index #1 - Media 10baseT-FDX (#4) described by a 21142 Serial PHY (2) block.
tulip0:  Index #2 - Media 100baseTx (#3) described by a 21143 SYM PHY (4) block.tulip0:  Index #3 - Media 100baseTx-FDX (#5) described by a 21143 SYM PHY (4) block.
tulip0:  Index #4 - Media 100baseTx (#3) described by a 21143 reset method (5) block.
eth1: Digital DS21143 Tulip rev 65 at 000000000001df00, 00:00:C5:53:BF:1C, IRQ 16.
NET: Registered protocol family 17
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:01:0c.0[A] -> GSI 19 (level, low) -> IRQ 19
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fe9fe000-fe9fe7ff]  Max Packet=[2048]
ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:02:00.0 to 64
eth%d: -- ERROR --
        Class:  internal Software error
        Nr:  0x2bd
        Msg:  TWSI: transfer does not complete
sk98lin: SkGeInitAssignRamToQueues failed.
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc000099bc35]
NET: Registered protocol family 10
Disabled Privacy Extensions on device ffffffff80350f40(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:05:00.0 to 64
NVRM: loading NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
NVRM: WARNING: Your Linux kernel has problems in its implementation of
NVRM: the change_page_attr kernel interface.  The NVIDIA kernel
NVRM: module will attempt to work around these problems, but
NVRM: system stability may be affected.  It is recommended that
NVRM: you update to a 2.6.11 or newer kernel.

drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2 (1500 mV)
powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
cpu_init done, current fid 0xe, vid 0x2
eth0: no IPv6 routers present
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root
``` 

I am not sure whether this is a module or driver issue, given the nature of the error and that it occurred in both my P4 and AMD64 builds, I have been approaching it from the module standpoint but I am at a loss ](*,) .  Any help would be awesome, thank you for your consideration.

-Kurt

---

### Post by kurtwisener on 2005-06-08
After checking the ALSA website I have found the right module but I do not know how to load it.

Sound Blaster Live 24bit
Sound Blaster Live 7.1 	SB0410 (ca0106)

When I modprobe I get:
```
root@kurt:/home/kwisener # modprobe ca0106
FATAL: Module ca0106 not found.
root@kurt:/home/kwisener # modprobe sb0401
FATAL: Module sb0401 not found.
root@kurt:/home/kwisener #
``` 

From what I can gather, the ALSA package from ubuntu configured without the snd-card=ca0106 option.  When I download and try to install the ALSA sourcecode it refuses to compile correctly.  Does anyone know of how to compile/install the module?

-Kurt

---

### Post by kurtwisener on 2005-06-08
DISREGARD ALL OF LAST...

RTFM at [http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211) :-x 

It works. :)  

Problem solved thank you for viewing this and I am sorry I took up your time.

Mad props to Ubuntu Geek, I give thanks for you.\0/

---

