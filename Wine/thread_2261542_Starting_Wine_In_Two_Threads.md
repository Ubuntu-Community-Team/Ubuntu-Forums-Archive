---
title: "Starting Wine In Two Threads?"
date: 2015-01-19
forum: Wine
---

### Post by ysnikitin on 2015-01-19
Hi,

Running latest Wine 1.6 on Ubuntu 14.

I have a service that starts a Java program with multiple threads, and may run Wine. So there may be at most 2 Java threads trying to start Wine at the same time (using same prefix; they will start two different exe's).

Is there documentation specifying that this is safe to do?

Thanks!

---

