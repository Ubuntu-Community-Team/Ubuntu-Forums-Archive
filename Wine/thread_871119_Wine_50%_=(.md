---
title: "Wine 50% =("
date: 2008-07-26
forum: Wine
---

### Post by viciad0 on 2008-07-26
Well, i installed wine and its great!

The only problem i have is about it only uses 50% of processor, when i mean 50% i mean it uses 50% of cpu1 and 50% of cpu2 , it uses the two cores but only 50% =(.

Is there any way it to use the full processor??

Thanks =)

---

### Post by YokoZar on 2008-07-26
> **viciad0 said:**
> Well, i installed wine and its great!

The only problem i have is about it only uses 50% of processor, when i mean 50% i mean it uses 50% of cpu1 and 50% of cpu2 , it uses the two cores but only 50% =(.

Is there any way it to use the full processor??

Thanks =)

Most likely Wine is actually using all of one processor and none of the other.  Dual CPUs require threaded applications to run.  If the Windows programs you're running in Wine aren't designed to use up multiple CPUs, then Wine won't be able to either.

---

### Post by viciad0 on 2008-07-26
Damn, thats bad =(.

Maybe in the future you can use the multiprocessing in single threaded applications like windows =).

Thanks anyway

---

### Post by YokoZar on 2008-07-26
> **viciad0 said:**
> Damn, thats bad =(.

Maybe in the future you can use the multiprocessing in single threaded applications like windows =).

Thanks anyway
What are you talking about?  Windows has the same limitation.  Load is distributed across multiple processors because there's always more than one application running currently, even if they're all single-threaded.

---

