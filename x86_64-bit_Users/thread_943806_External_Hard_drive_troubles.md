---
title: "External Hard drive troubles"
date: 2008-10-10
forum: x86 64-bit Users
---

### Post by mongoosled on 2008-10-10
I have a 1TB External Hard Drive from Cavalry that i got about a week ago. I have been storing movies and music, and some other things, and have been only accessing it on my roommates computers, which run Vista. A few days ago, the Hard Drive stopped working, and we can't see it on the Windows computers, but on mine, running Hardy, i can see a USB device, but i cannot mount it. 

if its useful, my fdisk -l  looks like this when the External is attached:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot        Start         End      Blocks   Id  System
/dev/sda1   *           1         13995   112414806   83  Linux
/dev/sda2             13996       14593     4803435    5  Extended
/dev/sda5             13996       14593     4803403+  82  Linux swap / Solaris
```


the 120gb is my internal hard drive. 

Anyways, my question is, is there a way to get into the drive and retrieve the files, or make it accessible again without deleting the files on it?

---

### Post by linux6994 on 2008-10-10
Maake sure that you have ntfs-3g installed, that will enable you to see the drive.

---

### Post by mongoosled on 2008-10-10
just checked. I have the latest version of ntfs-3g.

---

### Post by Jouke74 on 2008-10-10
Please define "stopped working" in more detail... It sounds like it's crashed this way. You will see a USB entry because the controller is probably still connecting. Vista does not give that information. Check also what happens in Vista when you connect it. In the event viewer look for disk errors. 

The same needs to be done using the command "dmesg" in the Ubuntu terminal. That will give more info why the disk cannot be read.

---

### Post by mongoosled on 2008-10-11
By stopped working, i mean that it no longer appears to be accessible. The External Hard Drive still turns on and i can hear it spinning when i listen for it. It probably did crash.

dmesg | -i usb   gives me
```
[  465.266594] usb 6-1: new high speed USB device using ehci_hcd and address 2
[  465.319776] usb 6-1: configuration #1 chosen from 1 choice
[  465.407567] usbcore: registered new interface driver libusual
[  465.425095] Initializing USB Mass Storage driver...
[  465.426631] scsi4 : SCSI emulation for USB Mass Storage devices
[  465.427939] usbcore: registered new interface driver usb-storage
[  465.427945] USB Mass Storage support registered.
[  465.428330] usb-storage: device found at 2
[  465.428333] usb-storage: waiting for device to settle before scanning
[  468.449128] usb-storage: device scan complete
[  471.075850] usb 6-1: reset high speed USB device using ehci_hcd and address 2

```

Windows can see it in Device Manager under the usb attachments. It says that there are no problems with it under Properties, but i cannot see it in the My Computer. I'm not sure what you mean by event viewer, though.

---

### Post by DeeZiD on 2008-10-12
> **mongoosled said:**
> By stopped working, i mean that it no longer appears to be accessible. The External Hard Drive still turns on and i can hear it spinning when i listen for it. It probably did crash.

dmesg | -i usb   gives me
```
[  465.266594] usb 6-1: new high speed USB device using ehci_hcd and address 2
[  465.319776] usb 6-1: configuration #1 chosen from 1 choice
[  465.407567] usbcore: registered new interface driver libusual
[  465.425095] Initializing USB Mass Storage driver...
[  465.426631] scsi4 : SCSI emulation for USB Mass Storage devices
[  465.427939] usbcore: registered new interface driver usb-storage
[  465.427945] USB Mass Storage support registered.
[  465.428330] usb-storage: device found at 2
[  465.428333] usb-storage: waiting for device to settle before scanning
[  468.449128] usb-storage: device scan complete
[  471.075850] usb 6-1: reset high speed USB device using ehci_hcd and address 2

```

Windows can see it in Device Manager under the usb attachments. It says that there are no problems with it under Properties, but i cannot see it in the My Computer. I'm not sure what you mean by event viewer, though.

This problem was introduced in a hardy kernel update.
Since then USB2.0 doesn't work on many PCs and notebooks, the same happens in intrepid, too!

Only thing you can try is to blacklist the ehci_hcd module.


Dennis

---

### Post by mongoosled on 2008-10-14
still no go. thanks for all the help, though.

---

### Post by Barlennan on 2008-11-09
What happens when you try to pmount it?

If it says something like "Error: drive not removable", try adding the drive (/dev/sdb or similar) to /etc/pmount.allow.  I've reported this bug here:

[https://bugs.edge.launchpad.net/ubuntu/+source/pmount/+bug/296164](https://bugs.edge.launchpad.net/ubuntu/+source/pmount/+bug/296164)

---

