---
title: "CPU running high?"
date: 2009-02-10
forum: x86 64-bit Users
---

### Post by ffixcollector on 2009-02-10
My CPU is running higher than I'd like. I have a 64 bit Pentium 4 @ 3.00 Ghz and 2gb of ram

With nothing running, the CPU1 and CPU2 is between 10% and 30% apiece. On the processes tab, 
Gnome system monitor is at 4%, Firefox is at 2% and compiz is at 1%. Everything is sleeping except Gnome system Monitor.

What is using the CPU for the other 20%-50%?

I am having problems with Rythmbox freezing and The CPU's shooting to 100%. This usually only occurs when I am browsing with Firefox. With Rythmbox running, the CPU's seem to run at 30% and shoot up to 100% occasionally. On the Processes tab, it only shows using 1%?

How can I find what is eating up mu CPU and why?

---

### Post by cariboo on 2009-02-10
Open an Applications-->Accessories-->Terminal and type:

```
top
```

This should show what is using all the cpu cycles.

Jim

---

### Post by ffixcollector on 2009-02-10
Thank you.

It looks like Xorg is whats using up the CPU. Is there any way to make it run more efficiently?

---

### Post by ackray on 2009-02-11
Same here.  About 25% on an AMD Athlon 64 1.2  

Seems very strange as this is a worse benchmark than Vista.

---

