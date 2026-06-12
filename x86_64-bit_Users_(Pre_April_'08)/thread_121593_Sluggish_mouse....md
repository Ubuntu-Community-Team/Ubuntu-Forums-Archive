---
title: "Sluggish mouse..."
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fjodor on 2006-01-25
From time to time (quite often), my mouse seems to have frozen, only to begin to move sluggishly after a little while. I don't know where the problem lies, but here is the rundown:

Mouse: Logitech MX Laser (bluetooth, own adapter)
Kernel: Ubuntu 2.6.15, compiled with all the available low latency options (3 of them, I think. I chose the ones suited for desktops).
System: Ubuntu Breezy amd64.

I usually run boinc, and do quite a bit of downloading (Yukon Gigabit ethernet and latest madwifi). The problem persists with boinc turned off. As of this moment, 'uptime' reports a load of 0.20.

Three system monitors in the upper panel scroll uninterrupted.

What can I do?

Best regards,

Fjodor

---

### Post by Fjodor on 2006-02-03
Some debugging later, it turns out madwifi is unstable on 64bit and causes it

---

