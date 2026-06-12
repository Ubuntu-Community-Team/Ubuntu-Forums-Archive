---
title: "usb system broken? problem"
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by johnwren on 2006-05-14
I have done a clean install of 5.10 (x86_64)) on my Athlon 64 with an ASUS A8N-E mobo.  Something is very wrong with the entire usb system.  On startup, devices are recognized, things look good.   When I start up, a dmesg | grep usb shows:
[ 27.469474] usbcore: registered new driver usbfs
[ 27.469492] usbcore: registered new driver hub
[ 35.324137] usb 1-1: new low speed USB device using ohci_hcd and address 2
[ 35.609761] usb 1-2: new full speed USB device using ohci_hcd and address 3
[ 35.899383] usb 1-3: new full speed USB device using ohci_hcd and address 4
[ 36.924334] usbcore: registered new driver hiddev
[ 36.934458] input: USB HID v1.10 Mouse [KYE WebScroll Eye] on usb-0000:00:02.0-1
[ 36.934467] usbcore: registered new driver usbhid
[ 36.934470] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[ 67.521033] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[ 67.541323] usbcore: registered new driver usblp
[ 67.541328] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

and this is confirmed by lsusb which shows:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem
Bus 001 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 002: ID 0458:001a KYE Systems Corp. (Mouse Systems) Genius WebScroll+
Bus 001 Device 001: ID 0000:0000

I have problems with all devices, including usb mouse and printer.  As for the mouse, there is a device /dev/input/mice (major minor codes 13 64), but when I cat /dev/input/mice and move the usb mouse, I see nothing. If I move the PS2 port mouse I see the usual binary strings.

If I remove the usb plug from the mouse, and then do a dmesg |tail I get:
[ 106.475896] eth0: no IPv6 routers present
[ 488.462050] usb 1-1: USB disconnect, address 2
[ 513.606061] usb 1-1: new low speed USB device using ohci_hcd and address 5
[ 525.066035] usb 1-1: device not accepting address 5, error -110
[ 525.149924] usb 1-1: new low speed USB device using ohci_hcd and address 6
[ 536.609898] usb 1-1: device not accepting address 6, error -110
[ 536.688794] usb 1-1: new low speed USB device using ohci_hcd and address 7
[ 547.077173] usb 1-1: device not accepting address 7, error -110
[ 547.155070] usb 1-1: new low speed USB device using ohci_hcd and address 8
[ 557.543449] usb 1-1: device not accepting address 8, error -110

Similarly, if I unplug the usb printer (epson c67) and then plug it back in, dmesg shows:

[   91.454071] IPv6 over IPv4 tunneling driver
[  101.515091] eth0: no IPv6 routers present
[  140.041596] usb 1-2: new full speed USB device using ohci_hcd and address 4
[  151.501569] usb 1-2: device not accepting address 4, error -110
[  151.584460] usb 1-2: new full speed USB device using ohci_hcd and address 5
[  163.044434] usb 1-2: device not accepting address 5, error -110
[  163.122331] usb 1-2: new full speed USB device using ohci_hcd and address 6
[  173.511710] usb 1-2: device not accepting address 6, error -110
[  173.589606] usb 1-2: new full speed USB device using ohci_hcd and address 7
[  183.977986] usb 1-2: device not accepting address 7, error -110

Something seems very wrong with the usb handling. This is as far as I can go with the limited knowledge I have. Can anybody help?
Thanks,
John

---

### Post by johnwren on 2006-05-14
Doing some research on my own, the linux usb faq ([www.linux-usb.org](www.linux-usb.org)) suggests that there may be a problem with the PCI setup "that's preventing your USB host controller from getting hardware interrupts".  I'm in winXP now, because the lack of usb support means I can't use my usb modem under linux.  I'll go off and check this out, looking in /proc/interrupts to see if it's happening.

In the meantime, if anyone has a suggest, perhaps a boot parameter to disable ACPI?  [except I actually don't know how to do this in grub without doing more research].  The ASUS motherboard (A8N-E) seems to have an OK reputation in linux, but perhaps I have a bios setting wrong?  

Any ideas/suggestions gratefully accepted.
John

---

### Post by johnwren on 2006-05-14
It appears that interrupts are being received by the usb system.  Attached is a copy of /proc/interrupts before unplugging and then plugging back in my three usb ports (printer, mouse and modem); followed by a look at it after plugging everything back in.  Dmesg shows some unusual things, lots of ACPI PCI interrupts off, and even some invalid IRQ messages -- I'll post this on the hardware forum, but I'll also attach it here.  If anyone could help me interrpret this, I'd be really grateful.
           CPU0       
  0:     339104    IO-APIC-edge  timer
  1:        658    IO-APIC-edge  i8042
  8:          0    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  acpi
 10:          0    IO-APIC-edge  MPU401 UART
 12:        128    IO-APIC-edge  i8042
 14:       9585    IO-APIC-edge  ide0
 15:       2702    IO-APIC-edge  ide1
 16:          2   IO-APIC-level  ohci1394
 20:          4   IO-APIC-level  ehci_hcd:usb2
 21:         71   IO-APIC-level  ohci_hcd:usb1
 22:       1032   IO-APIC-level  libata, NVidia CK804
 23:      29792   IO-APIC-level  libata, eth0
NMI:        102 
LOC:     338532 
ERR:          0
MIS:          0

after plugging everything back in...

          CPU0       
  0:     715225    IO-APIC-edge  timer
  1:       1215    IO-APIC-edge  i8042
  8:          0    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  acpi
 10:          0    IO-APIC-edge  MPU401 UART
 12:        220    IO-APIC-edge  i8042
 14:      10178    IO-APIC-edge  ide0
 15:       6068    IO-APIC-edge  ide1
 16:          2   IO-APIC-level  ohci1394
 20:         10   IO-APIC-level  ehci_hcd:usb2
 21:        131   IO-APIC-level  ohci_hcd:usb1
 22:       1032   IO-APIC-level  libata, NVidia CK804
 23:      67620   IO-APIC-level  libata, eth0
NMI:        111 
LOC:     714611 
ERR:          0
MIS:          0

---

### Post by isabellf on 2006-11-03
I got a simillar issue when the "AI N.O.S" overclock was enabled in the CMOS setup.

---

