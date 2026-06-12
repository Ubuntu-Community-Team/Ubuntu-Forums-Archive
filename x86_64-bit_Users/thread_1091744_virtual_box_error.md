---
title: "virtual box error"
date: 2009-03-09
forum: x86 64-bit Users
---

### Post by eng.reem on 2009-03-09
hello all, plz i need help in this issue
i was installing windows vista by using virtualBox after i finished installation and tried to start vista i got that error 

"The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup' "
 when i write this /etc/init.d/vboxdrv setup
 in the terminal i only get this :
Stopping VirtualBox kernel module                                                                                                                          *  done.
 * Recompiling VirtualBox kernel module                                                                                                                      /etc/init.d/vboxdrv: 342: cannot create /var/log/vbox-install.log: Permission denied



and the problem still exist !!

---

### Post by squaregoldfish on 2009-03-09
It's not mentioned in the error message, but the command should be run as sudo to get root-level access. It should work then.

Steve.

---

