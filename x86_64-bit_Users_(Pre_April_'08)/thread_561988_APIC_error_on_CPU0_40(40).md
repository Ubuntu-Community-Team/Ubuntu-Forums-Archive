---
title: "APIC error on CPU0: 40(40)"
date: 2007-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by zeus09 on 2007-09-28
Hi,
I am new to linux so dunno much about it.
I recently checked the syslog and found a lot of logs as "APIC error on CPU0: 40(40)".
Is this normal......or should i be worried about it.........
if this helps i am using an amd machine with 1gb ram.
Thanks

---

### Post by Natr0n on 2007-09-28
It seems like booting with the noapic option *might* fix this. Here is a thread on how to do that: [[COLOR="Blue"]How to boot with the "noapic" option[/COLOR]]("http://ubuntuforums.org/showthread.php?t=148761"). This doesn't seem like a big problem though based on post #5 of this thread: [ [COLOR="Blue"]APIC error on CPU0: 40(40) on Targa 826[/COLOR]]("http://ubuntuforums.org/showthread.php?t=23718"). Hope that helps.

---

