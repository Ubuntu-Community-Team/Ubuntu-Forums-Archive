---
title: "Dual Boot 32 Bit and 64 Bit: Can I reuse SWAP?"
date: 2007-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mark Grice on 2007-10-31
OK, when I did my 64-bit Ubuntu install, I have three partitions: Root, Home and Swap.

If I set up a new partition, and install the 32 bit version there, can I reuse swap for both? Or do I need a new swap and home for each install?

---

### Post by buzzbo on 2007-11-01
My guess is yes.  It seems that swap has nothing to do with anything except that it is part of your hard drive for dealing with memory as you are running the OS.  Since you are running only one OS at a time, then you only need one swap.  There is no such thing as 32-bit swap or 64-bit.

I would imagine that people running other distros probably have a common swap.

---

### Post by jocko on 2007-11-01
Yes, you can use the same swap.
And it should work to use the same /home for both installs, but there may be some differences in some configuration files that may cause problems, so it may be better to have separate /home.

---

