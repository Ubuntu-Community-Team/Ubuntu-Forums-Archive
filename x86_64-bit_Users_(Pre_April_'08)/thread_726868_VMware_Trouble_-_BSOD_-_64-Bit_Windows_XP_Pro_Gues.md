---
title: "VMware Trouble - BSOD - 64-Bit Windows XP Pro Guest on 64-Bit Linux Host"
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by topgun98 on 2008-03-17
I am trying to use raw disk mode to run XP Pro x64 as a guest on an AMD64 Ubuntu Linux Host. So far, I have installed XP on a partition, but I get a blue screen when I try to boot it within VMware Workstation. That part is expected. In the past I was able to remedy this problem by manually installing the SCSI driver found on the VMware Downloads page. However, now I get an error in windows stating that I can't install a 32-bit driver.

Is there any way to load a VMware-friendly disk driver on a 64-bit XP-based guest?

Thanks in advance for any assistance!

---

### Post by Kilz on 2008-03-17
> **topgun98 said:**
> I am trying to use raw disk mode to run XP Pro x64 as a guest on an AMD64 Ubuntu Linux Host. So far, I have installed XP on a partition, but I get a blue screen when I try to boot it within VMware Workstation. That part is expected. In the past I was able to remedy this problem by manually installing the SCSI driver found on the VMware Downloads page. However, now I get an error in windows stating that I can't install a 32-bit driver.

Is there any way to load a VMware-friendly disk driver on a 64-bit XP-based guest?

Thanks in advance for any assistance!

Find a 64bit scsi driver for vmware. Lack of drivers is a major issue with 64bit Windows.

---

### Post by alejandro.mc on 2008-03-17
I'm a newby, but I always want to help. Have you tried virtualBox? I run XP in Ubuntu using and it works perfectly. Bye! Good luck!

---

