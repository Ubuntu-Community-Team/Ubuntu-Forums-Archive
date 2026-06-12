---
title: "VirtualBox question:  Nested Paging not available for my configuration?"
date: 2009-03-16
forum: x86 64-bit Users
---

### Post by dpcole72 on 2009-03-16
Hello  I use the following configuration - but when using VirtualBox on the following set-up, it says "Nested paging" is disabled - despite being enabled in the VM configuration:

Host:
Ubuntu 64-bit, v8.10
Intel Q9650 CPU
Asus P5Q mobo (all h/w virtualization options enabled that I can tell)
8GB RAM
nVidia GTX260 mobo
Compiz is activated

VirtualBox 2.14 (64-bit)
Running Windows XP 32-bit guest

Again, the guest OS configuration has "Nested Paging" checked.  Yet when I run the OS, it says it is disabled. VT-x/AMD-v does show "enabled", however.
   
Is there a way to force enabling of nested paging?

Thanks!

---

### Post by sergey.didyk on 2009-03-20
> **dpcole72 said:**
> 
Intel Q9650 CPU


Nested Paging isn't supported by that proc. Only Core i7 has it.

---

