---
title: "wifi and Internet access"
date: 2006-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by BenoitD on 2006-03-17
Dear all,
I'm new on Ubuntu and quite happy with it. 

My configuration :
- Ubuntu Breezy 64 bits (dual boot with XP)
- Laptop Acer Aspire 5024 WMLi (AMD Turion 64 bits)
- Broadcom card for wifi 80211.g

My problem is simple but :

- I configured correctly my Broadcom card with ndiswrapper
- I have a wlan0 active
- with iwlist wlan0 scan, I can see my network with a correct essid and no key (that's normal, I first try withou WEP/WPA key)
- network is correctly running with XP

But I have still no access to internet. [http://www.google.com](http://www.google.com) gives no return.

Do I miss something ? Can you help me ?

Thanks,

BenoitD

---

### Post by John Jason Jordan on 2006-03-17
[QUOTE=BenoitD]
- I configured correctly my Broadcom card with ndiswrapper
- I have a wlan0 active
- with iwlist wlan0 scan, I can see my network with a correct essid and no key (that's normal, I first try withou WEP/WPA key)
- network is correctly running with XP

But I have still no access to internet. [http://www.google.com](http://www.google.com) gives no return.BenoitD[/QUOTE]
What happens if you try to ping a location from the command line? 

For example, first try "ping comcast.net"
If that doesn't work, try "ping 204.127.195.15."

If the first doesn't work, but the second does, then it's a DNS problem.

---

