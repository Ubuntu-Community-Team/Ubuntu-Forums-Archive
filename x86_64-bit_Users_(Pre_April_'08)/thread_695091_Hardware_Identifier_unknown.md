---
title: "Hardware Identifier unknown"
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wisp2006 on 2008-02-12
Hy all,
I have managed recently to install Maya2008 on my gutsy x64 Ubuntu. But the joy was short since the program does not recognize my license which worked flawlessly in windows. When I want to see the hardware identifiers in the specific tab, it shows a blank window. Any idea why the network hardware adress is not shown? (that is, normally, the hardware identifier). The network card is working excellent.
P.S. Hope this is the right place where to post this.
Thanks.

---

### Post by Yellow Pasque on 2008-02-12
You should be able to get the hardware addy from the System -> Administration -> Network Tools GUI, or from the CLI with:
```
sudo ethtool eth0
```

---

### Post by Wisp2006 on 2008-02-13
I know that, there is no problem with the licence file. The problem is that Maya refuse to recognize my network card's adress. Could be any known reason for which it doesn't see it? Obviously, i can't get help from Maya forums since Ubuntu is not one of the supported Unix distributions. :confused:

---

