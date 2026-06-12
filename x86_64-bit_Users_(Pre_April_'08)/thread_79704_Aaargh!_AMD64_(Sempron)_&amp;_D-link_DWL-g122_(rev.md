---
title: "Aaargh! AMD64 (Sempron) &amp; D-link DWL-g122 (rev: b1) wireless lan problem"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by lupine_nickt on 2005-10-20
HIyas,

Another poor soul having trouble with wireless networking, lol. My USB wlan device is the one mentioned above, and it works fine with the CD-provided NT/XP drivers in 5.10 (upgraded from 5.04 - but I've only ever done the wireless in 5.10) with a 32-bit kernel (2.6.12-9-k7). I've installed a 64-bit distro of ubuntu (same kernel version), to go with my 2500+ AMD64 :), and I simply can't get it working :(. ndiswrapper refuses to work with the 32-bit drivers (I suppose that's a bit of a no-brainer, really), and D-link don't provide WinXP-64 drivers for the device, as far as I can see. The card seems to be based on a RT2500 / 2570 chipset, but when I try other Windows drivers under ndiswrapper (I've tried drivers at [http://ralink.rapla.net/](http://ralink.rapla.net/)) -- RT2500USBV2.0.3.0x64.zip, and the x64 drivers in IS_STA_7x_D73-1.0.0.0_D2500USB-2.0.4.0_RU-1.0.10.0_100605_1.0.2.0.exe (loadndisdriver fails with errorcode 9, and leaves a message in syslog relating to a problem with kernel paging) , and I've also tried compiling RT25USB-SRC-V2.0.6.0.tar.gz -- unsuccessfully, and I don't have a clue how to get it working, lol.

The exact model details:- V/PID is 2001:3C00. Hardware is rt2500usb/rt2570 (means the same thing, I think). So... anyone got any ideas? A working driver for ndiswrapper in 64-bit  mode would be great :). I'm getting desperate now, so I'm considering trying to use ural, and the rt2x00 open-source driver. Can't see myself succeeding with either of those, though... but anything's worth a try, lol.

xF,

...Nick

---

### Post by lupine_nickt on 2005-10-20
w00t! Cruising happily along with the rt2570 driver (1.1.0-b1). I don't know if WEP or anything like that is working, though. Bye-bye ndiswrapper :). 

What I did: simple enough :). Downloaded the driver mentioned above, unzipped it, and typed 'make', 'make install'. (note: I did all this in root terminal; you might need to sudo those steps if you're logged on as a normal user). Then I ran 'cp rt2570.ko /lib64/modules/2.6.12-9-amd64-k8/kernel/drivers/usb/net' (as it didn't seem to copy by default), then ran 'modprobe rt2570', then 'lsmod' to confirm it was loaded. From there, you can set up the basics using net-admin. Don't have a clue about whether WEP/WPA works, though... probably :)

xF,

...Nick

---

