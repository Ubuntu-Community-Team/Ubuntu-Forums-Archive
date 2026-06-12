---
title: "Usb thumb drive not mounting on 64bit system"
date: 2008-07-12
forum: x86 64-bit Users
---

### Post by biker955 on 2008-07-12
I am having issues with an 8Gb thumb drive. Under the 32bit version it mounts fine, but under the 64bit on my main machine it comes up with an error.

dmesg output:-
[  122.466494] Initializing USB Mass Storage driver...
[  122.467752] scsi6 : SCSI emulation for USB Mass Storage devices
[  122.469358] usbcore: registered new interface driver usb-storage
[  122.469364] USB Mass Storage support registered.
[  122.469697] usb-storage: device found at 8
[  122.469699] usb-storage: waiting for device to settle before scanning
[  124.739727] usb-storage: device scan complete
[  124.740387] scsi 6:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[  125.011423] sd 6:0:0:0: [sdb] 15663104 512-byte hardware sectors (8020 MB)
[  125.012726] sd 6:0:0:0: [sdb] Write Protect is off
[  125.012730] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  125.012732] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  125.017334] sd 6:0:0:0: [sdb] 15663104 512-byte hardware sectors (8020 MB)
[  125.018242] sd 6:0:0:0: [sdb] Write Protect is off
[  125.018245] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  125.018247] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  125.018251]  sdb: sdb1
[  125.019210] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  125.019245] sd 6:0:0:0: Attached scsi generic sg3 type 0

When I plug it into the 32bit system it mounts under /media/disk-1 and shows as 8Gb Disk, but under the 64bit sys it says Cannot mount volume. and the details are:-
mount point cannot contain the following characters: ....

I have removed the /media/.hal-mtab file in-case it had some errors, but still not playing.

Any ideas?

Ken

---

### Post by dcstar on 2008-07-12
> **biker955 said:**
> I am having issues with an 8Gb thumb drive. Under the 32bit version it mounts fine, but under the 64bit on my main machine it comes up with an error.
........
Any ideas?

Ken

And exactly what filesystem is it formatted at?

---

### Post by biker955 on 2008-07-12
Opp! Knew I had forgotten something. It is formated as fat32. Single partition.
I can mount it using, sudo mount -t vfat -o rw,defaults /dev/sdb1 /media/disk, but it is mounted as read only on the 64bit system.

---

### Post by dcstar on 2008-07-13
> **biker955 said:**
> Opp! Knew I had forgotten something. It is formated as fat32. Single partition.
I can mount it using, sudo mount -t vfat -o rw,defaults /dev/sdb1 /media/disk, but it is mounted as read only on the 64bit system.

```
umount /dev/sdb1
fsck -y /dev/sdb1
```

Then pull it out and put it back in.

---

### Post by biker955 on 2008-07-13
ok done that same result.

fsck message:-
fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 0 files, 1/1952089 clusters

no errors just no mounting on the 64bit system.

Ok just resorted to deleting the partition and recreating it on the 64bit system, loads now. VERY strange.:lolflag:

---

