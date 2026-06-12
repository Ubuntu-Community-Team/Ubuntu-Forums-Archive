---
title: "Can not configure printer"
date: 2005-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gunnar on 2005-04-12
Hi all
After installation I am trying to configure my HP OfficeJet K80 with ptal/CUPS.
Everything works great up to the point where CUPS want a user/password
(web-interface localhost:631, Manage Printer, Add printer).
No matter what I say here it the system does not allow me to proceed.
All help appreciated.
Gunnar

---

### Post by Robban59 on 2005-04-12
Hi Gunnar, 

I read somewhere else in the UBUNTU forums that this may help :

1) $ sudo adduser cupsys shadow
2) $ sudo /etc/init.d/cupsys restart


Have not tried it yet personally..

---

### Post by Gunnar on 2005-04-12
Thanks very much for your help, it works perfectly.
Regards, 
Gunnar

---

### Post by paxmark on 2005-04-25
Mange tusen takk
Many thousand thank you's
worked like a charm for Kubuntu

---

### Post by sylbal on 2005-04-27
Hello,

I have problem when trying to install my Laserjet 6P, I presume it's quite close to 6L and I followed the help provided here (add user).

When sending print page, the printer start flashing leds and nothing happens, the job is automatically removed from the list.

I have fresh install and I dind't had any package yet. 

I tried with LiveCD64 and the same action print awful line of characters on few pages. It's different behaviour but still not really interresting.

Can anyone help me before I'd get back to 32bits (which print perfectly, ...) I'd be a little frustrated.

Regards,
-sb

---

