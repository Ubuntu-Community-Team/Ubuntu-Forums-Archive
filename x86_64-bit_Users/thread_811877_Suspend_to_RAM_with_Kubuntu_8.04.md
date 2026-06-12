---
title: "Suspend to RAM with Kubuntu 8.04"
date: 2008-05-29
forum: x86 64-bit Users
---

### Post by archwndas on 2008-05-29
Hi guys,
I just installed Kubuntu and to my surprise once again I found out that suspend to RAM doesn't work. I expected that to work since it was fixed somehow in 7.10 Gutsy. Any ideas what one could do ? I know it is a platform dependent problem. Sabayon Linux though seems to have solved the problem and suspend works fine out of the box. I get a black-screen after resume and I have to press power-off. CTRL-ALT-BACKSPACE e.t.c. will not work. If you need any info on my Laptop please let me know. I suspect however that the problem is more general and not laptop specific. I have nvidia drivers installed but suspend to RAM wouldn't work even before I install the Nvidia drivers. 

best,
Archwn.

---

### Post by bford16 on 2008-05-30
Did you try```
gksu gedit /etc/default/acpi-support
``` and set ENABLE_LAPTOP_MODE from false to true?

---

### Post by archwndas on 2008-05-30
Yes I did that. Nothing changed. The same old black screen after resume and can't do anything else except shutting off.

---

### Post by archwndas on 2008-06-04
I would like to say that problem is finally solved. I updated and installed the new kernel .18

Linux Symeon 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux. Now my Laptop ACER Aspire 5633 wakes up from the Standby in RAM. Everything is fine. Thanks guys. Take care and do not break that feature in future releases.

---

