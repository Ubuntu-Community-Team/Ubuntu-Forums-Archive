---
title: "Mild Problem - Wireless Adapter"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Disabled20240622 on 2006-04-08
How can I get a Broadcom WLAN module to be detected in Ubuntu?

---

### Post by BjornHaland on 2006-04-10
Try and just activate it:

System->Administration->Networking

Check the 'Properties' box for 'Wireless connection'

Check the box 'Enable this connection'

Choose 'Network name (ESSID)': just type 'ANY'

Key type: Hexadecimal

WEP key: blank

Connection Settings: DHCP

Press 'OK'

Then mark the 'Wireless connection' tab and check 'Activate'

----------

This is what I did after taking trying the hard way, failing.
It was much easier than I expected, but it may or may not work with your card.

Good luck!

---

### Post by Disabled20240622 on 2006-04-10
I'm asking how to install it because It's not in that list. AKA not installed.

I think I've found the drivers myself.

---

### Post by Disabled20240622 on 2006-04-10
The driver I've found is at madwifi.org.

I'm sure it's for my WLAN module.

But step1 of the begginners installation guide didn't work




I have never managed to install anything to any distro of linux sucessfully. But I can build a PC and program in VB. Bearing this in mind could someone help me install this?

---

### Post by BjornHaland on 2006-04-10
Ok, I just wanted to help.

I tried the hard way first and found out there was an easier way, as explained above. The easy way even worked with a fresh ubuntu install. So.. I figured I'd share what I found out, and I did in no way intend to suggest you were a beginner or something by explaining the steps to do it, hope you didn't take it that way. Hope you find out!

---

### Post by BjornHaland on 2006-04-12
Oh, by the way.. I've noticed (like just now, when I reinstalled Dapper) that the wlan0 device won't show up in that list if you've got it plugged in to 'the wrong' usb port. As soon as I switch usb port, the device shows up.

---

