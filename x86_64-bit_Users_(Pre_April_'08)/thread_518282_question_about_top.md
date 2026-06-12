---
title: "question about top"
date: 2007-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-08-05
Hello, When I start top, I must push 1 to get cpu usage for both cores. How can I have that info shown automatically when starting top, so that I do not have to push 1 each time? I'd like to do the same with "z", so that I can have colors. Thanks. :popcorn:

---

### Post by John.Michael.Kane on 2007-08-05
I tested atop, and it shows both cores.

```
ATOP - ubuntu             2007/08/05  21:52:52               10 seconds elapsed
PRC | sys   0.11s | user   1.39s | #thr     115 | #zombie    0 | #exit      ? |
CPU | sys      1% | user     14% | irq       0% | idle    185% | wait      0% |
cpu | sys      1% | user      8% | irq       0% | idle     91% | **cpu000 w  0%** |
cpu | sys      1% | user      6% | irq       0% | idle     94% | **cpu001 w  0%** |
```

---

### Post by fakie_flip on 2007-08-08
> **SD-Plissken said:**
> I tested atop, and it shows both cores.

```
ATOP - ubuntu             2007/08/05  21:52:52               10 seconds elapsed
PRC | sys   0.11s | user   1.39s | #thr     115 | #zombie    0 | #exit      ? |
CPU | sys      1% | user     14% | irq       0% | idle    185% | wait      0% |
cpu | sys      1% | user      8% | irq       0% | idle     91% | **cpu000 w  0%** |
cpu | sys      1% | user      6% | irq       0% | idle     94% | **cpu001 w  0%** |
```

There should be a configuration in a configuration file that would allow for what I said. I'd like to have top automatically start with some features instead of having to push "z" and "1" each time i start top.

---

