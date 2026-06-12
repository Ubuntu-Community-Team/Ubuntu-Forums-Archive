---
title: "How do you load a diver at boot?"
date: 2008-09-14
forum: x86 64-bit Users
---

### Post by acidblue on 2008-09-14
I want to load  a driver at boot time but not sure 
on how to do that any nudge in the right direction would 
be appreciated.

This is the driver: modprobe ftdi_sio vendor=0x403 product=0xbd90
Trying to get this to load: [http://letsmakerobots.com/node/663#comment-6925](http://letsmakerobots.com/node/663#comment-6925)

---

### Post by go_beep_yourself on 2008-09-15
Try putting that command at the end of your /etc/rc.local.

---

### Post by acidblue on 2008-09-15
Ok thanks i'll try that when i get home.

---

### Post by diobrando on 2008-09-15
If that doesn't work try adding it to /etc/modules

---

