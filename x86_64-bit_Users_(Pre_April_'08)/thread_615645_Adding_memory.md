---
title: "Adding memory"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by davesbedroom on 2007-11-17
I ordered some more memory and I can't wait to install Gutsy before I get it.  I have some memory.

My question is, if I install with 1GB of physical memory and then upgrade to 8GB.  Should I reinstall the kernel or do anything?  Or will the system just notice the extra memory and make use of it?

---

### Post by Yellow Pasque on 2007-11-17
The system should definitely detect and use the extra memory. Your OS won't be a problem, since you had the foresight to install a 64-bit distro. Just make sure your BIOS can detect 8GB

One setting I would recommend changing is vm.swappiness
```
sudo gedit /etc/init.d/rc
``` and add the following line (or edit if it already exists):
```
vm.swappiness=10
```Since you'll have a lot of free memory, there's no reason to swap to disk until you really start getting low on memmory.

---

