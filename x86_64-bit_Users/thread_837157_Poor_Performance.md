---
title: "Poor Performance"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by Ubangi on 2008-06-22
My plain C programs run just fine. However, any benchmarks involving more intensive use of the stack, in particular the "recursive" benchmark from: [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/) is twice as slow as expected. This happens when using interpreted languages, in comparison against similar machines running it under SUZY Linux, for instance.  The benchmark runs  typically 60 times slower than compiled C, instead of just 30 times slower under Suzy.

I realise that the 64bit machine is going to be a bit slower perhaps than the 32bit version but this is out of proportion and must be caused by something else?

Did anyone else notice similar slowdown?

Is this possibly connected with the busybox issue I, amonst many others, suffered from during installation? I had only managed to install with manual boot parameter:

all_generic_ide=1

Could this be subsequently affecting the performance?

---

### Post by pixel :-) on 2008-06-26
i think you prefer to repost here [http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

