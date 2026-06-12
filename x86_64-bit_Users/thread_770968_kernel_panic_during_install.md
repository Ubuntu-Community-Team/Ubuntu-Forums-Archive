---
title: "kernel panic during install"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by h36th on 2008-04-27
hello

i am trying to install ubuntu 8.0 64 on a AMD athlon 64 x2 dual core 5000+ processor system

i get a kernel panic as soon as i sellect install ubuntu option

[http://irational.org/heath/ubuntu/kernel_panic.jpg](http://irational.org/heath/ubuntu/kernel_panic.jpg)

any suggestions ?

many thanks

heath

---

### Post by felker2 on 2008-04-28
Have you googled for "aiee, killing interrupt handler"? I see things about BIOS (SMART?) settings.

Does Ubuntu 7.10 work OK?

Have you tried booting with the boot options "pci=nomsi irqpoll noapic acpi=off"?

Have you tried the Safe Graphical Mode?

---

