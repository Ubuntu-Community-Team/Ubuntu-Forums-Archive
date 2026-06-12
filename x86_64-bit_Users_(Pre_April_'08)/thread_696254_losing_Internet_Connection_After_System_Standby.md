---
title: "losing Internet Connection After System Standby"
date: 2008-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by bogr@ on 2008-02-13
Hi,
Any ideas why I have to reboot to connect to the internet after the system goes to standby?
Thanks

---

### Post by mrsteveman1 on 2008-02-13
It may be that certain network settings don't initialize again when the computer wakes up. You might try reloading the kernel module for whatever network chipset you are referring to.

Is this a wireless network connection you are talking about?

---

### Post by Megaton on 2008-02-14
I had this same issue with Gutsy. Wired would work perfectly, but wireless would not start automatically. Even if connected when the laptop was put to sleep, the hardware wasn't even detected anymore. I have since made the leap to testing Hardy, and this has not been a problem. It has worked perfectly, every time.

---

### Post by bogr@ on 2008-02-16
Thanks for the replies; it's a wired system.:confused:

---

### Post by LO Matt on 2008-02-16
try this next time.

```
sudo /etc/init.d/networking restart
``` in a terminal

at least you wouldn't have to restart the whole os

---

### Post by Yellow Pasque on 2008-02-17
ethtool is a handy little program that spits out info on network connections. Keep that in your bag of diagnostic tricks.

---

### Post by Cappy on 2008-02-17
Run
```
gksudo gedit /etc/default/acpi-support
```
and change the line

STOP_SERVICES=""

to

STOP_SERVICES="networking"

then save the file.

---

### Post by bogr@ on 2008-02-17
Sweet! Thanks for the info... I'm away from the computer for a day or two - will post results ASAP.
Cheers!

---

### Post by xravexheavenx on 2008-03-12
Thanks!  I had this problem on 32 and hopefully this will solve it! :)

---

