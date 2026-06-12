---
title: "Load balancing broken?"
date: 2007-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by janerikdahlin on 2007-06-19
According to top I quite often have two (or more) CPU bound processes competing for one of my two processors while the other is 99% or 100% idle. Isn't the kernel supposed to rebalance the load so both my processors are used? Does anyone else see similar behavior?

I have two Opteron 252s and I use Feisty Fawn.
Linux dalburk 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

---

### Post by kuja on 2007-06-19
I've noticed it acting strangely too. Seems it often tries to throw more than one cpu-intensive process on one core, and the other gets relatively low activity, holding the others back. If you really want to seperate things, try this:

sudo apt-get install schedutils
taskset 1 programname

to run the programs. The #1 would refer to the processor, and as you might think it forces it to run on just that processor :)

---

