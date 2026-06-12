---
title: "AMD 64, Gutsy Evolution Send/Recieve Problems"
date: 2007-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by thuleni on 2007-11-11
SUS AMD 64
Gutsy (7.10)
Kernel 2.6.22-14-generic
Evolution 2.12.0

After installation of the standard products - Sending and receiving email became problematic. I only managed to get it to work (using the pop and SMTP server names) very occasionally, and ONLY when i was doing a Trace Route, within Network Tools.

Changed all the DNS names to actual IP addresses (found during Trace Route) and NOW Evolution sends and receives all email to and from all three of my pop and SMTP accounts.

This looks like a DNS look up problem and I would be grateful if someone could shed some light on any similar problems in the set-up as described above.

Thank you

---

### Post by nss0000 on 2007-11-11
BigT:

I may be way-off , but doesn't the (local) system query your ISP "dns-server" every time you go_out? Are they responding? Perhaps the problem is with them.

---

### Post by thuleni on 2007-11-11
Hi BigT,

Yes the ISP responds each time the server does a hit to the outside world; however Evolution  doesn't seem to accept the acknowledgement?  So I can ping the DNS name and Trace Route to it.  And the Internet response is instantaneous, like with Web Mail (by DNS name).

---

### Post by thuleni on 2007-11-20
Ultimately, I switched "Automatic Update" on and downloaded all the updates.  This included  a newer version of Evolution, and following the update, changed all the IP Addresses back to DNS names of the POP and SMTP servers.

All working like lightening :-)

---

