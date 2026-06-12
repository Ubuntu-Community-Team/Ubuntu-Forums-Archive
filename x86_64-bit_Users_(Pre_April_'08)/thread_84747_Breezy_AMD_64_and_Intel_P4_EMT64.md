---
title: "Breezy AMD_64 and Intel P4 EMT64"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by kupokomapa on 2005-10-31
I have a Dell machine (dimention 9100, I believe) that I cannot install neither x86 or 64 bit ubuntu on. Can you tell me what could be the problem as it boots to some point (after starting APIC) and then displays some information about the hard drive and then stalls. I have RHEL 4 Workstation on it and it runs fine it is just that I do not want to keep the RH and I'd rather install ubuntu but I cannot even get the installation to work. The live CD does not seem to work either, so it must be some invopatibility issue.

I read the posts of some users that EMT64 should work with the AMD_64 Ubuntu but this does not seem to be the case with me.

Thanks to everybody who can help me.

Kupo

---

### Post by RAOF on 2005-10-31
You should be able to install either the x86 or the x86_64 version.  That you can't install (or boot) either suggests that acpi, apci or some similar four letter acronym may be messing stuff up.  You'd probably find more help in the "Installation support" forum, but a quick search for acpi will net you something like [this thread]("http://www.ubuntuforums.org/showthread.php?t=76482&page=2&highlight=noacpi").  

Briefly, try booting either the install cd or the live cd with 
"linux acpi=off noacpi" at the grub prompt.

---

