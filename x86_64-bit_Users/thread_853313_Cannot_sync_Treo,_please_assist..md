---
title: "Cannot sync Treo, please assist."
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by Krovas on 2008-07-08
I have an old Treo 90 I used to sync with Feisty, but Hardy is just not having any. I have the visor module load on boot from /etc/modules. Tailing /var/log/messages as the Treo is plugged in and a HotSync attempted results in the following:

```
Jul  8 12:57:19 thievesguild kernel: [  433.869967] usb 1-1: new full speed USB device using ohci_hcd and address 4

Jul  8 12:57:19 thievesguild kernel: [  434.093976] usb 1-1: configuration #1 chosen from 1 choice

Jul  8 12:57:19 thievesguild kernel: [  434.109839] visor: probe of 1-1:1.0 failed with error -5

```

No device anything like /pilot or /ttyUSBxxx is ever created as per the rule in /etc/udev/rules.d/60-symlinks.rules. I am at the end of my tether here, and would appreciate assistance.

---

### Post by bunnyhugh on 2008-07-08
> **Krovas said:**
> I have an old Treo 90 I used to sync with Feisty, but Hardy is just not having any. I have the visor module load on boot from /etc/modules. Tailing /var/log/messages as the Treo is plugged in and a HotSync attempted results in the following:

```
Jul  8 12:57:19 thievesguild kernel: [  433.869967] usb 1-1: new full speed USB device using ohci_hcd and address 4

Jul  8 12:57:19 thievesguild kernel: [  434.093976] usb 1-1: configuration #1 chosen from 1 choice

Jul  8 12:57:19 thievesguild kernel: [  434.109839] visor: probe of 1-1:1.0 failed with error -5

```

No device anything like /pilot or /ttyUSBxxx is ever created as per the rule in /etc/udev/rules.d/60-symlinks.rules. I am at the end of my tether here, and would appreciate assistance.


Hi,

I found this link which I used to set up the synching of my tungsten E2 in hardy. I know it's for bluetooth but maybe it will give you some pointers

[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

Rgds

---

### Post by Krovas on 2008-07-08
Oh yes, I forgot to mention that I'm attempting to hotsync via the usb cable only. My treo is too old for Bluetooth.

---

### Post by mmolitor on 2008-07-09
In J-Pilot Preferences, specify usb:any as Serial Port (instead of /dev/pilot).

---

### Post by Krovas on 2008-07-10
> **mmolitor said:**
> In J-Pilot Preferences, specify usb:any as Serial Port (instead of /dev/pilot).

Tried that. No joy.

---

