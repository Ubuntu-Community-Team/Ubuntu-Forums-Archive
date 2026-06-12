---
title: "Config_hpet_emulate_rtc"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by gmaltby on 2007-05-05
Hi All,

Is anyone aware of the reasons why CONFIG_HPET_EMULATE_RTC is disabled in the x86_64 server versions (edgy and feisty) when it is enabled in the 386 versions?

Is there some difference with the 64bit hardware that means it should be disabled?

The question relates to the message 'rtc: lost some interrupts at xxx Hz' generated when VMware is running.  At least on the Dell hardware I'm using, enabling this setting removes the errors and the clock slip problems associated.

This then leads to maintenance issues on the host when updates are processed as it wants to upgrade my custom kernel.

Graham

---

### Post by Ken_Lewis81 on 2007-05-16
You could ask the kernel team on their mailing list -- see [http://lists.ubuntu.com](http://lists.ubuntu.com).

Take care.
Ken.

---

