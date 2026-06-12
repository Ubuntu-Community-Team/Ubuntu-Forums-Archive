---
title: "NVIDIA card problems (6200 GT)"
date: 2005-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2005-04-15
so I installed my nvidia card, but it tells e that the memory is 64MB when I have a Nvidia  6200 GT . I can see the panel that has he settings but I cannot change any of them. How do I checked the version that I have.
Thanks again to all that respond
Sara

---

### Post by mthaddon on 2005-04-15
I looked at the specs for this card, and it seems like that may be correct.

Here's an example:

[http://www2.atelco.de/7CybxYJrs6f-GS/lo/articledetail.jsp?aid=4609&agid=430](http://www2.atelco.de/7CybxYJrs6f-GS/lo/articledetail.jsp?aid=4609&agid=430)

If you know that you have a different amount of RAM or the specific card that would be helpful. If you could also post the output of dmesg that would be useful. To do that just open a command line and type "dmesg" and then post the output that's related to the graphics card.

---

### Post by tikal26 on 2005-04-15
here is the output I cannot find the nvidia settings I find a nfoce line for my chipset but nothing on the vidio card maybe I'm new so maybe I'm reading it wrong
$ sudo dmesg
: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ===|
Freeing memory... done (518 pages freed)
Restarting tasks... done
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 498004k swap on /dev/hda3.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
Real Time Clock Driver v1.12
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
input: PC Speaker
inserting floppy driver for 2.6.10-5-amd64-k8
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
irda_init()
NET: Registered protocol family 23
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 23 (level, low) -> IRQ 23
ohci_hcd 0000:00:02.0: PCI device 10de:005a (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 23, pci mem 0xfebff000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 10 ports detected
usb 1-5: new low speed USB device using ohci_hcd and address 2
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
ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 21 (level, low) -> IRQ 21
PCI: Setting latency timer of device 0000:00:04.0 to 64
usb 1-5: new low speed USB device using ohci_hcd and address 3
intel8x0_measure_ac97_clock: measured 49977 usecs
intel8x0: clocking to 46884
usb 1-6: new full speed USB device using ohci_hcd and address 4
libata version 1.10 loaded.
sata_nv version 0.5
ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:07.0[A] -> GSI 20 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:07.0 to 64
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xCC00 irq 20
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xCC08 irq 20
Linux video capture interface: v1.00
usb 1-9: new low speed USB device using ohci_hcd and address 5
ata1: no device found (phy stat 00000000)
scsi0 : sata_nv
ata2: no device found (phy stat 00000000)
scsi1 : sata_nv
ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:08.0 to 64
ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xB800 irq 23
ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xB808 irq 23
usb 1-10: new full speed USB device using ohci_hcd and address 6
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
usbcore: registered new driver hiddev
drivers/usb/media/ibmcam.c: IBM PC Camera USB camera found (model 2, rev. 0x030a )
videodev: "ibmcam USB Camera" has no release callback. Please fix your driver fo r proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
drivers/usb/media/usbvideo.c: ibmcam on /dev/video0: canvas=352x240 videosize=35 2x240
usbcore: registered new driver ibmcam
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
input: USB HID v1.00 Mouse [1241:1177] on usb-0000:00:02.0-5
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
input: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:02.0-9
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
input: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:02.0-9
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
ata3: no device found (phy stat 00000000)
scsi2 : sata_nv
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 pr oto 2 vid 0x03F0 pid 0xB802
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Initializing USB Mass Storage driver...
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
ata4: no device found (phy stat 00000000)
scsi3 : sata_nv
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
scsi4 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:0a.0 to 64
eth0: forcedeth.c: subsystem: 0105b:0ca2 bound to 0000:00:0a.0
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
ohci1394: fw-host0: Unexpected PCI resource length of 1000!
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fe9ff000-fe9ff7ff]  Max  Packet=[2048]
eth0: no link during initialization.
NET: Registered protocol family 17
eth0: link up.
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200008ccc7]
  Vendor: HP        Model: Photosmart 7400   Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
usb-storage: device scan complete
Attached scsi removable disk sda at scsi4, channel 0, id 0, lun 0
NET: Registered protocol family 10
Disabled Privacy Extensions on device ffffffff80373bc0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6 (1400 mV)
powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
cpu_init done, current fid 0xa, vid 0x6
eth0: no IPv6 routers present
Also I al posting a screnshot with nvidia-settings

---

### Post by tikal26 on 2005-04-15
here is a screenshot

---

