---
title: "can't mount sdb1 USB jump drive?"
date: 2009-05-08
forum: x86 64-bit Users
---

### Post by dh003i on 2009-05-08
Why can't I mount my jump drive? here's what I do:

I have one that says sdb:sdb1 when I plug it in; but i have no /dev/sdb1 device:

```
**# mount -t vfat /dev/sdb1 /media/"USB Drive"**
mount: special device /dev/sdb1 does not exist
```

Navigating to /dev and using MAKEDEV doesn't help:

```
[b]# cd /dev
# sudo ./MAKEDEV sdb1[/b]
.udevdb or .udev presence implies active udev. Aborting MAKEDEV invocation.
```

Using mknod doesn't help either:

```
[b]# sudo mknod -m 666 /dev/sdb1 b 3 1
# mount -t vfat /dev/sdb1 /media/"USB Drive"[/b]
mount: /dev/sdb1 is not a valid block device
```

This sucks. What do I do?

---

### Post by cariboo on 2009-05-08
Could you paste the results of:

```
dmesg | tail -n15
```

when you plug in your device in your next post.

---

### Post by dh003i on 2009-05-09
The result of **dmesg | tail -n15**

```
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 8:0:0:0: Direct-Access OCZ DIESEL PMAP PQ: 0 ANSI: 0 CCS
sd 8:0:0:0: [sdb] 7831552 512-byte hardware sectors: (4.00 GB/3.73 GiB)
sd 8:0:0:0: [sdb] Write Protect is off
sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
sd 8:0:0:0: [sdb] Assuming drive cache: write through
sd 8:0:0:0: [sdb] 7831552 512-byte hardware sectors: (4.00 /3.73 GiB)
sd 8:0:0:0: [sdb] Write Protect is off
sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
sd 8:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1
sd 8:0:0:0: [sdb] Attached SCSI removable disk
sd 8:0:0:0: [sdb] Attached scsi generic sg2 type 0
```

---

