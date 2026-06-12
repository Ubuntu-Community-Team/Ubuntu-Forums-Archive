---
title: "Mounting Memorex mp3 Player"
date: 2007-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by velociped on 2007-12-06
I'm a bit of a newbie on Feisty, amd64...other mp3 players mount automatically.  This new one doesn't.

My dmesg output after plugging the thing in looks like below.  I don't know enough about fstab to know quite what to add, or even if that's what I should be doing.
```
[ 3118.364134] usb 2-5: USB disconnect, address 2
[ 3145.107455] usb 2-5: new high speed USB device using ehci_hcd and address 3
[ 3145.177682] usb 2-5: configuration #1 chosen from 1 choice
[ 3151.977196] usb 2-5: USB disconnect, address 3
[ 3153.527486] usb 2-5: new high speed USB device using ehci_hcd and address 4
[ 3153.595857] usb 2-5: configuration #1 chosen from 1 choice
[ 3153.683527] usbcore: registered new interface driver libusual
[ 3153.698509] Initializing USB Mass Storage driver...
[ 3153.698607] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3153.698690] usb-storage: device found at 4
[ 3153.698693] usb-storage: waiting for device to settle before scanning
[ 3153.698712] usbcore: registered new interface driver usb-storage
[ 3153.698716] USB Mass Storage support registered.
[ 3156.515879] usb-storage: device scan complete
[ 3156.541394] scsi 2:0:0:0: Direct-Access     GENERIC  USB DISK DEVICE  1.00 PQ: 0 ANSI: 0 CCS
[ 3156.545104] sd 2:0:0:0: [sdb] 7920233 512-byte hardware sectors (4055 MB)
[ 3156.545788] sd 2:0:0:0: [sdb] Write Protect is off
[ 3156.545793] sd 2:0:0:0: [sdb] Mode Sense: 00 12 00 00
[ 3156.545798] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3156.548102] sd 2:0:0:0: [sdb] 7920233 512-byte hardware sectors (4055 MB)
[ 3156.548666] sd 2:0:0:0: [sdb] Write Protect is off
[ 3156.548671] sd 2:0:0:0: [sdb] Mode Sense: 00 12 00 00
[ 3156.548675] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3156.548681]  sdb: unknown partition table
[ 3156.554137] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 3156.554187] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 3299.195821] usb 2-5: USB disconnect, address 4
[ 3358.104976] usb 2-5: new high speed USB device using ehci_hcd and address 5
[ 3358.243673] usb 2-5: configuration #1 chosen from 1 choice
[ 3432.799276] usb 2-5: USB disconnect, address 5
[ 3445.015555] usb 2-5: new high speed USB device using ehci_hcd and address 6
[ 3445.088326] usb 2-5: configuration #1 chosen from 1 choice
[ 3540.434097] usb 2-5: USB disconnect, address 6
[ 3547.998647] usb 2-5: new high speed USB device using ehci_hcd and address 7
[ 3548.070624] usb 2-5: configuration #1 chosen from 1 choice

 
```

---

