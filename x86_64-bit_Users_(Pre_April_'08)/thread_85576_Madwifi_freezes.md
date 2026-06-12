---
title: "Madwifi freezes"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by fassan on 2005-11-03
I have narrowed down all my problems to the wireless card. I am using an AR5212 on Ubuntu 64. I have tried two different wireless cards, both with that chipset. Both function okay for a while. If, however, I leave a bitorrent program or something similar going, the machine will freeze (it always takes a while, as the monitor is always blanked out.) I am using the latest SMP kernel and the madwifi modules that come in the 'restricted' package. I looked at the madwifi CVS, but all of the drivers seem to be the same version as the ones in Ubuntu's repository.

I know that the freeze is wireless related because If I disable the wireless and just use an ethernet cable, the machine runs fine for days.

Has anyone else experienced and/or solved something like this?

---

### Post by finni on 2005-11-03
Same problem here with x86 install. Hoary worked just fine.
I've got HP nc6000 laptop with atheros chipset wireless mini-pci card.:confused:

---

### Post by domo on 2005-11-25
Same thing here, with ipw2200 on a A3N asus and Breezy x86.
No special driver add and the last Kernel install (2.6.12-9-386).

Wifi works find but I have a hard freeze sometimes (don't find any reason).

---

