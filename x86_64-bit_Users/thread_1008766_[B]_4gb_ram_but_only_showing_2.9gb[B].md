---
title: "[B] 4gb ram but only showing 2.9gb[/B]"
date: 2008-12-11
forum: x86 64-bit Users
---

### Post by mannaa on 2008-12-11
Grettings!

Background:
I recently managed to install Intrepid 64 bit on my laptop. In order to get it to install on my system I had to edit the boot command line by adding: mem=4096m or else it wouldnt install at all. I also have to edit the boot command line each time I run Intrepid, for it to start. I have 2x2gb dual channel at 800 mhz. 

And now the question: Why does it only show 2.9gb when I have 4gb installed? How can I resolve this issue?

---

### Post by psusi on 2008-12-11
Post your dmesg.  It is probably that your motherboard can't remap the ram above the 4 GB mark so the ram in the 3-4 GB area is hidden by IO devices.

---

### Post by mannaa on 2008-12-11
Hello! Thanks for the fast reply, here are the lines(sorry I dont know how to create thoose nice lookin boxes):

[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8b3000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8b3000 - 00000000bf8b9000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8b9000 - 00000000bf9c3000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9c3000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb0d000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb0d000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd66000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd66000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)

---

### Post by psusi on 2008-12-12
Hrm... looks good... I think your problem is your mem= parameter.  It's telling the kernel not to use the addresses from 4-4.6 gigs.

---

