---
title: "CPU frequency scaling unsupported"
date: 2006-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by arjaybe on 2006-01-21
I get this message when I boot Ubuntu 64 5.10.  Frequency scaling was working untill just recently.  I upgrade once or twice a week so I can't say exactly what might have caused this change, but it was before the most recent kernel upgrade.  Frequency scaling failed in Kubuntu at about the same time, although it didn't give a message.  Here are the Powernow lines from dmesg:

powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
powernow-k8: BIOS error - no PSB or ACPI _PSS objects

This is identical in Ubuntu and Kubuntu.  I've only entered CMOS to change the device boot order lately.  I don't think I could have caused this by changing the BIOS, but I'm open to all suggestions.

Edit:
It looks as if it was my mistake.  I went into the CMOS and found the Cool'n'Quiet setting disabled.  I enabled it and Powernow works again.  I still don't remember disabling it in the first place, but I guess I must have.  Maybe I should see a doctor about that.-)

---

