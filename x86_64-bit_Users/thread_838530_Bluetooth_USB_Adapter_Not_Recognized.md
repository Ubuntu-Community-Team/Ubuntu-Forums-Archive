---
title: "Bluetooth USB Adapter Not Recognized"
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by rjonesx on 2008-06-23
I have attempted to install an Insignia NS-BTHDST Headset and with no luck so far. I am on an HP Pavilian dv2000 laptop (AMD64) with Hardy Heron.

lsusb shows the following, where Bus

Bus 002 Device 011: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 010: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 009: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000  

Where Bus 002 Device 011,010, and 009 are all Bluetooth USB device.

However, if I run hciconfig or hcitool, it shows nothing.

~# hciconfig scan
Can't get device info: No such device

:~# hcitool dev
Devices:

Any ideas? I would really like to get this working.

Russ

---

### Post by pixel :-) on 2008-06-26
try this forum [http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by go_beep_yourself on 2008-10-30
Hey you guys! Got it working?

---

### Post by rjonesx on 2008-10-31
nope. Just upgraded to Ibex as well, and still no luck.

---

