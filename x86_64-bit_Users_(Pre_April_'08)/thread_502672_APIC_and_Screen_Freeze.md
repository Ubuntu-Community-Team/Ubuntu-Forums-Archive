---
title: "APIC and Screen Freeze"
date: 2007-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by TeeGeeLee on 2007-07-16
Please explain:
      I am used to using Mandriva Linux. When I use that system, I do not have to disable APIC. The OS works perfectly without the change. 
     On th other hand, Ubuntu 6.06 will freeze after a few minutes (sometimes seconds) if APIC is not completely disabled in the BIOS. If I just bring up the start-up screen in Ubuntu, and ask it to disable APIC locally, I get the same result.
     I would like to be able to dual-boot XP and Ubuntu. If I disable APIC, Windows will NOT work at all.
    Is there a solution to this?
    Anthony Genco

---

### Post by Cappy on 2007-07-17
are you using the boot params
```
noapic nolapic
```
That's what I and others use.

---

