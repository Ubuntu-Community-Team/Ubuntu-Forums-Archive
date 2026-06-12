---
title: "No wireless after suspend on ibook G4"
date: 2006-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by NickDanger on 2006-04-09
Hi all. I am running dapper flight 6 with the 2.6.15-20-powerpc kernel on an ibook G4. I am having troubles to get wireless networking after the machine wakes up from suspend-to-ram (it works fine directly after boot though). After waking up I can run, for example, iwlist scan just fine, but dhcp never gets a reply. I tried unloading and reloading the bcm43xx modules, but the problem persists. I also cannot see anything about eth0 (the wireless interface) in /var/log/syslog, only notes about suspending and waking up eth1.

Any ideas for how I can resolve the situation?

Regards.

---

