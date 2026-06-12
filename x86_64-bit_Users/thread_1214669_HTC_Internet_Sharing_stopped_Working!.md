---
title: "HTC Internet Sharing stopped Working!"
date: 2009-07-16
forum: x86 64-bit Users
---

### Post by JouPA on 2009-07-16
Hi Everyone 

I use my HTC to connect to the Internet using the Internet Sharing option on my HTC. It used to work perfectly, but somewhere (maybe after an update) it stopped working without any errors. I made sure the cable is still operational and that internet sharing works fine on other notebooks. I have the following outputs that might help with an analysis...

It used to show a new RNDIS adapter in networking after i plugged the phone in, but that is not popping up anymore

HELP PLEASE!!!! **  By the way - I posted it here since i am on 64bit with 9.04** - Please move if it is teh wrong thread!

DMESG Output
[10211.556059] rndis0: unregister 'rndis_host' usb-0000:00:1d.1-1, RNDIS device (SynCE patched)
[16704.048092] usb 6-1: new full speed USB device using uhci_hcd and address 4
[16704.219689] usb 6-1: configuration #1 chosen from 1 choice
[16705.969897] rndis0: register 'rndis_host' at usb-0000:00:1d.1-1, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
[16716.092081] rndis0: no IPv6 routers present

LSUSB Output
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 0bb4:0b0b High Tech Computer Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by JouPA on 2009-07-23
Hi Everyone.

Finaly i got an error from DMESG

[ 8031.608048] usb 6-1: new full speed USB device using uhci_hcd and address 2
[ 8031.771841] usb 6-1: configuration #1 chosen from 1 choice
[ 8031.886994] rndis_wlan: Unknown symbol rndis_tx_fixup
[ 8031.887307] rndis_wlan: Unknown symbol rndis_unbind
[ 8031.888161] rndis_wlan: Unknown symbol rndis_status
[ 8031.888550] rndis_wlan: Unknown symbol rndis_command
[ 8031.888783] rndis_wlan: Unknown symbol generic_rndis_bind
[ 8031.889550] rndis_wlan: Unknown symbol rndis_rx_fixup
[ 8031.909042] usbcore: registered new interface driver cdc_ether
**[ 8031.920196] rndis_host 6-1:1.0: RNDIS init failed, -71**
**[ 8031.920224] rndis_host: probe of 6-1:1.0 failed with error -71**
[ 8031.920261] usbcore: registered new interface driver rndis_host


Can someone help with this?

Thanx a million

---

### Post by JouPA on 2009-08-31
Hi Everyone

Any ideas?

Thanx

---

