---
title: "X-fi Suspend Issues"
date: 2008-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusingcircle on 2008-03-18
Using the howto thread i've got sound working with the creative x-fi 64bit driver, but I have a problem with sound after suspending or hibernating though. The sound works on a cold or warm start but after suspending it fails to work. alsa-utils are called to stop and start when suspending and resuming, but ctsound will not stop due to:

> 
/etc/init.d$ sudo ./ctsound stop
Unloading X-Fi driver...
ERROR: Module ctalsa is in use


when i call lsmod it shows ctalsa running 1 process but does not name it. I cannot manually remove ctalsa to restart it:

> 
sudo modprobe -r ctalsa
FATAL: Module ctalsa is in use.


Anyone any ideas on how to get sound (or get ctalsa to restart) when resuming from suspend?

Thanks

---

