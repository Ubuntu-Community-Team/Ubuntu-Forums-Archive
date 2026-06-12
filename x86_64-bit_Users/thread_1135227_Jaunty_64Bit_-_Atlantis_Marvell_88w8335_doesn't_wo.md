---
title: "Jaunty 64Bit - Atlantis Marvell 88w8335 doesn't work"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by giankyfava on 2009-04-24
Hi,
I just installed Jaunty Jackalope 64Bit and my Atlantis Land PCI wireless card doesn't work. The chipset is recognised as Marvell Libertas 88w8335 802.11b/g Rev.03. I tried to use ndiswrapper wi th two different 64bit windows drivers without success. This is what happens: I can load the driver (ndiswrapper -l gives "driver installed, ok"), I can load ndiswrapper as module (with -m option) but I can't see any device wlan0 in iwconfig. I tried also to blacklist the broken driver mrv8k, but anything happens... Someone can help me? Thanks in advance.

---

### Post by giankyfava on 2009-04-25
up

---

### Post by giankyfava on 2009-05-01
uppp

---

### Post by Krisseh on 2009-05-02
Where did you find 64bit of marvell 88w8335 ?
__[URL="http://ubuntuforums.org/showthread.php?t=1135812"]
[/URL]

---

### Post by Krisseh on 2009-05-02
> **Krisseh said:**
> Where did you find 64bit of marvell 88w8335 ?
[URL="http://ubuntuforums.org/showthread.php?t=1135812"]
[/URL]

I found a 64-bit driver that work grate without a problem : [http://moosy.blogspot.com/2007/01/netgear-wg311v3.html](http://moosy.blogspot.com/2007/01/netgear-wg311v3.html)  :: Chosie the 64-bit : [http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

---

