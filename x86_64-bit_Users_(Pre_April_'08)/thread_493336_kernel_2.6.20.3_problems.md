---
title: "kernel 2.6.20.3 problems"
date: 2007-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by kthardin on 2007-07-05
Awhile back I posted problems with the kernel to my upgrade of Edgy to Feisty.  All kernels above 2.6.17-10-generic would not run.  Which was strange since in Edgy 2.6.17-11-generic would run, but no longer in Feisty.

Attempting to follow the directions here:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

I managed to compile a custom 2.6.20.3 kernel based upon the 2.6.17-10 config.

Of course, this new kernel didn't work either.  Basically what happens is that when it loads, it starts with the kernel loading message, then I see a kernel keep alive message at the bottom of the screen, after which it just goes black and then nothing.  No response from the computer and no picture.  Waiting about 10 minutes, yielded nothing, forcing me to hit reset, which is what it was doing with the original Feisty Kernels.  Oddly, if I boot in diagnostics mode, I'm able to start an x windows session manually.

Can anyone tell me where do I start looking for the problem, and/or how do I go about finding it?

---

### Post by Cappy on 2007-07-05
You may need to use kernel option
```
nosplash
```
or maybe ```
noapic nolapic
```

---

### Post by kthardin on 2007-07-05
Thanks.  The nosplash option made it come up just fine.

What was going on there?

---

