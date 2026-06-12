---
title: "[SOLVED] Parallel Port on Optiplex 745"
date: 2007-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by razeshkale on 2007-07-05
Hi
I couldnot get work around Parallel port on 745 desktop
using 7,04 Server 64 bit
does anyone has any comments on this
port is enable in BIOS

Cheers

---

### Post by razeshkale on 2007-07-06
Even now i m trying to get around with USB Dongle its Hard Lock
I can see USB device in list but i cant activate as i try to select by clicking on it doesnt make any diffrence to USB device?
I think there is something patch for Linux for using Hard lock keys Devices.
But not sure
as My host is Linux -Ubuntu 64 bit host is XP and could not get work around both port
USB as well Parallel one

Any other USB devices like Stick n all works fine with selecting usb device
in hard lock case i can see the attached device with Vmware but not selectable as check box stays blank even on clicking on it

Anyone has any comments!!!
Cheers

---

### Post by razeshkale on 2007-07-06
We fix that
We have to turn off Print Port Services
CUPSYS and HPLIP from System>Administration>Services

then
follow those commands@

ls -l /dev/parport*
sudo chmod 666 /dev/parport0
sudo rmmod lp
lsmod | grep lp

and you are done!

---

