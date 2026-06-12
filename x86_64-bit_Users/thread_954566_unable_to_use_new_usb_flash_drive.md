---
title: "unable to use new usb flash drive"
date: 2008-10-21
forum: x86 64-bit Users
---

### Post by firebottle01 on 2008-10-21
i'm a relatively new user, and probably being a bit of a duffer but can anyone help.
I have a new computer (and a new 4GB flash drive). i am unable to access the new flash drive, though the computer accepts an older flash drive. The error message i am getting is something like 'unable to mount device'. If i boot up my system with my new and old flash drives connected the older drive automatically appears on my desktop, but I can only 'see' the new flash drive at /media. 
Any help would be greatly appreciated this is the only problem i have encountered so far since installing 64 bit ubuntu.
many thanks

---

### Post by firebottle01 on 2008-10-21
the full error message is 'unable to mount location, can't mount file'

---

### Post by fornix on 2008-10-21
Insert the flash drive and type the following command
```
$ dmesg
```
Look towards the tail for messages which seem to suggest the USB has been detected properly by linux.
Paste the relevant output here.
Also paste the output for the following command after inserting USB drive
```
$ sudo fdisk -l
```

---

### Post by firebottle01 on 2008-10-21
output from dmsg:-

[ 1128.486252] usb 2-8: new high speed USB device using ehci_hcd and address 2
[ 1128.620403] usb 2-8: configuration #1 chosen from 1 choice
[ 1128.669875] usbcore: registered new interface driver libusual
[ 1128.694869] Initializing USB Mass Storage driver...
[ 1128.697483] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1128.698268] usbcore: registered new interface driver usb-storage
[ 1128.698275] USB Mass Storage support registered.
[ 1128.698378] usb-storage: device found at 2
[ 1128.698380] usb-storage: waiting for device to settle before scanning
[ 1133.685077] usb-storage: device scan complete
[ 1133.685839] scsi 4:0:0:0: Direct-Access     PEAK III Flash Drive      0.00 PQ: 0 ANSI: 2
[ 1133.687266] sd 4:0:0:0: [sdb] 7897088 512-byte hardware sectors (4043 MB)
[ 1133.687935] sd 4:0:0:0: [sdb] Write Protect is off
[ 1133.687939] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1133.687941] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1133.690666] sd 4:0:0:0: [sdb] 7897088 512-byte hardware sectors (4043 MB)
[ 1133.691414] sd 4:0:0:0: [sdb] Write Protect is off
[ 1133.691417] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1133.691418] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1133.691422]  sdb: sdb1
[ 1133.906480] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1133.906515] sd 4:0:0:0: Attached scsi generic sg2 type 0

---

### Post by firebottle01 on 2008-10-21
$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8e3b51d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29696   238533088+  83  Linux
/dev/sda2           29697       30401     5662912+   5  Extended
/dev/sda5           29697       30401     5662881   82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         492     3948512+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 38)

---

### Post by dcstar on 2008-10-21
> **firebottle01 said:**
> $ sudo fdisk -l
......
Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         492     3948512+   b  W95 FAT32
**Partition 1 has different physical/logical endings**:
     phys=(490, 254, 63) logical=(491, 145, 38)

Reformat the drive (using Gparted) and it should then make sense to Linux.

---

### Post by firebottle01 on 2008-10-25
thanks David,

i've used gparted to format the flash disk, but i am still getting the 'unable to mount volume' message. i feel really out of my depth on this, any help would be much appreciated

Kevin

---

### Post by Manice on 2008-10-26
What does sudo fdisk -l say after the format?

---

### Post by firebottle01 on 2008-10-29
thanks for all the responses. i have managed to get the flash drive to work in my roundabout way. Changing the drive to FAT16 meant i was able to write access drive, something i was unable to do when drive was formatted linux.

firebottle01

---

### Post by John Jason Jordan on 2008-10-30
> **firebottle01 said:**
> thanks for all the responses. i have managed to get the flash drive to work in my roundabout way. Changing the drive to FAT16 meant i was able to write access drive, something i was unable to do when drive was formatted linux.firebottle01

FAT16 is so out of date. You should use FAT32. FAT32 should present no read/write problems.

When you formatted it with a Linux filesystem you probably had a permissions issue. FAT16 and FAT32 cannot hold permission data, so they are completely unsecure. However, as long as the flash drive is in your pocket and you don't keep national defense secrets on it, either FAT16 or FAT32 should be fine. You just want to use FAT32 because it is more up to date.

---

### Post by feenana on 2008-10-30
[img]http://www.top1gaming.com/cosplay/Goddess-16.jpg[/img]See more pics [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-45-16.html).  Want to see more [[color=#800080]cosplayer[/color]](http://www.top1gaming.com/cosplayer.php) ? Show yourself on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/forumdisplay.php?fid=29).**Recommend : **[[color=#0000ff]Chrono Trigger's Ayla [/color]](http://www.top1gaming.com/coscontent-130.html)   [[color=#0000ff]Legend of Zelda cosplay[/color]](http://www.top1gaming.com/coscontent-51.html)

---

