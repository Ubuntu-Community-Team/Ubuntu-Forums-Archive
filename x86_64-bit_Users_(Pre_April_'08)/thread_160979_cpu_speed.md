---
title: "cpu speed"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-04-16
I have an 800MHz G4, but /proc/cpuinfo says it is 667MHz.

How to fix it?

Max.

---

### Post by bikeboy on 2006-04-16
I don't know anything about PowerPC but can they scale the speed down at idle?

Out of interest try looking at cpuinfo while the system is under full load with something.

---

### Post by davidmaxwaterman on 2006-04-16
[QUOTE=bikeboy]I don't know anything about PowerPC but can they scale the speed down at idle?

Out of interest try looking at cpuinfo while the system is under full load with something.[/QUOTE]

Wow, you're absolutely correct :

```
$ while [ 1 ]; do
> grep clock /proc/cpuinfo
> sleep 1
> done
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 800MHz
clock           : 800MHz
clock           : 800MHz
clock           : 667MHz
clock           : 667MHz
clock           : 800MHz
clock           : 800MHz
clock           : 800MHz
clock           : 800MHz
clock           : 800MHz
clock           : 800MHz
clock           : 800MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz
clock           : 667MHz

```

Thanks :)

Max.

---

