---
title: "broken dependencies"
date: 2008-05-23
forum: Za Team - South Africa
---

### Post by LDrenzo on 2008-05-23
hi guys!

when i was trying to install beryl on my pc i got a massage like error installing package x, x package is to b installed. i tried installing again but i got exactly the same massage. when i tried to launch dolphin it did not launch so i tried installing otheer appllications and they also did not lauch and they gave a massage like broken dependencies. when i realised that no application could launch i restarted my pc and when i had finished restarting it could not log me back to the graphical interface. so i restarted the 2nd and third tym with no luck.

any suggestion and effort to help will highly apreciated thanks.

---

### Post by Applecache on 2008-07-04
Hello


This command is a diagnostic tool. It does an update of the package lists and checks for broken dependencies.
#

apt-get -f install

This command does the same thing as Edit->Fix Broken Packages in Synaptic. Do this if you get complaints about packages with "unmet dependences".
#

apt-get autoclean

---

