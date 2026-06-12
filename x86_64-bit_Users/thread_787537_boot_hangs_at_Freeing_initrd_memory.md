---
title: "boot hangs at Freeing initrd memory"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by dbenc on 2008-05-09
I recently installed 8.04 64bit onto a 2-disk raid1 using the alternate install cd ... its two 750gb disks partitioned with lvm automagically as the install cd does it ... i believe the raid configuration is what is causing the problems, but i havent been able to pinpoint what's wrong...

now it hangs while booting with LILO, the last 2 messages are

[ 42.228504] checking if image is initramfs... it isn't (bad gzip magic number); looks like an initrd
[ 42.234624] Freeing initrd memory: 8667k freed

and then it just hangs ... 

ironically enough i intended to use raid1 to prevent any data loss, but as soon as i finished backing up everything this problem appeared.

I already tried mounting the disks using the livecd but ive been unable to get it to recognize the disks as having LVM at all ... ive followed a bunch of guides and none has helped ... :(

any ideas? if i can at least mount the disks and verify the data is there i can wipe one and reinstall everything ...

---

### Post by dbenc on 2008-05-09
/dev/sda and /dev/sdb make up the raid array, sdc is just storage .. 

sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00070fa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00061dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8598bb1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

```

sudo lvdisplay and sudo vgchange -ay both display No volume groups found

sudo vgscan --mknodes
```
ubuntu@ubuntu:~$ sudo vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  No volume groups found
  No volume groups found
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver 

```

i am starting to think i should use a 32bit live cd? could that be a factor?

---

### Post by Dixie Flatline on 2008-05-26
I hit the same problem upgrading from Gutsy amd64 to Hardy.  Here's the fix that worked for me: [https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/221664]("https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/221664")

I was able to boot just fine into the old 2.6.22 kernel, then edit /etc/lilo.conf to add the "large-memory" option and rerun lilo.  Now it's working OK.

In your situation, I'm not sure if it would be easier to rebuild with a separate non-LVM /boot partition -- as I understand it, that would allow you to use GRUB instead of LILO.

---

