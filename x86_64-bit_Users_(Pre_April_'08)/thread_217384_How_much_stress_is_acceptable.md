---
title: "How much stress is acceptable ?"
date: 2006-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by topgun_ca on 2006-07-17
I gave the following command:
$stress --cpu 12 --io 10 --vm 10 --vm-bytes 128M --timeout 100000s --verbose

and then my top shows:
top - 01:23:10 up 3:13, 3 users, load average: 24.29, 24.32, 24.50

and then the system gave a kernel panic.

kernel panic at load average of 24 is it acceptable ?

---

### Post by wmcbrine on 2006-07-17
A kernel panic is never acceptable; it reflects either a bug or a hardware problem. However, I've never seen a load average of 24 before, and I hadn't heard of "stress" until now.

---

### Post by phork on 2006-07-18
Your system should not kernel panic regardless of load.  Usually when this happens it's a result of some hardware issue (i.e. CPU overheating).  Try installing lm_sensors and checking out some temps while running stress.

As a side note, 24 is nothing -- I've seen 4 digit loads where I work (though obviously that's an extreme case).

---

