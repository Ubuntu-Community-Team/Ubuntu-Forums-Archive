---
title: "Network manager or hal bug?"
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by stephenb on 2007-05-30
I've been able to solve most problems with Ubuntu on my own but the following has got me stumped. It's in the annoying category more than anything else because everything still runs, but I wonder what it's all about. 

I get this in syslog every time I start using the PC again after the screensaver has been on. I've read of other people with similar messages concerning NM and Hal but none associated with mouse and keyboard. It only started happening after an upgrade, I think.

May 31 06:21:38 server1 kernel: [32990.179095] usb 6-1: new high speed USB device using ehci_hcd and address 5
May 31 06:21:39 server1 kernel: [32990.311467] usb 6-1: configuration #1 chosen from 1 choice
May 31 06:21:39 server1 kernel: [32990.311528] hub 6-1:1.0: USB hub found
May 31 06:21:39 server1 kernel: [32990.311629] hub 6-1:1.0: 4 ports detected
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.080406] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.145562] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial_if0'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.189095] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial_usbraw'). 
May 31 06:21:39 server1 kernel: [32990.615849] usb 6-1.1: new low speed USB device using ehci_hcd and address 6
May 31 06:21:39 server1 kernel: [32990.741536] usb 6-1.1: configuration #1 chosen from 1 choice
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.511441] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5af_802_noserial'). 
May 31 06:21:39 server1 kernel: [32990.750709] input:   USB Keyboard as /class/input/input7
May 31 06:21:39 server1 kernel: [32990.750753] input: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1a.7-1.1
May 31 06:21:39 server1 kernel: [32990.765636] input:   USB Keyboard as /class/input/input8
May 31 06:21:39 server1 kernel: [32990.765683] input: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1a.7-1.1
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.553735] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5af_802_noserial_if0'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.584533] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5af_802_noserial_if1'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.588490] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5af_802_noserial_if0_logicaldev_input'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.614104] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5af_802_noserial_usbraw'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.620513] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5af_802_noserial_if1_logicaldev_input'). 
May 31 06:21:39 server1 kernel: [32990.964687] usb 6-1.2: new low speed USB device using ehci_hcd and address 7
May 31 06:21:39 server1 kernel: [32991.059879] usb 6-1.2: configuration #1 chosen from 1 choice
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.828222] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_461_4d15_noserial'). 
May 31 06:21:39 server1 kernel: [32991.061804] input: USB Optical Mouse as /class/input/input9
May 31 06:21:39 server1 kernel: [32991.061881] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.7-1.2
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.876002] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_461_4d15_noserial_if0'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.886861] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_461_4d15_noserial_usbraw'). 
May 31 06:21:39 server1 NetworkManager: <debug info>^I[1180560099.926028] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_461_4d15_noserial_if0_logicaldev_input'). 

Is it anything to worry about? Does anyone know of a fix?

Cheers.

---

### Post by krismatth3 on 2007-05-31
Fix for what? It's outputting debug information. Nothing is wrong. Note that they each different interfaces (the 'hal udi' here). Sometimes USB devices do more than is readily apparent (or have more than one interface to do the thing they do).

---

### Post by stephenb on 2007-05-31
OK, I see. Thanks for the reply! It's put my mind at ease.

I had suspected there wasn't a problem because I haven't had any major problems with Ubuntu so far. But I was a little concerned to see Network Manager having something to do with the mouse and keyboard, and to see the hub, mouse and keyboard apparently reconnected or readded occasionally. Because I don't know much about it, I didn't understand why this was happening. I'll try to do so when I have time. 

Thanks again.

---

### Post by Drone4four on 2007-12-19
My similar NetworkManager errors prevent my Ubuntu Gutsy from booting.  [url= 
http://ubuntuforums.org/showthread.php?p=3979769#post3979769]Here[/url] is the forum post.

---

