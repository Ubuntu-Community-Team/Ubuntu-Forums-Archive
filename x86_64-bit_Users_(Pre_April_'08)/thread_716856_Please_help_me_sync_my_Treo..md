---
title: "Please help me sync my Treo."
date: 2008-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krovas on 2008-03-06
I have a Treo 90 running PalmOS 4.1. I'm unable to sync with either the Gnome pilot app or jpilot. I've been tailing /var/log/messages, but it's not telling me what device the Treo gets asigned to when I plug it in. It's definitely not /dev/pilot. All I get is this:

Mar  6 11:36:37 thievesguild kernel: [  993.615278] usb 2-2: new full speed USB device using ohci_hcd and address 15

Mar  6 11:36:37 thievesguild kernel: [  993.839278] usb 2-2: configuration #1 chosen from 1 choice


Jpilot reports:

```

pi_bind error: /dev/pilot No such file or directory

Check your serial port and settings

Exiting with status SYNC_ERROR_BIND

Finished:
```


I've played with all the Gnome Pilot settings to no avail. I'd rather sync with Evolution, but I'll use jpilot if I have to. I'll take just about anything at the moment.

---

