---
title: "Get some file from an very old hd, with hfs maybe (macintosh 7.x)"
date: 2006-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jollyr0ger on 2006-04-14
Hi. I've got a very old mac (Macintosh Performa 630, with os Macintosh 7.x), the filesystem would be hfs... maybe. 
The machine is broken, but the hd not.
I've an usb box for the hd, where i linked them.
Now with 'lsusb' my notebook (centrino 32bit) find the usb box:
> $ lsusb
Bus 005 Device 006: ID 04cf:8818 Myson Century, Inc. Fast 3.5" External Storage
...
...

I try to mount it with
> $ mount -t hfs /dev/sda /media/mac/
but don happen nothing, seam that the process is "loop". With ^C happen nothing. I've to turn off the box, and reapper the shell.

How can i do???

Help!](*,)

---

### Post by ubernoob on 2006-04-14
don't you have to specify which partition you should mount?
mount -t hfs /dev/sda**1** /media/mac/

try fdisk and see what that gives out:
sudo fdisk /dev/sda
then press "p"

---

### Post by jollyr0ger on 2006-04-14
with fdsik /dev/sda the shell do nothing, like the loop. and if i do something like mount -hfs /dev/sda1 /media/mac
appens the same thing: loop

if i do:
```
# dmesg | tail
usb-storage: waiting for device to settle before scanning
  Vendor: QUANTUM   Model: MAVERICK 540A     Rev: A06.
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 1057392 512-byte hdwr sectors (541 MB)
sda: assuming drive cache: write through
SCSI device sda: 1057392 512-byte hdwr sectors (541 MB)
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: unknown partition table
Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete

```

---

### Post by jdp on 2006-04-14
Your dmesg outpur says "unknown partition table" so it may be that when the 630 died, it took the HDD, or even just the info on it, with it.  Ubuntu can understand a regular Apple partition map, so it shoul have found it if ti was there and correct.

For an HFS partition, it'd probably be sda3 or higher, as Apple drives use the first few partitions for boot loaders and patch files, then the main OS parts after.

---

