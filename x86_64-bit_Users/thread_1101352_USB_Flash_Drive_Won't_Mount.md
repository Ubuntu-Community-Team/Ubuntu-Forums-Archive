---
title: "USB Flash Drive Won't Mount"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by MichaelSammels on 2009-03-20
OK, so I plugged in my flash drive this morning, and it won't mount. There is no output on the screen, etc, but my external HDD mounts fine. =/

Also, is it possible to set a hard drive to automount when you login to Ubuntu?

---

### Post by MaindotC on 2009-03-20
You can set it to automount by making some edits to the /etc/fstab file.  First of all, plug in the usb drive then post the output of:
```

sudo fdisk -l

```

---

### Post by MichaelSammels on 2009-03-20
michael@sokar:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e236c5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      181086  1454573263+  83  Linux
/dev/sda2          181087      182401    10562737+   5  Extended
/dev/sda5          181087      182401    10562706   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x666e6b55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976759804    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc30aae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          26      204819+  ee  GPT
/dev/sdc2              26      121602   976557744    7  HPFS/NTFS

---

### Post by MaindotC on 2009-03-20
Well that does seem to be a problem because I don't see the flash drive being listed.  This lists three drives that seem to be TB drives - wow 3 of them...

Okay, another thing you can do is open up System -> Administration -> System Log -> syslog, THEN plug in the flash drive.  When you plug it in you should see syslog produce some comments that will define how it names (or tries to name) the flash drive.

---

### Post by itendo on 2009-03-20
sorry about posting a dumb reply, but you did test the usb drive first right? ie. mount it on another computer?

---

### Post by MichaelSammels on 2009-03-20
Yes, I have tested it on my Windows Desktop. Works fine.

strAlan: Two of them are 1TB and the third is a 1.5TB ^_^

Also, I got the following output:

Mar 20 21:17:35 sokar kernel: [  376.816015] usb 5-7: new high speed USB device using ehci_hcd and address 5
Mar 20 21:17:35 sokar kernel: [  376.949592] usb 5-7: configuration #1 chosen from 1 choice
Mar 20 21:17:35 sokar kernel: [  376.999173] usbcore: registered new interface driver libusual
Mar 20 21:17:35 sokar kernel: [  377.009308] Initializing USB Mass Storage driver...
Mar 20 21:17:35 sokar kernel: [  377.009890] scsi4 : SCSI emulation for USB Mass Storage devices
Mar 20 21:17:35 sokar kernel: [  377.011512] usbcore: registered new interface driver usb-storage
Mar 20 21:17:35 sokar kernel: [  377.011517] USB Mass Storage support registered.
Mar 20 21:17:35 sokar kernel: [  377.012100] usb-storage: device found at 5
Mar 20 21:17:35 sokar kernel: [  377.012103] usb-storage: waiting for device to settle before scanning
Mar 20 21:17:40 sokar kernel: [  382.012188] usb-storage: device scan complete
Mar 20 21:17:46 sokar kernel: [  387.624015] usb 5-7: reset high speed USB device using ehci_hcd and address 5
Mar 20 21:18:01 sokar kernel: [  402.736526] usb 5-7: device descriptor read/64, error -110

---

### Post by MaindotC on 2009-03-20
Ok - looks like it knows that the device exists, electrically speaking, but it has a problem recognizing how to communicate with it.  I googled the error message: [http://is.gd/ogtr](http://is.gd/ogtr)  Check out some of those posts and see if you can make anything of it.

---

### Post by MichaelSammels on 2009-03-21
strAlan, I have an update:

I found that it is only this USB device which refuses to mount. Any ideas?

---

### Post by MaindotC on 2009-03-21
Examine your BIOS settings to ensure USB and USB 2.0 is enabled - look for any settings at all that relate to USB.  

Other than that, you'll need to find a module (driver) that will allow Ubuntu to communicate with that device.  It's really simple to understand - as I said the device is seen from an electrical standpoint, but Ubuntu doesn't know how to communicate with it's chipset and that's what modules do.  Any chance the manufacturer provides a linux driver?  If not, you'll have to google for linux usb drivers (or modules).  They may already be present in your system and you'll just need to load them with the "modprobe -a" command.  Please read the manpage so you understand what this command does.

The tough part is FINDING the module.  I'm not sure there are a lot of places with USB modules for linux because typically linux doesn't run into this problem.  There are several modules already loaded by default in your system which you can see with the "lsmod" command and I think the developers just kind of assume that statistically that will take care of a majority of user's issues.

Another step you may take is to file a bug report.  That's dedicated support and the moderators are usually very good about handling these issues, but they sometimes reply as little as once per day.

---

