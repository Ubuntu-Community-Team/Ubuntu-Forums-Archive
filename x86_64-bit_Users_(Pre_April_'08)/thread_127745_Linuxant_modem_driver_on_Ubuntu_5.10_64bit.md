---
title: "Linuxant modem driver on Ubuntu 5.10 64bit"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Alendit on 2006-02-09
I've get today my Ubuntu shiped and have a lot of fun with it ;-)
I've spend ca 3 hours instlling my modem...i had to reinstall my system 3 times))
I use linuxant 64 driver in tar archive. 
Please if anybody knows how i can get it running post a little howto or give me a link.

I hope i will never more have to use win to surf in internet)

Alendit

---

### Post by ippiraman on 2006-02-11
You can find instructions on setting up / configuration of dial-up modems here:

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

---

### Post by Alendit on 2006-02-12
@ippiraman

Thank you for this link, but there no HOWTO for 64-bit Breeze. There no .deb package on the linuxant.com for 64-bit breeze, only source and i can't compile this source because it wants autoconfig.h in /usr/src/linux/include. I've installed linux headers and source packages, but it didn't help me. If some one installed winmodem on 64-bit Ubuntu plz tell me how did you do that.

Alendit

---

### Post by danielta on 2006-02-12
hi, i have a conexant winmodem and i tried to install it following instructions on this page of ubuntu forum:
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=forum%2Fhardware%2FConexant#head-0164869cfd1c39a2bdff939835094630ba26bdef](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=forum%2Fhardware%2FConexant#head-0164869cfd1c39a2bdff939835094630ba26bdef)

my system is an acer laptop with Amd turion 64bit and i have installed kernel 2.6.12.10 (kubuntu 5.10 64bit).

the problem is that , once rebooted, i receive this error:
hsfmc9797ati can't be loaded missing kernel or user mode driver hsfmc97ati.

and the startup procedure is stopped!

what can i do?

thanks!
Danielta

---

### Post by Alendit on 2006-02-12
The same problem.
I recieved a message Architecture specific modules configuration for x86_64 not found... Any ideas what it can be? The package modutils is installed by default.

---

