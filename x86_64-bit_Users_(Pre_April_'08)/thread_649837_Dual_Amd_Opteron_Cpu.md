---
title: "Dual Amd Opteron Cpu"
date: 2007-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by enarxi on 2007-12-25
Hi 2 all and merry christmas...

I have an MSI K8D master mothrboard with 2 cpu's opteron. Unfortunately when I try to install or load the live cd, version 7,10 it crashes. The systme has 2 Gigs of registered ram and 2 terra storage. I also tried to install the server edition but stops responding where it looks for generic drivers for IDE devices. I played around with linux but not much I will say.

:(:confused: 

Thanx in advance..........

---

### Post by soslug on 2008-01-12
I would suggest seeing as you can not run from Live CD that you try to modify the kernel parameters, try the following

noacpi
noapic

also you could try to remove quite and splash from the kernel parameter line 

Cannot remember the exact format string but by pressing one of the Function keys you can edit the kernel parameters and append one or both suggested kernel strings besure to delete the double dash at the end of the kernel string and append as necessary.

press enter to boot from accepted kernel string

---

### Post by Rhubarb on 2008-01-12
> **soslug said:**
> Cannot remember the exact format string but by pressing one of the Function keys you can edit the kernel parameters ...

Insert the live CD, when the ubuntu boot menu comes up,
Press **F6**, then type in:
```
acpi=off libata.noacpi=1
```

This might work for you.

---

