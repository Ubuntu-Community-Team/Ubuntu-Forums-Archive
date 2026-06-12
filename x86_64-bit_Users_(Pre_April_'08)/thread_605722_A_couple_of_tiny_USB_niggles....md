---
title: "A couple of tiny USB niggles..."
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by SJI on 2007-11-07
Hello everyone,

I've recently junked my gaff ECS/Elite socket 939 main rboard and picked up an Asus A8N-SLI Premium board.

Slotted everything together and celebrated by wiping my Ubuntu 7.04 and installing a fresh 7.10 AMD64.

Everything is ticking along nicely. Install was pretty smooth with only bluetooth hanging; easily resolved.

I've come to try USB and pen drive, external reader etc are all recognised and run fine. However my internal card reader (no name UCR-61) and my trusty external USB HD don't seem to want to play ball.

USB HD is seen but fails to mount. That might be something to do with the NTFS partition on it so i'll wipe that and try again shortly.

The internal card reader is seen by the OS but i'm unable to read any cards that are inserted.

From syslog:

Unplug internal reader from main board gives:

Nov  7 15:18:28 boron kernel: [38646.573172] usb-storage: probe of 1-9:1.0 failed with error -1
Nov  7 15:18:28 boron kernel: [38646.573325] usb 1-9: USB disconnect, address 15
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.757158] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.760801] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1019_c55_20021119032313950'). 
Nov  7 15:18:28 boron kernel: [38646.706292] usb 2-6: USB disconnect, address 3
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.887214] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_14cd_6700____________if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.895090] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB_2_0_SD_MMC_Reader____________0_0'). 
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.899041] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_14cd_6700____________if0_scsi_host_scsi_device_lun0'). 
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.899144] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_14cd_6700____________if0_scsi_host'). 
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.901330] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_14cd_6700____________if0'). 
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.901441] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_14cd_6700___________'). 
Nov  7 15:18:28 boron NetworkManager: <debug> [1194448708.903287] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_14cd_6700____________usbraw'). 

Plug the internal reader back in and I get:

Nov  7 15:18:44 boron kernel: [38662.184137] usb 1-9: new full speed USB device using ohci_hcd and address 16
Nov  7 15:18:44 boron kernel: [38662.405859] usb 1-9: configuration #1 chosen from 1 choice
Nov  7 15:18:44 boron NetworkManager: <debug> [1194448724.588287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1019_c55_20021119032313950'). 
Nov  7 15:18:44 boron NetworkManager: <debug> [1194448724.625169] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 


Is the internal reader a lost cause or is the problem something simple?
The USB HD and the internal reader work fine if i reboot under XP, so they are known to be good and working.

Many thanks,

Stephen

Update:

USB HD problem was an NTFS issue, so only the card reader problem is outstanding.

---

