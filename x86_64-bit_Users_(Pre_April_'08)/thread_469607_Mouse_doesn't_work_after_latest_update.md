---
title: "Mouse doesn't work after latest update"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by joe_bruin on 2007-06-10
I updated my system this morning (Jun-09-2006, 14:00PST) and on reboot, the mouse no longer works.  Unplugging the USB cable and plugging it back in makes the mouse work correctly.  This is definitely repeatable.

Here's the relevant dmesg output:
```
[   33.618748] usb 2-2: new low speed USB device using ohci_hcd and address 2
[   33.823754] usb 2-2: configuration #1 chosen from 1 choice
[...]
[   42.246501] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input3
[   42.246616] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2
[   42.246637] usbcore: registered new interface driver usbhid
[   42.246641] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
```

after unplugging and then replugging the mouse:
```
[   88.401429] usb 2-2: USB disconnect, address 2
[   92.320670] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   92.431709] usb 2-2: configuration #1 chosen from 1 choice
[   92.436721] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input6
[   92.436774] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2
```

Anyone seen this before or know what's up?  This mouse has been problem-free since breezy.

---

### Post by FlowingSnake on 2007-09-11
exact same problem anyone with any ideas?
Sorry for bringing an old thread back ...but it was the yougest one i found.

---

### Post by Cappy on 2007-09-11
Try this:
```
gksudo gedit /etc/modules
```

and add a new line on the end that reads
```
usbhid
```

---

