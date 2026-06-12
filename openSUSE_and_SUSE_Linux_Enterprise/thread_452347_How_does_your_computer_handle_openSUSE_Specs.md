---
title: "How does your computer handle openSUSE? Specs?"
date: 2007-05-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by ThinkBuntu on 2007-05-23
I'm just curious what sort of PCs comfortably, or uncomfortably, run openSUSE. If you care to share with us your hardware, such as wireless and graphics card, that would be nice too.

---

### Post by j.miller565 on 2007-05-24
Mine runs more than comfortably with:

AMD Sempronn 2800+ @ 2,002.78 MHz
512 MB RAM
80GB SATA HDD
nVidia GeForce FX 5200

---

### Post by RedDwarf on 2007-05-24
Asus P5B (Intel P965 / ICH8 with an additional JMicron PATA controller) with 1GB RAM, a Core2 Duo E6420 an a nVidia 7600GT graphic card.
Works without problems. Since I have a PATA CDROM connected to the JMicron I needed to specify manualy the pata_jmicron module in the installation, but that was the only problem. Even suspend to RAM works without problems.
The computer is fast and so is openSUSE 10.2.

For WiFis:
- Broadcom driver requires the firmware to be downloaded from "somewhere". License issues.
- Atheros/Madwifi need to be installed from a repository in the madwifi web since Novell doesn't supports propietary drivers.
- RaLink driver in 10.2 doesn't works. That's because the transition between the old driver and the new one at rt2x00.serialmonkey.com. I think there are working drivers in the Build Service.
- Up to where I know anything else works.

---

