---
title: "[SOLVED] 4gigs RAM... iommu=noaperature no yield"
date: 2008-12-11
forum: x86 64-bit Users
---

### Post by rbprogrammer on 2008-12-11
Basically this is one of those "I have 4GB of RAM, and Ubuntu only sees 3.2GB" threads.

I tried putting that iommu=noaperature in the kernel options in grubs menu.lst.  But Ubuntu still only reads 3.2GB.

Where can I find out how to fix this?

---

### Post by TheAL76 on 2008-12-11
Even with 64 bit installed?

---

### Post by rbprogrammer on 2008-12-12
Yup, sorry I must of forgot to mention that.  I have 64-bit Intrepid Ibex installed.

Usually I install the 32-bit version.  But I decided to try and convert to 64-bit when Ibex came out.  And the 64-bit has been must smoother for me this time around.  The only problem I am really having is a few media player "skipping" things, not a big deal.

But I really wanted my all 4GB of RAM to be recognized.  I mean I don't normally use a whole bunch of RAM, but it would be nice to get this ironed out since some of my computer science courses in college require us to develop simulators that are usually resource hogs (just to demonstrate concepts).

---

### Post by rbprogrammer on 2008-12-12
From when the last time I tried using a 64-bit version of Ubuntu and trying to get the 4GB of RAM to be recognized, I had to change something in my BIOS.  That had no yield before, so I disabled it.

But this time around, I enabled in my BIOS something called "Memory Hole Remapping".  With that enabled and the iommu=noaperature on my boot parameters, the system monitor says 3.9GB.  I can then confirm it with:
```

$ free -t
             total       used       free     shared    buffers     cached
Mem:       4055632     586816    3468816          0      14996     225344
-/+ buffers/cache:     346476    3709156
Swap:      1004020          0    1004020
Total:     5059652     586816    4472836

```

So to me, it looks like all of my 4 sticks of RAM (1GB each) are all recognized.

---

