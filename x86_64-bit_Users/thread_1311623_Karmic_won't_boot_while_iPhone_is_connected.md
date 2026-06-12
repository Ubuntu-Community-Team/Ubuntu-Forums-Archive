---
title: "Karmic won't boot while iPhone is connected"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by 01000111 on 2009-11-02
I was running Jaunty and have upgraded to Karmic.  Everything works fine unless the iPhone is connected during the boot.  If I connect it after the boot completes, it works fine... I can access the pics via Nautilus and sync with iTunes in WinXP in VirtualBox.

Attached are the screenshots (sorry for the poor quality) of what happens when I boot with the iPhone connected, as well as what happens when I unplug the iPhone after the boot had hanged (hung?).  I've also attached a dmesg dump from a normal boot.

Any thoughts??

01000111

<edit>
since the screenshots are so bad, here's the text of what's on the screen when the iPhone is connected and the boot hangs:

[    1.614107] usb 2-2: configuration #1 chosen from 1 choice
[    1.626852] usbcore: registered new interface driver hiddev
[    1.634346] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input3
[    1.634481] generic-usb 0003:0A81:0205.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-2/input0
[    1.646392] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input4
[    1.646522] generic-usb 0003:0A81:0205.0002: input,hidraw1: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-2/input1
[    1.646610] usbcore: registered new interface driver usbhid
[    1.646671] usbhid: v2.6:USB HID core driver
[    1.740901] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1a:a0:6d:65:2c
[    1.740977] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.982520] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    2.264119] usb 2-4: configuration #1 chosen from 1 choice
[    2.450024] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    2.676112] usb 3-2: configuration #1 chosen from 1 choice

Apparently when the boot works, there's a few extra lines:

[    1.982520] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    2.264119] usb 2-4: configuration #1 chosen from 1 choice
[    2.450024] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    2.647768] [COLOR="Lime"]xor: automatically using best checksumming function: generic_sse[/COLOR]
[    2.676112] usb 3-2: configuration #1 chosen from 1 choice
[    2.692508] [COLOR="Lime"]   generic_sse:  8170.400 MB/sec[/COLOR]
[    2.692511] [COLOR="Lime"]xor: using function: generic_sse (8170.400 MB/sec)[/COLOR]
[    2.695032] [COLOR="Lime"]device-mapper: dm-raid45: initialized v0.2594b[/COLOR]

---

### Post by 01000111 on 2009-11-04
bump!

---

