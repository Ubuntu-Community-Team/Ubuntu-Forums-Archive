---
title: "USB will not mount"
date: 2007-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by leona on 2007-01-07
Hi there

Well new week, new problem.

I connect my PDA (Imate Kjam) via USB to my computer, I use a piece of software that makes it look like a usb drive, which is great.

Up until last week, this was working fine.

Now I get
[quote=Ubuntu]
mount: no medium found
mount: no medium found
error: could not execute pmount
[/quote]

output from messages
[quote=messages]
Jan  7 17:12:08 leona-amd64-3Ghz kernel: [  705.988075] sdf: Write Protect is off
Jan  7 17:12:08 leona-amd64-3Ghz kernel: [  705.997062] SCSI device sdf: 3972096 512-byte hdwr sectors (2034 MB)
Jan  7 17:12:08 leona-amd64-3Ghz kernel: [  706.000050] sdf: Write Protect is off
Jan  7 17:12:08 leona-amd64-3Ghz kernel: [  706.000061]  sdf: sdf1
Jan  7 17:12:08 leona-amd64-3Ghz kernel: [  706.011059] sd 3:0:0:0: Attached scsi removable disk sdf
Jan  7 17:12:08 leona-amd64-3Ghz kernel: [  706.011108] sd 3:0:0:0: Attached scsi generic sg5 type 0
Jan  7 17:12:23 leona-amd64-3Ghz kernel: [  720.546468] sd 3:0:0:0: SCSI error: return code = 0x8000002
Jan  7 17:12:23 leona-amd64-3Ghz kernel: [  720.546474] sdf: Current: sense key: Medium Error
Jan  7 17:12:23 leona-amd64-3Ghz kernel: [  720.546477]     Additional sense: Recorded entity not found
Jan  7 17:12:23 leona-amd64-3Ghz kernel: [  720.546483] end_request: I/O error, dev sdf, sector 249
Jan  7 17:12:37 leona-amd64-3Ghz kernel: [  734.726045] sdf: Current: sense key: Medium Error
Jan  7 17:12:37 leona-amd64-3Ghz kernel: [  734.726048]     Additional sense: Recorded entity not found
Jan  7 17:12:37 leona-amd64-3Ghz kernel: [  734.726054] end_request: I/O error, dev sdf, sector 250
[/quote]

trying to mount manually gives me
[quote=term]
sudo mount /dev/sdf /media/pda
mount: No medium found
[/quote]

Tried a number of different file system types 
[quote=term]
sudo mount -t usbfs /dev/sdf /media/pda
[/quote]
Kinda worked but gave me
[quote=term]
0 dr-xr-xr-x 2 root root 0 2007-01-07 17:01 001
0 dr-xr-xr-x 2 root root 0 2007-01-07 17:01 002
0 dr-xr-xr-x 2 root root 0 2007-01-07 17:01 003
0 dr-xr-xr-x 2 root root 0 2007-01-07 17:01 004
0 dr-xr-xr-x 2 root root 0 2007-01-07 17:01 005
0 -r--r--r-- 1 root root 0 2007-01-07 17:42 devices
[/quote]
and not my actual files
[quote=term]
sudo mount -t vfat /dev/sdf /media/pda
mount: No medium found
sudo mount -t autofs /dev/sdf /media/pda
mount: wrong fs type, bad option, bad superblock on /dev/sdf,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/quote]

What else can I try?

---

### Post by leona on 2007-01-07
looks like its a problem either with the device or the cable, can't get ti working in any operating system, the wonders of modern technology :(

---

### Post by leona on 2007-01-07
Hum, after a long time I do get
> 
mount: /dev/sdf is not a valid block device
mount: /dev/sdf is not a valid block device
error: could not execute pmount

seems it can't make up its mind if there is media in it or not, and when there is, it can't ead it.
Edit to add, connected it to my computer at work (Win XP) and it works perfectly, I can access it and read / write to it no troube, so its not the device that's the problem.

---

### Post by eggdeng on 2007-05-28
Just a shot in the dark but maybe you should be trying to mount /dev/sdf1 (partition) rather than /dev/sdf (device)?

---

### Post by leona on 2007-05-28
Hi eggdeng Thanks 

I tried
[quote=term]
sudo mount -t usbfs /dev/sdf1 /media/pda
[/quote]
and got
[quote=term]
dr-xr-xr-x 2 root root 0 2007-05-28 00:48 001
dr-xr-xr-x 2 root root 0 2007-05-28 00:48 002
-r--r--r-- 1 root root 0 2007-05-28 22:09 devices
[/quote]

---

### Post by leona on 2007-09-04
I was hoping that the upgrade to Fiesty 7.04 would fix this, sadly not, Is this a bug, should I report it?

```

Sep  4 18:41:05 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927665.857362] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_if0_serial_usb_0'). 
Sep  4 18:41:05 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927665.863440] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_if0'). 
Sep  4 18:41:05 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927665.864777] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_serial_usb_1'). 
Sep  4 18:41:05 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927665.868667] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_if1'). 
Sep  4 18:41:05 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927665.869993] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial'). 
Sep  4 18:41:05 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927665.872077] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_usbraw'). 
Sep  4 18:41:09 leona-ubuntu-linux-amd64 kernel: [ 2741.097862] usb 1-4: new full speed USB device using ohci_hcd and address 3
Sep  4 18:41:09 leona-ubuntu-linux-amd64 kernel: [ 2741.323676] usb 1-4: configuration #1 chosen from 1 choice
Sep  4 18:41:09 leona-ubuntu-linux-amd64 kernel: [ 2741.330355] scsi7 : SCSI emulation for USB Mass Storage devices
Sep  4 18:41:09 leona-ubuntu-linux-amd64 kernel: [ 2741.326807] usb-storage: device found at 3
Sep  4 18:41:09 leona-ubuntu-linux-amd64 kernel: [ 2741.326811] usb-storage: waiting for device to settle before scanning
Sep  4 18:41:09 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927669.980062] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0068DB9A07A6'). 
Sep  4 18:41:10 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927670.044290] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0068DB9A07A6_if0'). 
Sep  4 18:41:10 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927670.065393] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0068DB9A07A6_if0_scsi_host'). 
Sep  4 18:41:10 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927670.104154] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0068DB9A07A6_usbraw'). 
Sep  4 18:41:14 leona-ubuntu-linux-amd64 kernel: [ 2746.323835] usb-storage: device scan complete
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.842670] scsi 7:0:0:0: Direct-Access     Softick  Card Export      0001 PQ: 0 ANSI: 0 CCS
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.884593] SCSI device sdf: 3972096 512-byte hdwr sectors (2034 MB)
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.891583] sdf: Write Protect is off
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.891587] sdf: Mode Sense: 00 00 00 00
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.891591] sdf: assuming drive cache: write through
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.910561] SCSI device sdf: 3972096 512-byte hdwr sectors (2034 MB)
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.917550] sdf: Write Protect is off
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.917554] sdf: Mode Sense: 00 00 00 00
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.917557] sdf: assuming drive cache: write through
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.917563]  sdf: sdf1
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.932571] sd 7:0:0:0: Attached scsi removable disk sdf
Sep  4 18:41:15 leona-ubuntu-linux-amd64 kernel: [ 2746.932616] sd 7:0:0:0: Attached scsi generic sg5 type 0
Sep  4 18:41:15 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927675.616265] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0068DB9A07A6_if0_scsi_host_scsi_device_lun0'). 
Sep  4 18:41:15 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927675.653095] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0068DB9A07A6_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep  4 18:41:15 leona-ubuntu-linux-amd64 NetworkManager: <debug info>^I[1188927675.829518] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Softick_Card_Export_0068DB9A07A6_0_0'). 
Sep  4 18:41:19 leona-ubuntu-linux-amd64 kernel: [ 2750.526272] sd 7:0:0:0: SCSI error: return code = 0x08000002
Sep  4 18:41:19 leona-ubuntu-linux-amd64 kernel: [ 2750.526277] sdf: Current: sense key: Medium Error
Sep  4 18:41:19 leona-ubuntu-linux-amd64 kernel: [ 2750.526280]     Additional sense: Recorded entity not found
Sep  4 18:41:19 leona-ubuntu-linux-amd64 kernel: [ 2750.526288] end_request: I/O error, dev sdf, sector 249
Sep  4 18:41:19 leona-ubuntu-linux-amd64 kernel: [ 2750.526294] Buffer I/O error on device sdf1, logical block 0
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772068] sd 7:0:0:0: SCSI error: return code = 0x08000002
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772074] sdf: Current: sense key: Medium Error
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772077]     Additional sense: Recorded entity not found
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772083] end_request: I/O error, dev sdf, sector 250
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772087] Buffer I/O error on device sdf1, logical block 1
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772093] Buffer I/O error on device sdf1, logical block 2
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772096] Buffer I/O error on device sdf1, logical block 3
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772099] Buffer I/O error on device sdf1, logical block 4
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772102] Buffer I/O error on device sdf1, logical block 5
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772105] Buffer I/O error on device sdf1, logical block 6
Sep  4 18:41:33 leona-ubuntu-linux-amd64 kernel: [ 2764.772108] Buffer I/O error on device sdf1, logical block 7
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800325] sd 7:0:0:0: SCSI error: return code = 0x08000002
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800330] sdf: Current: sense key: Medium Error
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800333]     Additional sense: Recorded entity not found
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800338] end_request: I/O error, dev sdf, sector 249
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800342] Buffer I/O error on device sdf1, logical block 0
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800348] Buffer I/O error on device sdf1, logical block 1
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800352] Buffer I/O error on device sdf1, logical block 2
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800354] Buffer I/O error on device sdf1, logical block 3
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800357] Buffer I/O error on device sdf1, logical block 4
Sep  4 18:41:50 leona-ubuntu-linux-amd64 kernel: [ 2781.800360] Buffer I/O error on device sdf1, logical block 5

```

---

### Post by Herm87 on 2007-11-11
No, I don't think this is a bug. In general /dev/hda always points to the harddisk while /dev/hda1 points to the first partition. Has always been this way, hasn't it?

---

