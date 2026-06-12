---
title: "Multiple prossessors?"
date: 2008-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mjrwingnut on 2008-03-20
Does the 64 bit version of ubuntu takes advantage of multi-prossessors?

I just built a new system with a amd quad-core.

---

### Post by Virtual_Ron on 2008-03-20
> **mjrwingnut said:**
> Does the 64 bit version of ubuntu takes advantage of multi-prossessors?

I just built a new system with a amd quad-core.

I'm running 64 bit with the AMD X2 dual core... it sure takes advantage of both.   I routinely encode multiple video files at the same time.

---

### Post by stringkarma on 2008-03-20
if you open a terminal and run:

```
cat /proc/cpuinfo
```

you can see in two ways the number of cpus that the computer is using
1) there should be one block of information for each cpu
2) there is a line that says cpu cores that should also give you the number of cpus.

I know that option 2 works for one processor with multiple cores, but option 1 will definately work whether you have multiple processor and/or multiple cores

---

### Post by mjrwingnut on 2008-03-20
can I run 32 bit apps in the 64 bit os? for example clamav or gimp?

---

### Post by Jouke74 on 2008-03-20
Uhh yes, but both programs also have 64 bit versions available. Just read some things about 64 bit Ubuntu please in the stickies.

---

