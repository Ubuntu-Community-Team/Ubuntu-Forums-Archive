---
title: "no sub mouse"
date: 2006-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by johnwren on 2006-05-13
I've done a clean install of 5.10 on an AMD Athlon 3000+ on a ASUS A8N-E mobo with a NVIDIA GeForce 6600 . I've got X going using the vesa driver, but can't use my usb mouse.  I see the mouse usling lsusb, but X apparently doesn't see or know about it.  If I plug in a PS2 port mouse, everything is fine.  

Can anyone point me in the right direction to get my usb mouse working?

---

### Post by dermotti on 2006-05-13
hmmm, you tried running **sudo dpkg-reconfigure xserver-xorg** ? There should be an option for usb mouse in there.

---

### Post by johnwren on 2006-05-13
Thanks for your prompt reply.  Unfortunately I think the problem is deeper than just xorg.config.  When I start up, a dmesg | grep usb shows:
[   27.469474] usbcore: registered new driver usbfs
[   27.469492] usbcore: registered new driver hub
[   35.324137] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   35.609761] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   35.899383] usb 1-3: new full speed USB device using ohci_hcd and address 4
[   36.924334] usbcore: registered new driver hiddev
[   36.934458] input**: USB HID v1.10 Mouse [KYE WebScroll Eye] on usb-0000:00:02.0-1**
[   36.934467] usbcore: registered new driver usbhid
[   36.934470] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   67.521033] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[   67.541323] usbcore: registered new driver usblp
[   67.541328] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

and this is confirmed by lsusb which shows:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem
Bus 001 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 002: ID 0458:001a KYE Systems Corp. (Mouse Systems) Genius WebScroll+
Bus 001 Device 001: ID 0000:0000  

And, there is a device /dev/input/mice (major minor codes 13 64), but when I cat /dev/input/mice and move the usb mouse, I see nothing.  If I move the PS2 port mouse I see the usual binary strings.

If I remove the usb plug from the mouse, and then do a dmesg |tail  I get:
[  106.475896] eth0: no IPv6 routers present
[  488.462050] usb 1-1: USB disconnect, address 2
[  513.606061] usb 1-1: new low speed USB device using ohci_hcd and address 5
[  525.066035] usb 1-1: device not accepting address 5, error -110
[  525.149924] usb 1-1: new low speed USB device using ohci_hcd and address 6
[  536.609898] usb 1-1: device not accepting address 6, error -110
[  536.688794] usb 1-1: new low speed USB device using ohci_hcd and address 7
[  547.077173] usb 1-1: device not accepting address 7, error -110
[  547.155070] usb 1-1: new low speed USB device using ohci_hcd and address 8
[  557.543449] usb 1-1: device not accepting address 8, error -110

Something seems very wrong with the usb handling.  This is as far as I can go with the limited knowledge I have.  Can anybody help?
Thanks,
John

---

