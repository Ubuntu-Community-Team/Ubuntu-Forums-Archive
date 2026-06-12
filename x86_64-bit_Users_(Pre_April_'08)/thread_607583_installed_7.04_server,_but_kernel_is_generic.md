---
title: "installed 7.04 server, but kernel is generic"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by gian on 2007-11-09
hello,

I installed Ubuntu 7.04 server on an Acer Altos G330 box, but uname -r shows a generic kernel.

I searched the forum posts here, and found this suggestion:

sudo apt-get install linux-backports-modules-2.6.20-15-server linux-headers-2.6.20-15 linux-headers-2.6.20-15-server linux-image-2.6.20-15-server

however, in my case that did not change the kernel type.
Now uname -r shows: 2.6.20-16-generic

Should I try installing 7.04-i386-server?

thanks for your time,
-Gian

---

### Post by Yellow Pasque on 2007-11-09
Did you reboot and select the new kernel in GRUB?

---

### Post by gian on 2007-11-09
I did reboot, but did not select anything...

Anyway, it changed from 2.6.20-15 to 2.6.20-16.

---

### Post by Kilz on 2007-11-09
> **gian said:**
> I did reboot, but did not select anything...

Anyway, it changed from 2.6.20-15 to 2.6.20-16.

You need to select the kernel to boot in grub. Watch as the machine boots. The Grub kernel selection screen may not show itself as the machine boots if only linux is installed (the same regardless of what version of Ubuntu is installed). But it should say to press esc or some other key if you want to enter grub.

---

### Post by gian on 2007-11-09
Kilz,

you're right, the kernel was there.

The kernel loads, but when I login to Xfce (Xubuntu desktop) I get this:

"could not look up internet address for oracle2007,
this will prevent Xfce ..."

checked network configuration, and all is there, also, I can browse the internet.
also, opening Firefox I get:

"last session closed unexpectedly"

I think they relate to kernel change...

---

### Post by Kilz on 2007-11-09
Are you running this on server equipment, or on commodity hardware (hardware used for average computers) used as a server?

---

### Post by gian on 2007-11-10
the box is an Acer Altos G330 server

---

