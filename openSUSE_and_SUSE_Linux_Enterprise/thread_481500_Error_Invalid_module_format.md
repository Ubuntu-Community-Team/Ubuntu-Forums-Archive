---
title: "Error: Invalid module format"
date: 2007-06-22
forum: openSUSE and SUSE Linux Enterprise
---

### Post by justifier on 2007-06-22
Hi 

Whilst trying to install  driver made for suse 9.2 on suse 9.2 (new instalation) i get the error (<path>TWDrv.ko): Invalid module format we failed........  error: %post(TWDrv-5.64-1.0) scriptlet failed, exit status 1

Any ideas?

Justifier

---

### Post by kidders on 2007-06-23
Hi there,

You may be trying to load a kernel module compiled for the wrong CPU architecture. Even if it *were* to load successfully though, using kernel modules not designed for the specific kernel build you're running can cause serious malfunctions ... be careful!

What are the module's target architecture and kernel version? How do they compare to what you have?

---

