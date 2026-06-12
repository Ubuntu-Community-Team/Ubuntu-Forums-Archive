---
title: "wlan0/eth1 question"
date: 2006-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by brainfry on 2006-10-21
Hi people. This is more of an annoyance than a problem. I'm using Dapper 64 on an HP dv5046ea with the bcm4318 [air force 1] wireless card. It works fine using WEP (still not got my head round wpa_supplicant) and loading the 64 bit drivers with ndiswrapper (using it now while writing this) My question is has anyone had the situation where the name of the wireless connection changes from reboot to reboot? At the moment it's listed as wlan0 in iwconfig. however, it regularly changes to eth1 and then back again each time I boot up. Being a laptop I don't leave it on all the time like I used to with my desktop so I'm wondering what I can do to make it pick a name and stick with it. I only noticed when I started the firestarter gui and it said there was no connection. I can configure it in the firestarter prefs and then the firewall will start. It doesn't stop me using wireless but it is a bit puzzling.
Thanks in advance, Steve

---

### Post by kuja on 2006-10-21
eth1 sounds like a regular wired connection, though, you're completely wireless I'm assuming, right? Is it just changing the name? If not, you might be able to disable one of them (ie eth1) and see if things still work. Aside from this, what does the name matter anyhow?

---

### Post by brainfry on 2006-10-22
Aside from having to keep reconfiguring firestarter gui, it doesn't. Like I said, it's more of an annoyance than a problem, I can live with it. Just upgraded to edgy and now my card isn't even listed in network settings even though ndiswrapper says the driver is loaded and hardware is present. Heh, back to the drawing board!
Does this stuff keep your brain sharp or what?!
Cheers

---

### Post by Titus A Duxass on 2006-10-22
If you only use wireless, try disabling the eth1 in BIOS.  That way it will stay as wlan0 - least it does for me.

---

### Post by brainfry on 2006-10-22
Thanks, I may give it a try at some point, may just wait a few more days for edgy to be released (26th?) and go from there.
Cheers

---

