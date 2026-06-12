---
title: "MySQL Problem"
date: 2006-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by xMbx on 2006-09-17
I´m starting to ask me myself "Why the hell Ubuntu. We got never problems with Debian."

So, the problem is this:
MySQL keeps on crashing with the whole system nearly ever day. I dunno the reson. Sometime we see this message:

mysqld got signal 11;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help diagnose
the problem, but since we have already crashed, something is definitely wrong
and this may fail.

key_buffer_size=67108864
read_buffer_size=1044480
max_used_connections=0
max_connections=500
threads_connected=0
It is possible that mysqld could use up to
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 1599532 K
bytes of memory
Hope that's ok; if not, decrease some variables in the equation.

Sometimes, you find no error whatever.
I tried the mysql Ubuntu packets, i tried a source install. Both the same result.

We use the AMD64 Server Kernel of Ubuntu. System is a AMD 64 X2 3800 with 2GB RAM and 2x160 GB on Software Raid.

Does anybody got a wise idea, how to make that system stable ? It is really urgent.

---

