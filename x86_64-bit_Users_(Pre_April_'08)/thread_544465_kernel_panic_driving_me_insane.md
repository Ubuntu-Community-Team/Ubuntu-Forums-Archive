---
title: "kernel panic driving me insane"
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mistlur1 on 2007-09-06
Hi!

I have been having this problem with apic/acpi since I bought a new mobo about a year ago. I got the "MP-BIOS bug: 8254 timer not connected to IO-APIC", but still i could install and boot Feisty, except for a kernel panic every 50th boot or so. This really annoyed me, and since i couldn't fix it though I've flashed BIOS every time there was a new release and there are numerous posts by other linux-users experiencing the same problem, I resorted to buy a new motherboard last week (GA-M55S-S3). I really thought that this would solve my problem, but oh my I was wrong. It made it worse. Now I can install ubuntu if i append the "noapic" kernel parameter to avoid a kernel panic when booting the live-cd, but I can't boot from hdd. The only thing i get after grub is "Error 15\ no such file"... Am I missing something?
I'm writing this through a live-cd.

I'm going to try a few more things (feels like I've read all other posts concerning similar probelms, and they all seem to have differnet solutions or none at all), like different boot parameters and play around in the BIOS settings. If that doesn't help I might just lay down and cry for the rest of the day.

Does anyone have an idea what I should do, not do, or just give me some comforting words during these frustrating times I would gratefully appreciate it.

EDIT: I'm trying to install Ubuntu amd64

/mistluren

---

### Post by tgalati4 on 2007-09-06
Try installing Dapper 6.06.1 and see how long it runs.  You need stability first with your hardware.

---

### Post by mistlur1 on 2007-09-06
It's solved!

The reason for the strange error message that grub couldn't find the kernel... because there's a bug in my current BIOS which mixes up the boot order of hdd devices. By a whim i changed the boot order so that my second slave ide-drive was first in the boot order, which made my sata-drive actually being the first!? This enabled me to boot anyhow.

Happy now.

/mistlur1

---

