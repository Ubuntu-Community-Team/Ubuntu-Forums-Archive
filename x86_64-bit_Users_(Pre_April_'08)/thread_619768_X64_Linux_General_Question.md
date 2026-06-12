---
title: "X64 Linux General Question"
date: 2007-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krovas on 2007-11-21
While running GKrellm in Feisty 64, I can observe the activity of both of my Athlon 64 x2’s CPU cores, and I’ve noticed something: at no time will the combined effort of both cores ever exceed 100% capacity of one core. For instance, if at a given time CPU1 is operating at 80%, CPU0 will be operating at 20% or less. That’s always how it works; both CPUs will never run flat out, or even in excess of 100% of one core. So I guess my question is: is there some sort of governor prohibiting both cores from running at full capacity at the same time? If there is, can it be changed? And if the chip design inherently prohibits the cores from running at a greater speed than could be had by one core, what’s the advantage of having two cores?

Oh, also, CPU1 tends to get the lion’s share of the work done on my machine according to GKrellm, is there some reason for that?

I’m a 64 bit computing n00b, so please bear that in mind if these sound like infantile questions.

---

### Post by Kilz on 2007-11-21
> **Krovas said:**
> While running GKrellm in Feisty 64, I can observe the activity of both of my Athlon 64 x2’s CPU cores, and I’ve noticed something: at no time will the combined effort of both cores ever exceed 100% capacity of one core. For instance, if at a given time CPU1 is operating at 80%, CPU0 will be operating at 20% or less. That’s always how it works; both CPUs will never run flat out, or even in excess of 100% of one core. So I guess my question is: is there some sort of governor prohibiting both cores from running at full capacity at the same time? If there is, can it be changed? And if the chip design inherently prohibits the cores from running at a greater speed than could be had by one core, what’s the advantage of having two cores?

Oh, also, CPU1 tends to get the lion’s share of the work done on my machine according to GKrellm, is there some reason for that?

I’m a 64 bit computing n00b, so please bear that in mind if these sound like infantile questions.

Have you tried to get applications running that will use more? I know I have had more than 100% of 1 core running. But it takes a lot.

---

### Post by kuja on 2007-11-22
An interesting test might be something like this (with minor adjustments for your current setup) 

```

taskset 1 ~/Linux/bin/super_pi 20 > /dev/pts/3&
taskset 2 ~/Linux/bin/super_pi 20 > /dev/pts/4&


```

---

### Post by Kilz on 2007-11-25
Attached is a screenshot. I am encoding a dvd. Notice the conky display to the right. Both cpu's are being utilized on my AMD64 x2 4600 processor.

---

