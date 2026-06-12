---
title: "Acer 1410 and ubuntu 9.04. Failing to boot."
date: 2009-10-04
forum: x86 64-bit Users
---

### Post by agydar on 2009-10-04
I installed ubuntu 9.04 on my acer 1410 netbook from usb flash drive. It runs ok from the flash drive, but doesn't boot from HDD. Some times there is just a dark screen, and something like console. Can anyone help to solve this problem? 
There is Intel® Celeron®, supporting Intel® 64 architecture.

---

### Post by agydar on 2009-10-04
As i fugured out it was hdd troubles.
In bios by default HDD is in AHCI mode. I changed it to IDE and ubuntu started normally.

---

### Post by PatrickVogeli on 2009-10-04
Another solution, which I believe is better, is enable AHCI again and the add the kernel parameter libata.force=noncq

---

### Post by aspergerian on 2009-11-05
> **PatrickVogeli said:**
> Another solution, which I believe is better, is enable AHCI again and the add the kernel parameter libata.force=noncq

My 1410 solo core boots from CD if run as try it without installing but does not boot. I'll try the IDE switch but have no idea what to do with "add the kernel parameter libata.force=noncq"

Just open terminal and copy that line into terminal? 

Or need I switch to a different directory, then add the line?

---

