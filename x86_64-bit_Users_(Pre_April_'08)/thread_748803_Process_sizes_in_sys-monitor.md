---
title: "Process sizes in sys-monitor"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by NoWayBill on 2008-04-07
Running Gutsy 64 (Studio)
System monitor is reporting amazing sizes for some processes, 17179869180.0 GB.
Yes, 17.18 billion gigabytes, um, I don't have that much RAM.	;)
Everything seems to work as it should, it just nags at me as to why this would be.

[IMG]http://home.earthlink.net/~jmiller7101351/sitebuildercontent/sitebuilderpictures/screenshot_system_monitor.jpg[/IMG]

---

### Post by tamoneya on 2008-04-07
looks to me like a overflow error.  It is probably trying to display -1 MB or something and since the numbers are unsigned it overflows to +17 billion.  As to how to fix this I don't know.  A restart should do it though.

---

### Post by NoWayBill on 2008-04-08
Na, it does it every boot.
When I first start Sys-Mon sizes are reported correctly, for maybe a second, then.....

---

