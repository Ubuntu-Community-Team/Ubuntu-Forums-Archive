---
title: "Can't mount USB HDD"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by da_bad_spellah on 2007-12-05
HDD in question is WD MyBook 500GB with FAT32 filesystem. Mounted and worked as expected with Feisty 32 and Gutsy 32. Problem began with new (64 bit) hardware and Gutsy 64 install.

When drive is connected, I get a GUI error that says:

```
Cannot mount volume.

Unable to mount the voume 'USBVideo'.
```

Expanding the Details area, the error goes on to say:

```
mount:/dev/sdd1 already mounted or /media/USBVideo busy
```

Using the mount command, I've confirmed that /dev/sdd1 isn't already mounted.

/media/USBVideo isn't pre-existing, so clearly it's not in use - Ubuntu would be creating it as needed.

Using lsof and other commands, I'm convinced that nothing is accessing /dev/sdd1.

/var/log/messages shows the following when I connect the drive:

```
Dec  5 11:45:14 navi kernel: [296604.579326] usb 7-4: USB disconnect, address 12
Dec  5 11:45:33 navi kernel: [296623.733189] usb 7-4: new high speed USB device using ehci_hcd and address 13
Dec  5 11:45:33 navi kernel: [296623.864965] usb 7-4: configuration #1 chosen from 1 choice
Dec  5 11:45:33 navi kernel: [296623.866206] scsi15 : SCSI emulation for USB Mass Storage devices
Dec  5 11:45:38 navi kernel: [296628.719009] scsi 15:0:0:0: Direct-Access     WD       5000KS External  101a PQ: 0 ANSI: 4
Dec  5 11:45:38 navi kernel: [296628.720810] sd 15:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Dec  5 11:45:38 navi kernel: [296628.721290] sd 15:0:0:0: [sdd] Write Protect is off
Dec  5 11:45:38 navi kernel: [296628.722503] sd 15:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Dec  5 11:45:38 navi kernel: [296628.722988] sd 15:0:0:0: [sdd] Write Protect is off
Dec  5 11:45:38 navi kernel: [296628.722998]  sdd: sdd1
Dec  5 11:45:38 navi kernel: [296628.731287] sd 15:0:0:0: [sdd] Attached SCSI disk
Dec  5 11:45:38 navi kernel: [296628.731325] sd 15:0:0:0: Attached scsi generic sg4 type 0
Dec  5 11:45:38 navi kernel: [296629.036239] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi kernel: [296629.036251] device-mapper: ioctl: error adding target to table
Dec  5 11:45:38 navi kernel: [296629.036978] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi kernel: [296629.036988] device-mapper: ioctl: error adding target to table
Dec  5 11:45:38 navi kernel: [296629.088969] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi kernel: [296629.089241] device-mapper: ioctl: error adding target to table
Dec  5 11:45:38 navi kernel: [296629.089657] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi kernel: [296629.093346] device-mapper: ioctl: error adding target to table

```

dmesg says:

```
[296604.579326] usb 7-4: USB disconnect, address 12
[296623.733189] usb 7-4: new high speed USB device using ehci_hcd and address 13
[296623.864965] usb 7-4: configuration #1 chosen from 1 choice
[296623.866206] scsi15 : SCSI emulation for USB Mass Storage devices
[296623.866269] usb-storage: device found at 13
[296623.866271] usb-storage: waiting for device to settle before scanning
[296628.718285] usb-storage: device scan complete
[296628.719009] scsi 15:0:0:0: Direct-Access     WD       5000KS External  101a PQ: 0 ANSI: 4
[296628.720810] sd 15:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[296628.721290] sd 15:0:0:0: [sdd] Write Protect is off
[296628.721294] sd 15:0:0:0: [sdd] Mode Sense: 11 00 00 00
[296628.721296] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[296628.722503] sd 15:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[296628.722988] sd 15:0:0:0: [sdd] Write Protect is off
[296628.722991] sd 15:0:0:0: [sdd] Mode Sense: 11 00 00 00
[296628.722994] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[296628.722998]  sdd: sdd1
[296628.731287] sd 15:0:0:0: [sdd] Attached SCSI disk
[296628.731325] sd 15:0:0:0: Attached scsi generic sg4 type 0
[296629.036239] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
[296629.036247] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
[296629.036251] device-mapper: ioctl: error adding target to table
[296629.036978] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
[296629.036985] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
[296629.036988] device-mapper: ioctl: error adding target to table
[296629.088969] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
[296629.089136] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
[296629.089241] device-mapper: ioctl: error adding target to table
[296629.089657] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
[296629.093215] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
[296629.093346] device-mapper: ioctl: error adding target to table
```

and in the syslog:

```
Dec  5 11:45:33 navi kernel: [296623.733189] usb 7-4: new high speed USB device using ehci_hcd and address 13
Dec  5 11:45:33 navi kernel: [296623.864965] usb 7-4: configuration #1 chosen from 1 choice
Dec  5 11:45:33 navi kernel: [296623.866206] scsi15 : SCSI emulation for USB Mass Storage devices
Dec  5 11:45:33 navi kernel: [296623.866269] usb-storage: device found at 13
Dec  5 11:45:33 navi kernel: [296623.866271] usb-storage: waiting for device to settle before scanning
Dec  5 11:45:33 navi NetworkManager: <debug> [1196873133.597727] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_900_57442D5743414E5531383739363938'). 
Dec  5 11:45:33 navi NetworkManager: <debug> [1196873133.626094] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_900_57442D5743414E5531383739363938_if0'). 
Dec  5 11:45:33 navi NetworkManager: <debug> [1196873133.653419] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_900_57442D5743414E5531383739363938_usbraw'). 
Dec  5 11:45:38 navi kernel: [296628.718285] usb-storage: device scan complete
Dec  5 11:45:38 navi kernel: [296628.719009] scsi 15:0:0:0: Direct-Access     WD       5000KS External  101a PQ: 0 ANSI: 4
Dec  5 11:45:38 navi kernel: [296628.720810] sd 15:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Dec  5 11:45:38 navi kernel: [296628.721290] sd 15:0:0:0: [sdd] Write Protect is off
Dec  5 11:45:38 navi kernel: [296628.721294] sd 15:0:0:0: [sdd] Mode Sense: 11 00 00 00
Dec  5 11:45:38 navi kernel: [296628.721296] sd 15:0:0:0: [sdd] Assuming drive cache: write through
Dec  5 11:45:38 navi kernel: [296628.722503] sd 15:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Dec  5 11:45:38 navi kernel: [296628.722988] sd 15:0:0:0: [sdd] Write Protect is off
Dec  5 11:45:38 navi kernel: [296628.722991] sd 15:0:0:0: [sdd] Mode Sense: 11 00 00 00
Dec  5 11:45:38 navi kernel: [296628.722994] sd 15:0:0:0: [sdd] Assuming drive cache: write through
Dec  5 11:45:38 navi kernel: [296628.722998]  sdd: sdd1
Dec  5 11:45:38 navi multipathd: sdd: add path (uevent) 
Dec  5 11:45:38 navi kernel: [296628.731287] sd 15:0:0:0: [sdd] Attached SCSI disk
Dec  5 11:45:38 navi kernel: [296628.731325] sd 15:0:0:0: Attached scsi generic sg4 type 0
Dec  5 11:45:38 navi NetworkManager: <debug> [1196873138.512894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_900_57442D5743414E5531383739363938_if0_scsi_host'). 
Dec  5 11:45:38 navi NetworkManager: <debug> [1196873138.516823] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_900_57442D5743414E5531383739363938_if0_scsi_host_scsi_device_lun0'). 
Dec  5 11:45:38 navi NetworkManager: <debug> [1196873138.517859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_900_57442D5743414E5531383739363938_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Dec  5 11:45:38 navi multipathd: 1WDC_WD5000KS-00MNB0_WD-WCANU1879698: load table [0 976773168 multipath 0 0 1 1 round-robin 0 1 1 8:48 1000] 
Dec  5 11:45:38 navi multipathd: 1WDC_WD5000KS-00MNB0_WD-WCANU1879698: event checker started 
Dec  5 11:45:38 navi multipathd: dm-1: add map (uevent) 
Dec  5 11:45:38 navi multipathd: dm-1: devmap already registered 
Dec  5 11:45:38 navi multipathd: dm-2: add map (uevent) 
Dec  5 11:45:38 navi multipathd: uevent trigger error 
Dec  5 11:45:38 navi multipathd: dm-3: add map (uevent) 
Dec  5 11:45:38 navi multipathd: uevent trigger error 
Dec  5 11:45:38 navi multipathd: dm-3: remove map (uevent) 
Dec  5 11:45:38 navi kernel: [296629.036239] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi kernel: [296629.036247] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Dec  5 11:45:38 navi kernel: [296629.036251] device-mapper: ioctl: error adding target to table
Dec  5 11:45:38 navi multipathd: dm-3: add map (uevent) 
Dec  5 11:45:38 navi multipathd: uevent trigger error 
Dec  5 11:45:38 navi multipathd: dm-3: remove map (uevent) 
Dec  5 11:45:38 navi kernel: [296629.036978] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi kernel: [296629.036985] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Dec  5 11:45:38 navi kernel: [296629.036988] device-mapper: ioctl: error adding target to table
Dec  5 11:45:38 navi NetworkManager: <debug> [1196873138.771109] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_5000KS_External_57442D5743414E5531383739363938_0_0'). 
Dec  5 11:45:38 navi NetworkManager: <debug> [1196873138.813924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_E0DC_2260'). 
Dec  5 11:45:38 navi multipathd: dm-3: add map (uevent) 
Dec  5 11:45:38 navi kernel: [296629.088969] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi kernel: [296629.089136] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Dec  5 11:45:38 navi kernel: [296629.089241] device-mapper: ioctl: error adding target to table
Dec  5 11:45:38 navi multipathd: dm-3: remove map (uevent) 
Dec  5 11:45:38 navi kernel: [296629.089657] device-mapper: table: device /dev/mapper/1WDC_WD5000KS-00MNB0_WD-WCANU1879698p1 too small for target
Dec  5 11:45:38 navi multipathd: dm-3: add map (uevent) 
Dec  5 11:45:38 navi kernel: [296629.093215] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Dec  5 11:45:38 navi kernel: [296629.093346] device-mapper: ioctl: error adding target to table
Dec  5 11:45:38 navi multipathd: dm-3: remove map (uevent) 
Dec  5 11:45:39 navi udevd-event[10436]: run_program: '/sbin/kpartx' abnormal exit
```

I've searched my brains out, both in these forums and on the net in general. I've seen quite a number of people looking for help with what seems to be the same problem. The only solution I've seen - and it is reported as working by several - is to remove the 'evms' package. Unfortunately, I don't have that package installed!

I'm reasonably sure my problem is related to the encrypted partition I've set up using [these instructions]("http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/"). (The encrypted partition is on an internal SATA drive, not the external USB drive in question.) I say that I suspect this has somehow caused the problem for two reasons: it's the only "unusual" thing I've done to my new Gutsy64 install, and from what I've read, it appears that the issue is related to the device mapper in some way.

Here are a few more bits of info that may or may not be pertinent:

I have another WD MyBook, this one 300GB. When I connect it, I get a different result. The log files all reflect the device connection and identification, but end with

```
 usb 7-4: reset high speed USB device using ehci_hcd and address 15
```

Although the drive appears as /dev/hdd, the sole partition does not have an entry in dev. Consequently, I cannot mount it either.

Finally, I have a third USB HDD. This one is an enclosure with two HDDs, each 750GB. The hardware in the enclosure combines them into a single 1.5TB RAID volume and it ordinarily mounts  as a single drive / partition. When I connect it, I see this in syslog:

```
Dec  5 12:09:56 navi kernel: [298086.006292] usb 7-6: new high speed USB device using ehci_hcd and address 17
Dec  5 12:09:56 navi kernel: [298086.137828] usb 7-6: configuration #1 chosen from 1 choice
Dec  5 12:09:56 navi kernel: [298086.138999] scsi18 : SCSI emulation for USB Mass Storage devices
Dec  5 12:09:56 navi kernel: [298086.139052] usb-storage: device found at 17
Dec  5 12:09:56 navi kernel: [298086.139053] usb-storage: waiting for device to settle before scanning
Dec  5 12:09:56 navi NetworkManager: <debug> [1196874596.152266] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_3_ABCDEF0123456789'). 
Dec  5 12:09:56 navi NetworkManager: <debug> [1196874596.184709] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_3_ABCDEF0123456789_if0'). 
Dec  5 12:09:56 navi NetworkManager: <debug> [1196874596.196250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_3_ABCDEF0123456789_usbraw'). 
Dec  5 12:09:59 navi kernel: [298089.760262] usb 7-4: reset high speed USB device using ehci_hcd and address 15
Dec  5 12:10:01 navi kernel: [298090.991222] usb-storage: device scan complete
Dec  5 12:10:01 navi kernel: [298090.991703] scsi 18:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
Dec  5 12:10:01 navi kernel: [298090.992781] sd 18:0:0:0: [sdc] 2930297856 512-byte hardware sectors (1500313 MB)
Dec  5 12:10:01 navi kernel: [298090.993265] sd 18:0:0:0: [sdc] Write Protect is off
Dec  5 12:10:01 navi kernel: [298090.993267] sd 18:0:0:0: [sdc] Mode Sense: 10 00 00 00
Dec  5 12:10:01 navi kernel: [298090.993269] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Dec  5 12:10:01 navi kernel: [298090.994112] sd 18:0:0:0: [sdc] 2930297856 512-byte hardware sectors (1500313 MB)
Dec  5 12:10:01 navi kernel: [298090.994596] sd 18:0:0:0: [sdc] Write Protect is off
Dec  5 12:10:01 navi kernel: [298090.994599] sd 18:0:0:0: [sdc] Mode Sense: 10 00 00 00
Dec  5 12:10:01 navi kernel: [298090.994600] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Dec  5 12:10:04 navi kernel: [298090.994603]  sdc:<6>usb 7-4: reset high speed USB device using ehci_hcd and address 15
Dec  5 12:10:05 navi multipathd: error calling out /lib/udev/scsi_id -g -u -s /block/sdd 
Dec  5 12:10:05 navi multipathd: sdd: failed to get path uid 
Dec  5 12:10:05 navi multipathd: uevent trigger error 
Dec  5 12:10:05 navi multipathd: sdc: remove path (uevent) 
Dec  5 12:10:05 navi NetworkManager: <debug> [1196874605.060655] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_3_ABCDEF0123456789_if0_scsi_host'). 
Dec  5 12:10:05 navi NetworkManager: <debug> [1196874605.061320] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_3_ABCDEF0123456789_if0_scsi_host_scsi_device_lun0'). 
Dec  5 12:10:05 navi kernel: [298095.757647]  sdc1
Dec  5 12:10:05 navi kernel: [298095.757728] sd 18:0:0:0: [sdc] Attached SCSI disk
Dec  5 12:10:05 navi kernel: [298095.757798] sd 18:0:0:0: Attached scsi generic sg3 type 0
Dec  5 12:10:05 navi multipathd: sdc: add path (uevent) 
Dec  5 12:10:05 navi NetworkManager: <debug> [1196874605.776922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_3_ABCDEF0123456789_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Dec  5 12:10:10 navi multipathd: sdc: failed to get path uid 
Dec  5 12:10:10 navi multipathd: uevent trigger error 
```

syslog:

```
Dec  5 12:04:58 navi kernel: [297788.310831] usb 7-4: new high speed USB device using ehci_hcd and address 15
Dec  5 12:04:58 navi kernel: [297788.447147] usb 7-4: configuration #1 chosen from 1 choice
Dec  5 12:04:58 navi kernel: [297788.447380] scsi17 : SCSI emulation for USB Mass Storage devices
Dec  5 12:05:03 navi kernel: [297793.333796] scsi 17:0:0:0: Direct-Access     WD       2500JB External  0107 PQ: 0 ANSI: 0
Dec  5 12:05:03 navi kernel: [297793.334994] sd 17:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Dec  5 12:05:03 navi kernel: [297793.335839] sd 17:0:0:0: [sdd] Write Protect is off
Dec  5 12:05:03 navi kernel: [297793.336692] sd 17:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Dec  5 12:05:03 navi kernel: [297793.337540] sd 17:0:0:0: [sdd] Write Protect is off
Dec  5 12:05:03 navi kernel: [297793.337553]  sdd: sdd1
Dec  5 12:05:03 navi kernel: [297793.346976] sd 17:0:0:0: [sdd] Attached SCSI disk
Dec  5 12:05:03 navi kernel: [297793.347037] sd 17:0:0:0: Attached scsi generic sg4 type 0
Dec  5 12:05:08 navi kernel: [297798.423691] usb 7-4: reset high speed USB device using ehci_hcd and address 15
Dec  5 12:09:23 navi kernel: [298053.310225] usb 7-6: USB disconnect, address 5
Dec  5 12:09:56 navi kernel: [298086.006292] usb 7-6: new high speed USB device using ehci_hcd and address 17
Dec  5 12:09:56 navi kernel: [298086.137828] usb 7-6: configuration #1 chosen from 1 choice
Dec  5 12:09:56 navi kernel: [298086.138999] scsi18 : SCSI emulation for USB Mass Storage devices
Dec  5 12:09:59 navi kernel: [298089.760262] usb 7-4: reset high speed USB device using ehci_hcd and address 15
Dec  5 12:10:01 navi kernel: [298090.991703] scsi 18:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
Dec  5 12:10:01 navi kernel: [298090.992781] sd 18:0:0:0: [sdc] 2930297856 512-byte hardware sectors (1500313 MB)
Dec  5 12:10:01 navi kernel: [298090.993265] sd 18:0:0:0: [sdc] Write Protect is off
Dec  5 12:10:01 navi kernel: [298090.994112] sd 18:0:0:0: [sdc] 2930297856 512-byte hardware sectors (1500313 MB)
Dec  5 12:10:01 navi kernel: [298090.994596] sd 18:0:0:0: [sdc] Write Protect is off
Dec  5 12:10:04 navi kernel: [298090.994603]  sdc:<6>usb 7-4: reset high speed USB device using ehci_hcd and address 15
Dec  5 12:10:05 navi kernel: [298095.757647]  sdc1
Dec  5 12:10:05 navi kernel: [298095.757728] sd 18:0:0:0: [sdc] Attached SCSI disk
Dec  5 12:10:05 navi kernel: [298095.757798] sd 18:0:0:0: Attached scsi generic sg3 type 0
```

dmesg:

```
[298086.006292] usb 7-6: new high speed USB device using ehci_hcd and address 17
[298086.137828] usb 7-6: configuration #1 chosen from 1 choice
[298086.138999] scsi18 : SCSI emulation for USB Mass Storage devices
[298086.139052] usb-storage: device found at 17
[298086.139053] usb-storage: waiting for device to settle before scanning
[298089.760262] usb 7-4: reset high speed USB device using ehci_hcd and address 15
[298090.991222] usb-storage: device scan complete
[298090.991703] scsi 18:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[298090.992781] sd 18:0:0:0: [sdc] 2930297856 512-byte hardware sectors (1500313 MB)
[298090.993265] sd 18:0:0:0: [sdc] Write Protect is off
[298090.993267] sd 18:0:0:0: [sdc] Mode Sense: 10 00 00 00
[298090.993269] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[298090.994112] sd 18:0:0:0: [sdc] 2930297856 512-byte hardware sectors (1500313 MB)
[298090.994596] sd 18:0:0:0: [sdc] Write Protect is off
[298090.994599] sd 18:0:0:0: [sdc] Mode Sense: 10 00 00 00
[298090.994600] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[298090.994603]  sdc:<6>usb 7-4: reset high speed USB device using ehci_hcd and address 15
[298095.757647]  sdc1
[298095.757728] sd 18:0:0:0: [sdc] Attached SCSI disk
[298095.757798] sd 18:0:0:0: Attached scsi generic sg3 type 0
```

Again, this creates /dev/sdd, but no device appears in dev for the partition.

All three drives are working normally elsewhere.

Any assistance will be greatly appreciated.

---

### Post by Escipion on 2007-12-11
Since I'm a newbie I can't give you a very detailed solution but I had similar problems with all my usb devices under Gutsy 64 and solved the by adding the "noirqdebug" in the bootline on grub.

Please tell me if it works for you.

---

