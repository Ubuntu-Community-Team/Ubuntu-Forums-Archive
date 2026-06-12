---
title: "[SOLVED] PSP USB problems"
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by stringkarma on 2008-01-17
In moving to my new multicore 64 bit ubuntu box I have found that my psp (which connects to my old box) won't connect. lsmod shows that I have all the correct modules installed and dmesg tells me:

[ 1658.600189] usb 8-4: device not accepting address 62, error -71
[ 1658.871493] usb 8-6: new high speed USB device using ehci_hcd and address 63
[ 1658.989708] usb 8-6: device descriptor read/64, error -71
[ 1659.206619] usb 8-6: device descriptor read/64, error -71
[ 1659.422064] usb 8-6: new high speed USB device using ehci_hcd and address 64
[ 1659.536300] usb 8-6: device descriptor read/64, error -71
[ 1659.753222] usb 8-6: device descriptor read/64, error -71
[ 1659.968666] usb 8-6: new high speed USB device using ehci_hcd and address 65
[ 1660.378129] usb 8-6: device not accepting address 65, error -71
[ 1660.489846] usb 8-6: new high speed USB device using ehci_hcd and address 66

I have seen something similar on a 64 bit laptop but it was fixed by passing irqfixup at boot.

has anyone else had similar problems or can anyone help?
Thanks

---

### Post by homerh on 2008-01-17
Stringkarma  ,i a bug in the usb 2  driver on some usb hubs 

all you need to do is 
> sudo rmmod ehci_hcd 
and reconnect your psp ,it will now work at usb 1 speed

---

### Post by stringkarma on 2008-01-23
I had actually seen this somewhere else and tried it, with no success (I really didn't want to lose USB2 speed either). It turned out that for whatever reason the front ports wont give it an address whereas the USB ports in the rear of the computer seem to have no problem. While this isn't perhaps an adequate answer to the problem, it works, and I'm not going to complain.

---

### Post by stringkarma on 2008-04-29
Turns out that the front panel usb headers were improperly installed. Now that that is fixed all is fine.

---

