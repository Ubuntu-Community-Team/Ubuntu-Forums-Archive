---
title: "IDE HDD has default name of scsi drive - can't mount or rename"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by phlembob on 2008-06-21
Any help would be appreciated.  I previously had an IDE with intermittent identification.  It was named drive1 and NTFS-3g was installed.  I uninstalled NTFS-3g, then reinstalled it again.  Now, the name is scsi drive by default boot-up.  It can't be named nor will it mount.  Any ideas on a good fix now that it is no longer intermittent?:lolflag:

---

### Post by pixel :-) on 2008-06-21
Now, the name is scsi drive by default boot-up
//names have changed with the last ubuntu.


nor will it mount.
//send us the result of dmesg command
//also send us the content of /etc/fstab

---

### Post by phlembob on 2008-06-21
Pixel, dmesg as follows:

el, low) -> IRQ 20
[   32.774077] sata_nv 0000:00:07.0: Using ADMA mode
[   32.774369] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   32.775558] scsi0 : sata_nv
[   32.775667] scsi1 : sata_nv
[   32.775800] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[   32.775802] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[   33.029046] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   33.085024] ata1: SATA link down (SStatus 0 SControl 300)
[   33.164208] usb 2-2: configuration #1 chosen from 1 choice
[   33.396844] ata2: SATA link down (SStatus 0 SControl 300)
[   33.398330] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   33.398336] sata_nv 0000:00:08.0: Using ADMA mode
[   33.398654] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   33.398757] scsi2 : sata_nv
[   33.398994] scsi3 : sata_nv
[   33.399123] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
[   33.399126] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
[   33.403281] usb 2-8: new high speed USB device using ehci_hcd and address 4
[   33.537387] usb 2-8: configuration #1 chosen from 1 choice
[   33.838041] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   33.864591] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.874168] ata3.00: ATA-7: SAMSUNG HD160JJ, ZM100-33, max UDMA7
[   33.874170] ata3.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
[   33.883146] ata3.00: configured for UDMA/133
[   34.047115] usb 1-1: configuration #1 chosen from 1 choice
[   34.048740] usbcore: registered new interface driver libusual
[   34.051772] Initializing USB Mass Storage driver...
[   34.051840] scsi4 : SCSI emulation for USB Mass Storage devices
[   34.051889] usbcore: registered new interface driver usb-storage
[   34.051892] USB Mass Storage support registered.
[   34.051969] usb-storage: device found at 4
[   34.051970] usb-storage: waiting for device to settle before scanning
[   34.192392] ata4: SATA link down (SStatus 0 SControl 300)
[   34.193932] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[   34.193939] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   34.195284] pata_amd 0000:00:06.0: version 0.3.10
[   34.195319] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   34.195623] scsi5 : pata_amd
[   34.195910] scsi6 : pata_amd
[   34.196479] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   34.196481] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   34.202637] Driver 'sd' needs updating - please use bus_type methods
[   34.202707] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   34.202716] sd 2:0:0:0: [sda] Write Protect is off
[   34.202718] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.202729] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.202776] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   34.202782] sd 2:0:0:0: [sda] Write Protect is off
[   34.202783] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.202793] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.202796]  sda: sda1 sda2 < sda5 sda6 >
[   34.242505] sd 2:0:0:0: [sda] Attached SCSI disk
[   34.246204] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   34.362170] ata5.00: ATA-7: Maxtor 4R120L0, RAMB1TU0, max UDMA/133
[   34.362174] ata5.00: 240121728 sectors, multi 1: LBA48 
[   34.379052] ata5.00: configured for UDMA/133
[   34.625178] Attempting manual resume
[   34.625181] swsusp: Resume From Partition 8:6
[   34.625182] PM: Checking swsusp image.
[   34.625343] PM: Resume from disk failed.
[   34.662255] kjournald starting.  Commit interval 5 seconds
[   34.663707] EXT3-fs: mounted filesystem with ordered data mode.
[   34.908211] ata6.00: ATAPI: TSSTcorpCD/DVDW SH-S162L, TS08, max UDMA/33
[   34.908226] ata6.01: ATAPI: TSSTcorpCD/DVDW SH-S162L, TS08, max UDMA/33
[   35.104037] ata6.00: configured for UDMA/33
[   35.299929] ata6.01: configured for UDMA/33
[   35.300005] scsi 5:0:0:0: Direct-Access     ATA      Maxtor 4R120L0   RAMB PQ: 0 ANSI: 5
[   35.300065] sd 5:0:0:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   35.300073] sd 5:0:0:0: [sdb] Write Protect is off
[   35.300075] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.300086] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.300120] sd 5:0:0:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   35.300126] sd 5:0:0:0: [sdb] Write Protect is off
[   35.300128] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.300137] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.300140]  sdb:<3>ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   35.373468] ata5.00: BMDMA stat 0x64
[   35.373474] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   35.373475]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   35.373477] ata5.00: status: { DRDY ERR }
[   35.373479] ata5.00: error: { ICRC ABRT }
[   35.373494] ata5: soft resetting link
[   35.549408] ata5.00: configured for UDMA/133
[   35.549417] ata5: EH complete
[   35.650555] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   35.650558] ata5.00: BMDMA stat 0x64
[   35.650563] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   35.650564]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   35.650566] ata5.00: status: { DRDY ERR }
[   35.650568] ata5.00: error: { ICRC ABRT }
[   35.650582] ata5: soft resetting link
[   35.830228] ata5.00: configured for UDMA/133
[   35.830234] ata5: EH complete
[   35.927628] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   35.927630] ata5.00: BMDMA stat 0x64
[   35.927634] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   35.927635]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   35.927637] ata5.00: status: { DRDY ERR }
[   35.927639] ata5.00: error: { ICRC ABRT }
[   35.927649] ata5: soft resetting link
[   36.105072] ata5.00: configured for UDMA/133
[   36.105076] ata5: EH complete
[   36.204726] ata5.00: limiting speed to UDMA/100:PIO4
[   36.204728] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   36.204731] ata5.00: BMDMA stat 0x64
[   36.204734] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   36.204736]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   36.204738] ata5.00: status: { DRDY ERR }
[   36.204740] ata5.00: error: { ICRC ABRT }
[   36.204750] ata5: soft resetting link
[   36.385920] ata5.00: configured for UDMA/100
[   36.385924] ata5: EH complete
[   36.481813] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   36.481815] ata5.00: BMDMA stat 0x64
[   36.481819] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   36.481820]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   36.481823] ata5.00: status: { DRDY ERR }
[   36.481824] ata5.00: error: { ICRC ABRT }
[   36.481834] ata5: soft resetting link
[   36.661759] ata5.00: configured for UDMA/100
[   36.661764] ata5: EH complete
[   36.758912] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   36.758914] ata5.00: BMDMA stat 0x64
[   36.758918] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   36.758919]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   36.758922] ata5.00: status: { DRDY ERR }
[   36.758924] ata5.00: error: { ICRC ABRT }
[   36.758935] ata5: soft resetting link
[   36.936609] ata5.00: configured for UDMA/100
[   36.936616] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   36.936619] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   36.936622] Descriptor sense data with sense descriptors (in hex):
[   36.936624]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   36.936628]         00 00 00 00 
[   36.936631] sd 5:0:0:0: [sdb] Add. Sense: Scsi parity error
[   36.936636] end_request: I/O error, dev sdb, sector 0
[   36.936639] Buffer I/O error on device sdb, logical block 0
[   36.936646] ata5: EH complete
[   37.036004] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   37.036005] ata5.00: BMDMA stat 0x64
[   37.036009] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   37.036010]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   37.036012] ata5.00: status: { DRDY ERR }
[   37.036013] ata5.00: error: { ICRC ABRT }
[   37.036023] ata5: soft resetting link
[   37.212448] ata5.00: configured for UDMA/100
[   37.212453] ata5: EH complete
[   37.313091] ata5.00: limiting speed to UDMA/33:PIO4
[   37.313094] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   37.313096] ata5.00: BMDMA stat 0x64
[   37.313100] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   37.313101]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   37.313103] ata5.00: status: { DRDY ERR }
[   37.313105] ata5.00: error: { ICRC ABRT }
[   37.313115] ata5: soft resetting link
[   37.492273] ata5.00: configured for UDMA/33
[   37.492276] ata5: EH complete
[   37.522551] ldm_validate_partition_table(): Disk read failed.
[   37.522558] Dev sdb: unable to read RDB block 0
[   37.522768]  unable to read partition table
[   37.522814] sd 5:0:0:0: [sdb] Attached SCSI disk
[   37.522844] sd 5:0:0:0: Attached scsi generic sg1 type 0
[   37.525161] scsi 6:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S162L TS08 PQ: 0 ANSI: 5
[   37.525233] scsi 6:0:0:0: Attached scsi generic sg2 type 5
[   37.526045] scsi 6:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S162L TS08 PQ: 0 ANSI: 5
[   37.526085] scsi 6:0:1:0: Attached scsi generic sg3 type 5
[   39.047285] usb-storage: device scan complete
[   39.047330] scsi 4:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[   39.971595] sd 4:0:0:0: [sdc] 3985408 512-byte hardware sectors (2041 MB)
[   39.974843] sd 4:0:0:0: [sdc] Write Protect is off
[   39.974845] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   39.974847] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   39.984592] sd 4:0:0:0: [sdc] 3985408 512-byte hardware sectors (2041 MB)
[   39.987711] sd 4:0:0:0: [sdc] Write Protect is off
[   39.987713] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   39.987714] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   39.987717]  sdc: sdc1
[   39.993253] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   39.993273] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   44.625186] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   44.754327] parport_pc 00:09: reported by Plug and Play ACPI
[   44.754379] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   44.806113] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.824899] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.896096] input: Power Button (FF) as /devices/virtual/input/input3
[   44.946818] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   44.946832] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   44.954346] ACPI: Power Button (FF) [PWRF]
[   44.954390] input: Power Button (CM) as /devices/virtual/input/input4
[   45.018311] ACPI: Power Button (CM) [PWRB]
[   45.033137] logips2pp: Detected unknown logitech mouse model 127
[   45.356897] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   45.356904] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 22
[   45.357154] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   45.513780] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   45.680290] intel8x0_measure_ac97_clock: measured 54693 usecs
[   45.680294] intel8x0: clocking to 46879
[   45.789763] Driver 'sr' needs updating - please use bus_type methods
[   45.805644] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda 

Unless you want the whole thing, this may give you a heads up on what I need.  I went a little long, but the beginning of HDD info is here.  Thanks for the help.

---

### Post by phlembob on 2008-06-21
Pixel, the rest you requested:
/etc/fstab: line 7: proc: command not found
/etc/fstab: line 9: /: is a directory
/etc/fstab: line 11: none: command not found
/etc/fstab: line 12: /dev/scd0: Permission denied
/etc/fstab: line 13: /dev/scd1: Permission denied
/etc/fstab: line 14: /dev/fd0: Permission denied
/etc/fstab: line 15: /dev/sdb1: No such file or directory
/etc/fstab: line 16: /dev/sda1: Permission denied

---

### Post by pixel :-) on 2008-06-21
yea i think this should help you immediately

gksudo ntfs-config

more info:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

try the manual installation that it proposes.It's either sdb1(sdb 122942 MB) or sda1(sda 160042 MB) sdc1(usb key? 2041 MB)

if it doesn't work

;) put a copy of /etc/fstab as an attachment.

How exactly did you tried to mount it?

---

### Post by phlembob on 2008-06-22
:lolflag: I may have figured out this problem.  I booted up and it is now registering the drive.  What was done...I physically change the drive from IDE Master to Slave.  The conflict between SATA Master and IDE Master may have solved the problem.  That is it.  The bios remains the same but it too sees it as a slave.  I will access data from Ubuntu and if the data is not corrupted this will be the last entry on this subject, here.:guitar:

---

