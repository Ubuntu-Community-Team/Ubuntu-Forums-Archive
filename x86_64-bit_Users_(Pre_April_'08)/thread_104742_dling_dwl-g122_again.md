---
title: "dling dwl-g122 again"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jwhitt on 2005-12-16
ok im having issues getting a dlink dwl-g122 usb stick to work, my current setup is 12' ibook g3 800 with a d-link dwl-g122 h/w Ver B1, im assuming it uses the rt2570 driver so i download that driver make, make install then when i go to modprobe it or insmod it i get an error Fatal: Module not found, ive copied the rt2570.ko file from the unpack directory and placed it in both the /lib/modules/kernel/2.6.12-9-powerpc/kernel/drivers/net/wireless and /drivers/usb/net directories..... now ive been told that the latest driver release isnt compatable with the 2.6.12 kernel so i havent tried upgrading that yet any ideas anyone with a similar setup get this working etc?

---

### Post by jwhitt on 2005-12-16
ok ive done a little more looking around and found out that make install installs the rt2570.ko file to /lib/modules/2.6.12/extras, so i cp'd it to /lib/modules/2.6.12-powerpc/kernel/drivers/usb/net, and /drivers/net/wireless then sudo depmod -a and sudo modprobe rt2570 and i get error inserting rt2570 (lib/modules/2.6.12-powerpc/kernel/drivers/usb/net/rt2570.ok) invalid module format


any ideas?

---

