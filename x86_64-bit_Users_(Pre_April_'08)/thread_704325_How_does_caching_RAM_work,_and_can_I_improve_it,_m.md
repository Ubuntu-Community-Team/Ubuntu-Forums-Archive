---
title: "How does caching RAM work, and can I improve it, manually?"
date: 2008-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by aresnick on 2008-02-22
So I've looked for straightforward information on how caching works for a while, to no avail.  Essentially, my question is this: given that using memory as a cache improves performance, why doesn't Ubuntu (I'm running 7.10) use as much memory as possible as a cache?  For instance, currently 22% of my memory is in use by programs, and another 33% as cache.  Why not 78% as cache?

I'd appreciate a point in the right direction; I'm sure this information is out there, already.

Thanks!


Gratefully,
a.

---

### Post by fjgaude on 2008-02-22
Well, I think it does by default design, if you load enough programs to use up the memory. At least that the way it seems on my computer. I see cache sizes that use all the available memory I have, 2 G.

---

### Post by chrisccoulson on 2008-02-22
With enough uptime and if you run enough programs, then it will eventually use all remaining RAM as cache. Mine uses all remaining RAM within a few hours normally.

---

### Post by aresnick on 2008-02-22
Right, I can achieve this as well.  I guess I was hoping there was a way to do so directly (not just as a byproduct of program use).

Thanks!

---

### Post by fjgaude on 2008-02-22
Maybe you were thinking of setting up a RAM disk... cache is just that, cache, not a RAM disk. You have to use a program and its data before it can be stored in memory.

---

### Post by chrisccoulson on 2008-02-23
> **aresnick said:**
> Right, I can achieve this as well.  I guess I was hoping there was a way to do so directly (not just as a byproduct of program use).

Thanks!

Thats what caching is. What you're probably thinking of is *preloading*, where you preload commonly used libraries before you need them. There is a program in the repositories called 'preload', which can do this. I've used it before, but never noticed any gains out of it, so I got rid of it again.

---

### Post by Yellow Pasque on 2008-02-23
What output do you get for this command?
```
free -m
```

---

### Post by aresnick on 2008-02-23
total       used       free     shared    buffers     cached
Mem:          3884        781       3103          0          9        155
-/+ buffers/cache:        617       3267
Swap:         6236        510       5726

---

### Post by aresnick on 2008-02-23
I see.  Hmm, I'm still a little confused: when I open an application, and my machine caches RAM on its behalf, does this memory get uncached when I close the program?  I was under the impression that it didn't, that cached RAM can only increase.  If that's the case, then cached RAM would seem to not need to be connected to a specific app.  Preloading doesn't sound like what I want (but I'll play around with it--thanks!).  I want to be able to tell my machine, "Use 80% of the memory as cache," without needing to open programs to request it.  Does that make sense?

Thanks so much for your help!

---

### Post by chrisccoulson on 2008-02-23
When you open a program, that program may be cached after you close it so that it doesn't have to be read from disk next time you open it. While it is true that the size of the cache may increase as the uptime of the machine increases, there are times when the cache size will decrease - for example, if you're running low on RAM and that RAM needs to be freed up to be used for something else. In this scenario, the kernel may shrink the cache size to free up RAM, or swap out used RAM to your swap partition (whilst maintaining the cache size). The behaviour of this can be determined by the kernel *swappiness* value, which can be set from between 0 (always shrink cache size in favour of swapping) to 100 (always swap in favour of shrinking cache size)

The cache is not a fxed size - nor can it be set to a fixed size (80%, as you say). The cache size will vary, depending on what is cached. Things are only cached as you use them, so, you can't just say 'use 80% of my RAM as cache'. The beauty of cache, is that it is effectively *free* memory, and can be freed up at any time if needed by a running application. If you say 'use 80% of my RAM as cache', then what you're saying is 'reserve 80% as cache and leave me 20% for everything else'. In this scenario, your 'cache' is now 'using' your RAM and cannot be freed up by applications that need it. You're then just using RAM for the sake of using it, whilst running programmes suffer with less RAM.

What you *can* do though, is *preload* things that are used regularly, so that they reside in RAM before you need to use them.

I hope this all sort-of makes sense.

Have a look at this: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

---

### Post by Yellow Pasque on 2008-02-23
I'm sorry, but I don't quite understand what you want to do.
See if this clears things up for you: [http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/](http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/)

---

### Post by aresnick on 2008-02-24
Awesome; that makes sense, now.  And thanks for the link--that helped a lot.

I get it!

Gratefully,
a.

---

### Post by Jouke74 on 2008-02-24
To explain a small thing still here :lolflag:

If your memory is 2 GB and your system plus your Firefox eat about 500 MB. After you close Firefox it would be silly for the computer to suddenly eat up 2 GB if originally only 500 MB was used... That's why with more programs the cache memory slowly runs full.

A 300 MB file will be cache into memory once loaded. If you need to take out various lines with a grep command you will usually get disk access only the first time. The rest of the times it is cached. You will see that it is way quicker, and also helps your harddrives survive.

A ramdisk you can use if you want to make sure that the file is "cached" permanently. However, in this case you will have two copies if this file in memory. Once in the Ramdisk, and one in the cache (I assume that the ramdisk is also cached).

---

### Post by randiroo76073 on 2008-02-25
I'm running 4gb ram[soon to 6gb] so increasing the "swapiness value" would increase  the amount of prgms kept in ram ?  I just built this machine, I don't game so I'm not looking for that, but do want to run prgms like: Celestia, Google Earth and some video/photo editing[got stuck being family history archivist] .  Would increasing to, say 50% swapiness give me any advantages or just leave at default ? 

Specs:
ASUS M2A-VM
AMD Athlon 64x2 5600
4[6]gb PC6400 ram
ATI X1250[onboard] 1024mb shared ram
rough est. of available ram will be 4.25-4.50gb
No OC'ing, stock values

---

### Post by chrisccoulson on 2008-02-25
> **randiroo76073 said:**
> I'm running 4gb ram[soon to 6gb] so increasing the "swapiness value" would increase  the amount of prgms kept in ram ?  I just built this machine, I don't game so I'm not looking for that, but do want to run prgms like: Celestia, Google Earth and some video/photo editing[got stuck being family history archivist] .  Would increasing to, say 50% swapiness give me any advantages or just leave at default ? 

Specs:
ASUS M2A-VM
AMD Athlon 64x2 5600
4[6]gb PC6400 ram
ATI X1250[onboard] 1024mb shared ram
rough est. of available ram will be 4.25-4.50gb
No OC'ing, stock values

Increasing the swappiness is probably the *wrong* way to go. The effect of that will be that when your free RAM is running low, the kernel will favour swapping out pages instead of shrinking the cache size. This will cause responsiveness to drop right off. There is little benefit in maintaining your cache size when programs are running out of physical RAM and are having to be swapped out to disk.

I have 2GB of RAM, and I have my swappiness set to 0, so the cache size is always shrunk in favour of swapping out pages.

---

### Post by randiroo76073 on 2008-02-25
Thanks Chris, I was kinda leaning that way, just some leftover MS crap I evidently hadn't gotten rid of in my head.  Linux handles resources 100 times better than MS on their best day :)

---

