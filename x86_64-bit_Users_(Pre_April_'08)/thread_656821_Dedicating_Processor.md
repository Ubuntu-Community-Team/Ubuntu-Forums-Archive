---
title: "Dedicating Processor"
date: 2008-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by thecreekninja on 2008-01-03
Hi I have an AMD 64 x2 machine.
I have unbuntu AMD64 installed.

I want to record using freebob on ardour and  jack.
I want to know if I can dedicate one processor(or at least most of it) to jack.  I think this would allow me to acheive a lower latency .

Does it make sense to try and do this?
Thanks.

---

### Post by ~LoKe on 2008-01-03
Open up the system monitor and right click the process and set the priority level.  I believe if you slide it all the way left it will give it highest priority.

But that's just off the top of my head.

Also, have a look at..
.```
man nice
```

---

