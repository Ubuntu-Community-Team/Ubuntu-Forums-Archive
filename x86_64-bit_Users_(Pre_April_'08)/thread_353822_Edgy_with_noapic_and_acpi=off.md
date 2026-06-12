---
title: "Edgy with noapic and acpi=off"
date: 2007-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by #Reistlehr- on 2007-02-05
Hey, i was just wondering exactly why i need to run Edgy with noapic and acpi=off. without them, i get x crashes.

---

### Post by pseudonym on 2007-02-05
Most probably because the default kernel doesn't support your machine properly. It's not uncommon with newer hardware - it happened to me.

It's usually fixed by compiling yourself a more recent kernel. I found out my motherboard was well supported in the kernel from version 2.6.18, so I built a 2.6.19 kernel from kernel.org. With that I can boot without 'noapic' and get the full range of IRQs (though I wasn't getting crashes).

If you haven't built a kernel before, see [this thread]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel+compile").

HTH

---

### Post by #Reistlehr- on 2007-02-05
=D thank you very much

---

