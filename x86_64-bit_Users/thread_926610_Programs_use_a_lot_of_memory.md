---
title: "Programs use a lot of memory"
date: 2008-09-22
forum: x86 64-bit Users
---

### Post by obsrv on 2008-09-22
When I launched KInfoCenter, I saw that half of my memory is used. I have 8GB of RAM, I noticed that every app uses about 100-800mb of ram. Here is a screenshot: Is this some kind of prefetching feature of what? Using KUbuntu 8.04.1 AMD64

---

### Post by Greyed on 2008-09-22
First off ignore virt and look at res.  VIRTual memory is, well, I dunno what it is.  I'm more concerned with RESident memory.  Second, look at 2 lines up top that describe where the memory is.

4.9Gb used, 3.2Gb free.  But 1.8Gb of buffers and 2.5Gb of cache.  So 4.3Gb in buffers+cache, most of which can be freed up for programs if needed so are, effectively, free.  Which is why when you use free on the command line the second line shows you what your free memory would be with buffers+cache added in...

```

{grey@igbuntu:~/bin} free -m
             total       used       free     shared    buffers     cached
Mem:           376        358         17          0          8        105
-/+ buffers/cache:        244        131
Swap:          391         72        319

```

---

### Post by annatar on 2008-09-22
hmm...for the actual amount of SWAP and physical RAM used up, see %MEM or RES+SHR, but NOT VIRT
 
as for what is 'virtual memory'...
 
basically it is a technique to trick applications into 'thinking' it has contiguous working memory, which in fact maybe physically fragmented or may even overflow to other storage devices
 
Just ignore that reading

---

