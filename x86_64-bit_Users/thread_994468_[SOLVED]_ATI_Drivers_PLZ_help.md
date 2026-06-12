---
title: "[SOLVED] ATI Drivers PLZ help"
date: 2008-11-26
forum: x86 64-bit Users
---

### Post by mag1strate on 2008-11-26
Every time I check the driver option on the hardware section, it says it's downloading, but it ends up freezing! Can anyone help me!:(

---

### Post by inobe on 2008-11-26
restart your machine



now try again

---

### Post by nzadLithium on 2008-11-26
When you say its freezing do you mean hardware manager is? Or just the download stops going?

---

### Post by inobe on 2008-11-26
the download for nvidia froze with me as well, i tried restarting' that fixed the problem.

it seemed that this happens after an upgrade from 8.04 to 8.10.

that's not all, after restarting' the notifier stated their was a driver that needed to be enabled, looking in restricted drivers showed it already enabled, i disabled it and restarted once again !

once the desktop was loaded for the second time i enabled restricted nvidia driver, it worked

i thought it was pretty weird to have to do that' none the less i avoided getting down and dirty.

---

### Post by bford16 on 2008-11-26
I had the same problem with upgrades and with fresh installs.  So the last time, I just went ahead and installed the xorg-driver-fglrx package manually.  (I used synaptic, but there's no reason one couldn't just "sudo apt-get install xorg-driver-fglrx.")  NOTE: you might need a different ATI driver - I just happen to use fglrx on my machine.

---

### Post by mag1strate on 2008-11-26
WOW! Restarting really helps! Thanks for the comments guys!:)

---

### Post by nzadLithium on 2008-11-27
lol maybe someone should file a bug report XD You shouldn't have to restart your computer to install the drivers, at the most you would have to restart x to make the driver take effect after its been installed :S

---

### Post by inobe on 2008-11-27
yes but its also related to the network, considering that still runs.........

---

### Post by bford16 on 2008-11-28
> **nzadLithium said:**
> lol maybe someone should file a bug report XD You shouldn't have to restart your computer to install the drivers, at the most you would have to restart x to make the driver take effect after its been installed :S
Not only was it necessary to restart the computer (twice), but I had to do a "sudo apt-get update," then restart a third time to get Ubuntu to *offer* to install the new driver(s) on my laptop.  On my desktop, the Hardware Drivers program offered to intall 2 different versions of the proprietarty nVIDIA driver (173 and 177 - I used 177).  The installer still didn't work.  So I ended up purging everything nvidia via synaptic, then rebooting and installing the new 177.80 driver.

---

