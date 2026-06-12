---
title: "Wireless doesn't work after memory upgrade"
date: 2005-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by hartogvdb on 2005-11-27
I upgraded the memory of my Ferrari 4005 with Kubuntu from 1Gb to 2 Gb and now the Bluetooth and Wireless don't work anymore. Do I need to make changes to configuration files for this sort of upgrade?

---

### Post by doogleplex on 2006-10-17
I have a similar issue. I upgraded from 512m to 1280m on an HP notebook (i'm on dapper amd64). After upgrade, wpa_supplicant, when executed at the command-line, locks the system up. memTest doesn't show any issues with the memory, and there's a windows (dual boot) on that notebook, and the windows OS doesn't illustrate any issues so far. I wish I knew more about memory configuration and/or kernel re-linking along these lines...
I would think that the memory would simply be "welcomed" by Ubuntu, and little or no configuration would be necessary. The swap file is 1024M, and I don't really need any more than that, so I shouldn't think the swap is involved.

Other than wpa_supplicant, I haven't noticed any other notable peculiarities.

---

