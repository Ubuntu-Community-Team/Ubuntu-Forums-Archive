---
title: "What USB WLAN adapters do work?"
date: 2006-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Laryllan on 2006-12-06
Moin!

I am using the 64bit version of Ubuntu. So I tried to find an USB WLAN stick with 64bit support. I found one,with open source drivers from the manufacturer, an alternate driver project and 64bit Windows drivers.

After all, very good chances to make it work.

But: it only works for few minutes. I don't want to explain for now, just ask this question:

**Is there anyone out there who uses Ubuntu (Edgy) 64bit with an WLAN USB stick that works? Which one?**

I think this question is in the best interest of many users, maybe we can gather some information about working USB WLAN.

---

### Post by Azakus on 2006-12-06
Most USB cards based on the Prism chipset will work through the linux-wlan-ng drivers. Most Atheros cards will work through the madwifi drivers pre-installed. Anything on [this list]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz") can work with the linux-wlan-ng drivers. Search through it for a USB one you feel comfortable with (there are a few D-Link, Buffalo, and Linksys ones).

---

### Post by Laryllan on 2006-12-07
Thank you! :) 

Think I'll go for a Netgear MA111. Does anyone actually use this stick /w 64bit Linux?

---

### Post by Laryllan on 2006-12-07
No, I won't. It's a 11 Mbit model... :( 

This list seems to be very outdated.

---

### Post by Azakus on 2006-12-07
Yes. It is circa 2004. There are some 802.11g models on it though.

---

### Post by FrodoB on 2006-12-08
It should be noted that mAdWiFi does not support USB devices, so do not buy Atheros chips in USB devices unless you just want to use ndiswrapper.

---

