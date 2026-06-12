---
title: "x86_64 doesn't handle usb correctly"
date: 2007-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by valdisvi on 2007-04-10
I have two Kubuntu 6.10 (current updates) boxes.
One is AMD Athlon 32:
valdis@acteks:~$ uname -a
Linux acteks 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Another is AMD Athlon 64:
valdis@inks:~$ uname -a
Linux inks 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64 GNU/Linux

32 bit one works well. My USB Kingston DataTraveler 1GB and 4GB flash ROMs are mounted automatically, and Canon PowerShot S80 camera works right with gtkam.
64 bit one doesn't do that. Putting memory sticks or camera into USB socket even doesn't log something in dmesg -c. However, it works with older 64MB USB memory:
valdis@inks:~$ dmesg
[ 7958.994226] ohci_hcd 0000:00:0b.0: wakeup
[ 7959.377917] usb 2-5: new full speed USB device using ohci_hcd and address 11
[ 7959.597838] usb 2-5: configuration #1 chosen from 1 choice
[ 7959.600906] scsi10 : SCSI emulation for USB Mass Storage devices
[ 7959.601010] usb-storage: device found at 11
[ 7959.601012] usb-storage: waiting for device to settle before scanning
[ 7964.599182] usb-storage: device scan complete
[ 7964.606178]   Vendor: Generic   Model: Traveling Disk    Rev: 1.11
[ 7964.606186]   Type:   Direct-Access                      ANSI SCSI revision: 02
[ 7964.617143] SCSI device sdc: 129024 512-byte hdwr sectors (66 MB)
[ 7964.624135] sdc: Write Protect is off
[ 7964.624138] sdc: Mode Sense: 03 00 00 00
[ 7964.624139] sdc: assuming drive cache: write through
[ 7964.650116] SCSI device sdc: 129024 512-byte hdwr sectors (66 MB)
[ 7964.657110] sdc: Write Protect is off
[ 7964.657112] sdc: Mode Sense: 03 00 00 00
[ 7964.657114] sdc: assuming drive cache: write through
[ 7964.657118]  sdc: sdc1
[ 7964.667207] sd 10:0:0:0: Attached scsi removable disk sdc
[ 7964.667257] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 7969.852374] SMB connection re-established (-5)
[ 7969.908338] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
valdis@inks:~$ lsusb
Bus 002 Device 011: ID 0ea0:6803 Ours Technology, Inc. OTI-6803 Flash Disk
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
valdis@inks:~$

As it generally works, I looks as misconfiguration problem. Don't hesitate ask me config files for comparison if it will help.

---

### Post by Capslock118 on 2007-04-19
is your usb key a FAT filesystem? this might be a dumb question since all the usb keys i have ever played with were fat but whatev; its worth checking

---

### Post by valdisvi on 2007-04-19
FAT32, if more precisely. But it can't be related to filesystem, as it works on 32 machine.

---

### Post by ronocdh on 2007-04-19
> **Capslock118 said:**
> is your usb key a FAT filesystem? this might be a dumb question since all the usb keys i have ever played with were fat but whatev; its worth checking
My first thought, too, but OP is right in that it's also broken on i386. Hmph. I would love to see this solved! Maybe it's an issue with KDE? *ducks*

:popcorn:

---

### Post by firecat53 on 2007-04-20
Are you using any boot parameters like 'noapic' ?  I had to add an 'irqfixup' after 'noapic' to get my USB ports working on AMD64 laptop.

Just a thought :)

Scott

---

