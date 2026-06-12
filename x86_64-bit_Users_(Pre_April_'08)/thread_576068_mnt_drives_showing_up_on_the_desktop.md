---
title: "/mnt/ drives showing up on the desktop"
date: 2007-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by mad chey on 2007-10-14
Hi

having a slight problem with my new installation of gutsy and fstab

set up fstab as ive done previously (dapper - feisty)

but this time the /mnt/xxx mounted drives are showing up on the desktop, previously as far as i was aware /media/xx showed up on the desktop but the /mnt/xxx did not

they are not showing up as just the name either they are actually showing up as 
/mnt/storage1
/mnt/storage2
etc

ive umounted and mounted a couple of times each time they reappear on the desktop

any tips?

thanks

chey

**_fstab_**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9e024a1c-b879-4ef7-bdcf-43b05d832673 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc1
UUID=6be9bf39-9dcd-4962-960d-583af9c6de7d /home           ext3    defaults        0       0
# /dev/hda3
UUID=8ea6983f-b364-4df0-9856-7a19b4cea678 /mnt/storage4     ext3    defaults        0       0
# /dev/sda1
UUID=037cda85-d5c4-4222-8a0e-23abd970672f /mnt/storage1     ext3    defaults        0       0
# /dev/sdb1
UUID=8eedc1e2-7067-40b1-a5e0-bf300bf93771 /mnt/storage2     ext3    defaults        0       0
# /dev/sdc2
UUID=65bd9978-f6f9-4064-b3c3-f5ea4cca4471 /mnt/storage3     ext3    defaults        0       0
# /dev/hda2
UUID=f8b4d31f-e6c4-4331-85bf-b8aae6ca167c none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by mad chey on 2007-10-15
scratch that, woke up this morning turned pc on and they are gone, and are as they should be, im defo confused tho as i did a couple of restarts last night after installing my nvidia drivers

---

