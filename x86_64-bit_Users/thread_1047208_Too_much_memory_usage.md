---
title: "Too much memory usage?"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by tomitzel on 2009-01-22
Hi guys,
I've upgraded to 8.10 64bit and I've noticed that it takes 500 mb RAM when no application is opened and no visual effect activated (only a theme).
When I use my laptop normally, the average used memory is 1.3 GB from my 2 GB.

[IMG]http://i70.photobucket.com/albums/i104/militarutomita/memory.jpg[/IMG]

Isn't that too much? Might it be 'cause I'm using the 64 bit version?

Thanks.

---

### Post by binbash on 2009-01-22
what is the output of free -m command ? Linux and windows have different ram management.Do not think the windows way.

---

### Post by tomitzel on 2009-01-22
```
             total       used       free     shared    buffers     cached
Mem:          1881       1845         35          0         15        810
-/+ buffers/cache:       1019        862
Swap:         1011          5       1005

```

This is while using my computer and some applications are opened.

---

### Post by jocko on 2009-01-22
It's perfectly normal for linux to use most of the ram (unused ram is wasted ram).
Things that are no longer used remains in ram in case they are needed again later.
If another application needs more ram, unused data gets overwritten.

If you would have "too much" memory usage (i.e. if unused bits would not be overwritten with new things, or if a program leaked memory) you would see lots of swap usage, which would slow down your computer...

---

### Post by tomitzel on 2009-01-22
Thanks Jocko!
I think this is something like Vista's superfetch :D

---

### Post by johnjohn2 on 2009-02-04
> **jocko said:**
> It's perfectly normal for linux to use most of the ram (unused ram is wasted ram).
Things that are no longer used remains in ram in case they are needed again later.
If another application needs more ram, unused data gets overwritten.

If you would have "too much" memory usage (i.e. if unused bits would not be overwritten with new things, or if a program leaked memory) you would see lots of swap usage, which would slow down your computer...

i concurr

---

### Post by OrangeCrate on 2009-02-04
**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go? 

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

