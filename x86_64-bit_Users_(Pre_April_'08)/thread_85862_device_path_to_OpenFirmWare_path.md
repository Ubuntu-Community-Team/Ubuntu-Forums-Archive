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

### Post by autocrosser on 2005-11-03
Have you tried to option key reboot?--This puts you in the openfirmware "chooser" & bypasses the need to create a path---

Hope this helps----

---

### Post by abz on 2005-11-04
The USB memory stick doesn't appear with the option.
The only way to boot from USB storage is OF.
I think there is a note about this in the install doc.


Thank you.

---

