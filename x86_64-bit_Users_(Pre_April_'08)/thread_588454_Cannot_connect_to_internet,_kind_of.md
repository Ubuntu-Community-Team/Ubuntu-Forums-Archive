---
title: "Cannot connect to internet, kind of"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krono89 on 2007-10-23
I'm running Ubuntu 7.10 on the following:

Acer Aspire 5050
AMD Turion MK-38 2.2GHz
1GB DDR2 RAM
Atheros AR5007EG wireless card
Realtek ethernet port



The problem I'm having is that I can't connect at all, except for Totem, which downloaded some video codecs. I've set my eth0 to use dhcp with my Linksys WRT54G, I would set up my wireless with ndiswrapper, but I can't get to the internet on my Ubuntu partition. Any ideas as to what I could do?

---

### Post by whistl on 2007-10-23
you could plug your laptop's wired ethernet port to one of the lan ports on the back of your wrt45g, until you can get the wireless drivers installed and working.

---

### Post by Krono89 on 2007-10-23
Thats the problem I'm having, my ethernet doesn't work, except for Totem which somehow connected to the internet to download ffmpeg and such.

---

### Post by John.Michael.Kane on 2007-10-23
> **Krono89 said:**
> Thats the problem I'm having, my ethernet doesn't work, except for Totem which somehow connected to the internet to download ffmpeg and such.

First see if you can ping trying this.
```
ping -c 4 google.com 
```
make sure to hit Esc after it has run for a few seconds.

Next you can try
```
sudo ifdown eth0
```

Followed by
```
sudo ifup eth0
```

Last resort reset your router, and try pinging again.

---

