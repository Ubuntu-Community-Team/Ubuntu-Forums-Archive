---
title: "which is the current kernel of 6.10?"
date: 2006-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_ras on 2006-12-31
which is the current kernel of 6.10? (considering my sustem is up-to-date)

---

### Post by moma on 2006-12-31
$ [COLOR="SeaGreen"]sudo apt-get update [/COLOR]
$ [COLOR="SeaGreen"]sudo apt-cache search linux-image-[/COLOR]

```
linux-image-generic - Generic Linux kernel image
linux-image-386 - Linux kernel image on 386.
linux-image-686 - Obsoleted by: linux-image-generic
linux-image-k7 - Obsoleted by: linux-image-generic
linux-686-smp - Obsoleted by: linux-image-generic
linux-image-2.6.17-10-386 - Linux kernel image for version 2.6.17 on i386
linux-image-2.6.17-10-generic - Linux kernel image for version 2.6.17 on x86/x86_64

linux-image-server - Linux kernel image on Server Equipment.
linux-image-2.6.17-10-server - Linux kernel image for version 2.6.17 on x86/x86_64
linux-image-2.6.17-10-server-bigiron - Linux kernel image for version 2.6.17 on BigIron 
linux-image-server-bigiron - Linux kernel image on BigIron Server Equipment.
```

So the latest Ubuntu 6.10 kernel from the repository is "linux-image-generic" which points "linux-image-2.6.17-10-generic"  
$ [COLOR="SeaGreen"]apt-cache show linux-image-generic[/COLOR]

Some older machines may run "linux-image-2.6.17-10-386" kernel.

And server system has its own "linux-image-2.6.17-10-server" kernel.
--------------

Check your current, running kernel version
$ [COLOR="SeaGreen"]uname -r [/COLOR]

---

### Post by t_ras on 2006-12-31
thanks

---

### Post by fokuslee on 2007-01-02
you might also have extra (old) kernel lying around 
type ls /boot/vmlinuz* to check
u can safely remove older versions via synaptic

---

