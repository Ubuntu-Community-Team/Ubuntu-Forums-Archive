---
title: "WINE 2.8 breaks serial ports"
date: 2017-05-13
forum: Wine
---

### Post by rattskjelke on 2017-05-13
In the past I never had problems using a USB serial port dongle in WINE.
The windows programs were always happy with a symbolic link from /dev/ttyUSB0 to ~/.wine/dosdevices/com1.

Today I discovered that WINE 2.8 changed the way serial ports work.
Now WINE automatically creates 32 links for the ttyS devices to com1-com32 in the ~/.wine/dosdevices folder.
When I plug in the dongle it makes ttyUSB0 com33.
Many windows programs don't allow com ports with numbers higher than 8 or 16.
I tried deleting the com1 and comm33 links and making a new com1 link to ttyUSB0 but that doesn't work for some reason.
I tried deleting all the com port links in the ~/.wine/dosdevices folder but they just get created again.

Does anybody know how to disable this or force a device to use a specific com port number and not change?

This computer has no real serial or parallel ports. Is there a way to force Linux to only have one (or 8) serial ports?

I am using Lubuntu 17.04.

---

### Post by rattskjelke on 2017-05-15
I found out how to fix it.
[https://wiki.winehq.org/index.php?title=Wine_User%27s_Guide&oldid=2519#Serial_and_Parallel_Ports](https://wiki.winehq.org/index.php?title=Wine_User%27s_Guide&oldid=2519#Serial_and_Parallel_Ports)

---

### Post by blargblarg on 2017-05-20
Thank you for finding the instructions.  Saved me some grief.  I do wonder what has been gained by making such a change.  I don't think I've used any Windows software that can handle more than 32 comports, many stop at COM9.  It's certainly not any more convenient, having to edit the registry, and at the same time it breaks the old method badly!  Why break the previous method?  It can't be complete.

---

