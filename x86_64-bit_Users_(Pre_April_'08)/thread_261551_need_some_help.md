---
title: "need some help"
date: 2006-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by bbbbbtony on 2006-09-20
installed the new kernel and headers and it seemed to break a few of my programs. more specifically the ati drivers which breaks a few of my games. and i think it may have also broken amarok and azureus.

i was just wondering if there is an easy way to get these things working on the new kernel headers. and also, i want to know how to take the old headers off of my grub menu.

---

### Post by Kilz on 2006-09-20
> **bbbbbtony said:**
> installed the new kernel and headers and it seemed to break a few of my programs. more specifically the ati drivers which breaks a few of my games. and i think it may have also broken amarok and azureus.

i was just wondering if there is an easy way to get these things working on the new kernel headers. and also, i want to know how to take the old headers off of my grub menu.

To get the ati drivers working again open a terminal an paste in these commands

```
sudo module-assistant prepare
sudo module-assistant update 
sudo module-assistant build
sudo module-assistant install fglrx 
sudo depmod -a
```

Second, you can safly remove old kernels from Synaptic. Do a search for linux-image , and remove the versions before, it will remove it from grub . But only remove the ones with a version.
Its often a good idea to keep the latest and the one right before it. In case an update to the latest kernel messes something up but doesnt change the version number.

---

### Post by bbbbbtony on 2006-09-20
didn't quite work.

followed along and things looked like they went right but when i type in fglrxinfo i get the following output:

Error: couldn't find RGB GLX visual!

i also get something similar if i type in glxinfo

---

### Post by Kilz on 2006-09-20
> **bbbbbtony said:**
> didn't quite work.

followed along and things looked like they went right but when i type in fglrxinfo i get the following output:

Error: couldn't find RGB GLX visual!

i also get something similar if i type in glxinfo

I forgot to add to reboot.

---

### Post by bbbbbtony on 2006-09-20
awesome. works great. thanks.

---

