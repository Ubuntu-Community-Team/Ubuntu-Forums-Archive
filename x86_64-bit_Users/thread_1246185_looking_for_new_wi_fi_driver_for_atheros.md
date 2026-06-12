---
title: "looking for new wi fi driver for atheros"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by jojom271 on 2009-08-21
i am not happy with network manager that ubuntu came with. i want to know if i can download atheros  driver from toshiba. will this work and do i have to change anything to make it work for me or linux. i know this driver is used in vista. i feel that my network manager is working slow and having a hard time connecting.
i am running 64 bit ubuntu on a toshiba sat m305 s 49052 32/64 4gib 320 gig

---

### Post by Bucky Ball on 2009-08-21
When you open System->Administration->Hardware Drivers, what wireless driver is enabled?

---

### Post by Bucky Ball on 2009-08-21
Definitely do not attempt to load the driver I think you are intending to. I don't know how you would load it anyhow; it is probably an .exe file. Is it the one on this page:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2234107&rpn=PSMD8U&modelFilter=M305-S49052&selCategory=3&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2234107&rpn=PSMD8U&modelFilter=M305-S49052&selCategory=3&selFamily=1073768663)

If so it clearly says it's for XP. If you have Ubuntu up and running, open a terminal and paste this in:

```
lspci
```You will find your wireless card in there toward the bottom. Post that. If you can't find it, post the whole result of the command.

Mad Wifi is probably what you are after. Toshiba don't seem to offer any Linux drivers so this is how we do it. 

What did you find in Hardware Drivers? Is there a driver for wifi in there disabled? If so, enable it.

Try this stuff and let us know. Please keep all replies on the forum so it can help others. :)


*** V Important: Go to System->Admin->Synaptic Package Manager, search for:

```
ubuntu-restricted-modules
```... mark for installation and 'apply'. See if you get anything from that.


Failing all this, look here:

[http://madwifi-project.org/](http://madwifi-project.org/)

[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

You want ath9k by the looks, for all current Atheros 11/n (which I assume would be yours). I would plug in an ethernet cable if you can until you have this fixed. Post the results of 'lspci' from your terminal first though. :)

---

