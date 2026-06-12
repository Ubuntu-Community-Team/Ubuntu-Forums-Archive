---
title: "32 vs 64 bit posts and missing one of largest advantages of 64bit??"
date: 2009-07-24
forum: x86 64-bit Users
---

### Post by robackja on 2009-07-24
I am looking at the ridiculous boxee forums and just the horrible, horrible reasons why boxee won't be a 64bit build and I was referred to these 2 threads

[http://ubuntuforums.org/showthread.php?p=2200700#post2200700](http://ubuntuforums.org/showthread.php?p=2200700#post2200700)
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

In both those closed threads, a very important fact seems to be missed. And I love the claims, "you" don't need 64-bit. Well thanks Ubuntu and Boxee for letting me know what I need...

What about the registers!! x86 has 8 general purpose registers, 8 SSE floating point registers. x86_64 architecture has 16 general purpose registers and 16 SSE registers. 99% of the time, the doubling of the registers is a clear advantage over claims implications for efficient processor cache utilization, and an integer on 64bit is STILL 32bit. Yes longs and pointers are now 64bit.

Both articles do not even mention the word REGISTER.

---

### Post by jespdj on 2009-07-24
Indeed, especially CPU-intensive multimedia applications (which is what Boxee is, isn't it?) will be noticeably faster if they can use the extra registers in the CPU in 64-bit mode.

The second of the two threads you posted links to contains a link to a good article:
[64-bit: More than just the RAM](http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1)

---

