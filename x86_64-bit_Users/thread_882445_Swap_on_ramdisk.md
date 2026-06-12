---
title: "Swap on ramdisk?"
date: 2008-08-07
forum: x86 64-bit Users
---

### Post by incgnito on 2008-08-07
Hiya I've got a system with 8GB of ram and I figured I'd put 64-bit Ubuntu on it but instead of using a standard swap partition I'd like to see about setting up a ramdisk to use as swap (possibly tmpfs or something else, I'm open to suggestions); I did a general search here and didn't come up with much any ideas?

---

### Post by Jouke74 on 2008-08-07
That is a really bad idea. The swap partition is made to use as an overflow in case your memory is full. With 8 GB this will likely not happen on your computer. However if you would put swap in your memory, then you would basically say to your computer to use the swap "memory" of your PC only in case your (8GB-amount of allocated swap memory) is full. You will loose whatever part of memory you have set as swap memory for nice things like program cache etc.

So don't do it.

You can use your ram for temporary files if you want to. You need to use tmpfs and link your temp dirs to there. Probably there is some manual for that in the Ubuntu wiki.

Or to have quick access to certain data.  Again use tmpfs and copy the data you want to use there. Note that Ram data will be lost as soon as the computer goes of. So **copy** the data really and don't park your mp3 and foto collection on there without a backup.

---

### Post by drumsticks on 2008-08-07
Swap is used as an extension to physical memory. Ramdisk reserves physical memory (it cannot be reclaimed, aka swapped in the conventional sense). Dedicating physical memory to use as swap is rather pointless - you are essentially using one part of physical memory as extension to another part. For example, say you allocated 2GB as swap, then the 2GBÂ*swap extends 6GB of physical memory. You are better off having 0GB extending 8GB.

IÂ*run 4GB without swap. Then if I ever needed it, I can make a new swap file on existing partitions. There is no real need to run a swap partition - you can use swap files just like Windows or OSÂ*X. Having said that, I've never needed to enable swap: 4GB of physical RAM is sufficient for my use.

If you're concerned with disk I/O, set vm.swappiness = 0. This will give you the safety of a reserved swap partition/file on disk, without actually using it until you absolutely have to. I run without this safety net ;)

---

### Post by jpkotta on 2008-08-07
First of all, this makes no sense.  Don't do it.

[http://kerneltrap.org/node/3660](http://kerneltrap.org/node/3660), but it's not what you're talking about.  It's about if you can't fit anymore memory in your mobo.  

Swap isn't just about "overflow".  It's about putting pages that aren't getting used somewhere else, so that the memory can be put to better use.  Say you have a program running in the background that only runs once a day.  There is no reason for it to be in memory most of the time, and it will eventually get swapped out so that the pages can be used as, say, disk cache.  Obviously, we have to trust that the kernel will make good choices about what to swap out and what to keep, and we can bias those choices with /proc/sys/vm/swappiness.

---

