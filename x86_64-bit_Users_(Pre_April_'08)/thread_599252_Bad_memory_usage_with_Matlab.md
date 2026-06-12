---
title: "Bad memory usage with Matlab"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by lutzky on 2007-11-01
Hi,
I run a batch matlab job server here at my lab, running Dapper 6.06 (for the LTS). One of the users has submitted a very memory-consuming job, which successfully crashes the server. Upon closer inspection, the crash happens like this:
1. I run matlab with the given file
2. RAM usage quickly fills up
3. Once the RAM meter hits 100%, the system freezes: All SSH connections freeze up, and while switching VTs directly on the machine works, no new processes run - so one can't log in, or do anything if he is logged in. (Sometimes typing doesn't work at all)

Note that the swap - while 7 gigs of it are available - is never used. (The machine has 7 gigs of RAM as well)

I've tried the same on my Gutsy 32-bit box, and there was no system freezeup - matlab simply notified that the system was out of memory. However, it did this once memory was 100% in use - and still, swap didn't get used at all! (Though it is mounted correctly and shows up in "top" and "free").

So first thing's first - I'd like to eliminate the crash issue. I suppose I could switch the server to 32-bit, but I think that would be a performance loss, considering that it does a lot of heavy computation. There is no reason, however, that this should happen on a 64-bit machine anyway. Why does it?
The second concerning thing is swap - how come it doesn't get used?

---

### Post by kuja on 2007-11-01
Sounds like a bug that needs reporting.

As per it not swapping out, perhaps adjusting the swappiness will help.

---

### Post by lutzky on 2007-11-01
Reported here:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/159356](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/159356)

---

