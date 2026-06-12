---
title: "system clock not synchronising on startup."
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by tr333 on 2005-11-03
when i originally installed breezy, the system clock would synch with the ubuntu ntp server to get the latest time.  now when i boot the OS, it says that the time server synch failed.  is this a problem with the ubuntu ntp server or with my computer?

---

### Post by teaker1s on 2005-11-03
check that system-administration-services
clock syncronisation has a tick

---

### Post by tr333 on 2005-11-04
great!  thanks.

i also had to install ntp and adjust date & time to use the ntp service.

---

