---
title: "device path to OpenFirmWare path"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by abz on 2005-11-03
How to convert linux device (like /dev/sdc) to OpenFirmWare path (like usb0/disk0).
I wish to boot from Memorex 1g USB stick with my G5 2mhz.
(Ununtu is installed and work perfectly)
The stick is partionned and all files (from boot.img.gz) are inside the partition 2.
The stick flash at startup so the device is recongnized

At boot time I use the OF command usb0/disk:2,\\tbxi but the mac doesn boot.

I also try ht@0,f2000000/pci@4/usb@b/disk@2,\\tbxi and other flavor of OF path
but the better I can get is a screen that show a circle with an oblique line.

Any help will be appreciate.

Thank you

---

### Post by jdp on 2005-11-03
I'm not sure which model/revision but I seem to recall that Apple has disabled USB booting on new Macs.

---

