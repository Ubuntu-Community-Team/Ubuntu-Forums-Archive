---
title: "Aperature too small"
date: 2008-12-29
forum: x86 64-bit Users
---

### Post by TouchuvGrey on 2008-12-29
When booting i get a message "Aperature too small ( 32 meg ) 
than (64 meg )" Can someone tell me what that means and what
 if anything should be done about it ?

---

### Post by Bloemetjesgordijn on 2008-12-30
Hi,

check this thread


[http://ubuntuforums.org/showthread.php?t=1018854](http://ubuntuforums.org/showthread.php?t=1018854)


Cheerz

Bloemetjesgordijn

---

### Post by Yellow Pasque on 2008-12-30
Basically, it means your motherboard is stuck in the 32-bit stone age and doesn't set the AGP aperture properly (also affects PCI-e systems, see [http://en.wikipedia.org/wiki/Aperture_(computer_memory](http://en.wikipedia.org/wiki/Aperture_(computer_memory)) ).
The issue might possibly be solved with a BIOS update, but if your motherboard is a cheapie or OEM, don't count on it. You can check your BIOS for something like Aperture/GART size or if you're lucky, "memory hole remapping".

---

### Post by dcstar on 2008-12-30
> **TouchuvGrey said:**
> When booting i get a message "Aperature too small ( 32 meg ) 
than (64 meg )" Can someone tell me what that means and what
 if anything should be done about it ?

The bottom-line is: Don't worry about it.

---

### Post by dcstar on 2008-12-30
> **Temüjin said:**
> Basically, it means your motherboard is stuck in the 32-bit stone age and doesn't set the AGP aperture properly (also affects PCI-e systems, see [http://en.wikipedia.org/wiki/Aperture_(computer_memory](http://en.wikipedia.org/wiki/Aperture_(computer_memory)) ).
The issue might possibly be solved with a BIOS update, but if your motherboard is a cheapie or OEM, don't count on it. You can check your BIOS for something like Aperture/GART size or if you're lucky, "memory hole remapping".

PCI-E systems don't need or use an AGP Aperture, so there is no BIOS "update" that will ever fix that. It is just kernel code looking for something that doesn't exist (and will never be used) on that particular hardware.

---

