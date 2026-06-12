---
title: "link /dev/ttyUSBx?"
date: 2014-08-22
forum: Wine
---

### Post by dave131 on 2014-08-22
newbie here.  I have a Prodigy glucose meter for my diabetes.  It can connect via USB to a program that they supply, but the program is Windows only.  I installed Wine already for some other things, so I thought I'd try this as well, even though Wine doesn't support USB.  I looked at dmesg and saw the device is at /dev/ttyUSB2 which I *think* is a serial device??  I read another thread in the Wine forum and it showed creating symbolic links for that to comx in the wine dosdevices folder.  Tried com1 - no luck.  So I just went ahead and created 3 more symbolic links for com2 thru com4 - still no luck.

I know this may not be possible, but I thought I'd try asking to see if anyone has any suggestions.  The program makes it much easier to track and graph my blood glucose levels.

Thanks.

---

### Post by dave131 on 2014-08-23
I tried the program on a friends Windows 7 PC and it still doesn't find the meter there either.  I know the meter is ok, so I'm assuming either they have a software issue or, more likely, I just don't know what the heck I'm doing ;) ;)

---

### Post by dave131 on 2014-08-25
Heck, I plug the thing in now with the same cable, etc., and it doesn't even mount - dmesg shows an error now.

---

### Post by steeldriver on 2014-08-25
Does it have its own USB-serial adapter or are you using a generic one? they're notoriously flaky in my experience (regardless of OS)

---

### Post by dave131 on 2014-08-25
There doesn't seem to be any mention of a special cable for the Prodigy I have - though my Bayer meter does require a special cable.  I *think* that it uses USB but the device is somehow "converted" via a logical link to serial in the OS.  Not sure about that, but that's the impression I get - but hey - I'm a newbie so what the heck do I know ;) ;)

I did install Windows 7 in virtual box (downloaded the Win7 from digital river, so I don't even know if it's any good or full of all kinds of things I really don't want on my PC).  Even in Windows 7 as a guest it doesn't find the device - I imagine because Ubuntu doesn't mount it either.

I have noticed a couple of things:  when I first plug the meter in to USB it says Lnk, then when I push the button on the meter it says USB and then shortly thereafter it powers off.

What's really strange to me is that the software itself, when running in Wine, seems to stop when I have finished entering the information to add myself and my device to the software.  It gets to Save, but then clicking the button does nothing and I can't go to anywhere else on the software - I just have to close the window.  The meter supposedly doesn't even need (or should be) plugged in at that point.  So besides the device problem I'm also having problems with the software (the software does work in the Windows 7 vm).

I am a newbie so this is a real mystery for me - I don't know if it stands a chance of being solved or not ;) ;)

---

### Post by dave131 on 2014-08-25
I just double checked the site for the Prodigy meter - it says it just uses a normal USB cable.  I reset things and dmesg showed it mounted again.  Then the meter turned off automatically and I haven't been able to get it mounted since.  I get these messages in the log: ```
[ 4449.188441] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4449.188446] usb 5-2: Product: USB-Serial Controller D
[ 4449.188450] usb 5-2: Manufacturer: Prolific Technology Inc. 
[ 4449.190380] pl2303 5-2:1.0: pl2303 converter detected
[ 4449.202729] usb 5-2: pl2303 converter now attached to ttyUSB2
[ 4452.988346] hub 5-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 4452.988358] usb 5-2: USB disconnect, device number 58
[ 4452.988690] pl2303 ttyUSB2: pl2303 converter now disconnected from ttyUSB2
[ 4452.988717] pl2303 5-2:1.0: device disconnected
[ 4453.228273] usb 5-2: new full-speed USB device number 59 using uhci_hcd
[ 4453.348264] usb 5-2: device descriptor read/64, error -71
[ 4453.572243] usb 5-2: device descriptor read/64, error -71
[ 4453.992274] usb 5-2: new full-speed USB device number 60 using uhci_hcd
[ 4454.112261] usb 5-2: device descriptor read/64, error -71
[ 4454.336285] usb 5-2: device descriptor read/64, error -71
[ 4454.552264] usb 5-2: new full-speed USB device number 61 using uhci_hcd
[ 4454.968237] usb 5-2: device not accepting address 61, error -71
[ 4455.080180] usb 5-2: new full-speed USB device number 62 using uhci_hcd
[ 4455.496204] usb 5-2: device not accepting address 62, error -71
[ 4455.496262] hub 5-0:1.0: unable to enumerate USB device on port 2
me@me-Studio-1735:~$ 
```

Sometimes it says "bad cable?" other times it just shows the device not accepting address error.  I *think* the PL2303 it is showing is supposed to be some kind of converter - but it must be internal to the meter.

Any and all help is appreciated.  Like I said, I'm a newbie and don't have a clue about this. ;)

---

