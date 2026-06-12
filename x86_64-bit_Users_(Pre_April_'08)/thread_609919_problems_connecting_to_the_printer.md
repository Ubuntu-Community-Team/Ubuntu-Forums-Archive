---
title: "problems connecting to the printer"
date: 2007-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by DagonX on 2007-11-11
I have a brothers HL2070N printer that is connected via ethernet. How do I set the thing up in the AMD64 version of Ubuntu? The 32bit version of Ubuntu is different and I did not have a problem with the printer.

Charles

---

### Post by offroad64 on 2007-11-11
Try [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html) :)

---

### Post by DagonX on 2007-11-11
Thanks for the link. I will use it on my 32 bit system. Alas, the brothers driver doesn't work for the AMD64.

---

### Post by cjazz on 2007-11-12
> **DagonX said:**
> Thanks for the link. I will use it on my 32 bit system. Alas, the brothers driver doesn't work for the AMD64.

I've never used the driver for your particular printer. However, I'm currently using the 32-bit driver for the Brother MFC420CN on my 64-bit system. That required first installing the csh package, then installing the driver debs with "--force-architecture." If you want yours to run on AMD64, it might be worth a try.

---

