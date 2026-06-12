---
title: "High system load while idle"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by jlagrone on 2008-05-14
I've been having problems with the system load being high.  It seems to be consistent: idling the average load is always 2 or slightly higher, and generally the average load is reported about 2 higher than what it has normally been in the past.

---

### Post by Sam Lars on 2008-05-14
Does the command top in a terminal or System > Administration > System Monitor point to any process that's using a lot of processor or memory?

---

### Post by jlagrone on 2008-05-14
I think I found the culprit, I've been running mythweb and it seems that it got stuck in an infinite loop.  I had a symlink in one of the folders back to itself for some reason

---

