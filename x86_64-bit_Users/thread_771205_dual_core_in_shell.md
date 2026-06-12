---
title: "dual core in shell?"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by lackofcreativity on 2008-04-27
I have a dual-core processor and when running any benchmark in the shell, only one core gets used. Are there any tweaks to allow access to both cores?

---

### Post by jespdj on 2008-04-28
What benchmarks are you using?

If the benchmark programs only use one core, then there's no easy way to make them use both cores. Software has to be written specifically to take advantage of multiple cores.

---

### Post by lackofcreativity on 2008-04-28
Uhhh.....don't think it makes a difference, everything I do in the shell is single core. I was using crafty and john.
BTW is your laptop good? I was thinking of getting that same one.

---

### Post by pjkoczan on 2008-04-28
> **lackofcreativity said:**
> Uhhh.....don't think it makes a difference, everything I do in the shell is single core. I was using crafty and john.
BTW is your laptop good? I was thinking of getting that same one.

Try running multiple instances of your benchmark in parallel, then you should see both cores getting used. You can do this by separating the program calls with an ampersand, i.e.

[program] & [program]

Unless a program is written to take advantage of multiple cores, the only way you'll use both cores is to run several programs in parallel. For this usage case, multicore processors are a *HUGE* win.

---

### Post by MM23 on 2008-04-28
if you're using an SMP kernel it will use both cores regardless of if the app is multi threaded or not.

---

### Post by tgm4883 on 2008-04-28
> **MM23 said:**
> if you're using an SMP kernel it will use both cores regardless of if the app is multi threaded or not.

Wrong, for the app to use both cores then the app must be coded to use multi threading.  Having a SMP kernel will distribute the load of 2 programs over 2 cores, but not 1 program over 2 cores.

I've used (cpuburn?) before and I had to run 2 instances of it.  It's been a while, but I may have also had to specify 2 instances of it to.

---

