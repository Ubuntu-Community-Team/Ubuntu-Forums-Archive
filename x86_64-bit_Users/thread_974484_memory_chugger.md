---
title: "memory chugger"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by christoforever on 2008-11-07
So I should not have been surprised and yet I still was.. After installing a fresh 64 bit version my memory usage has more than doubled. I suppose that has been said somewhere and I do believe i've read it somewhere as well. But is this normal? That much memory?

---

### Post by dabl on 2008-11-07
> **christoforever said:**
> So I should not have been surprised and yet I still was.. After installing a fresh 64 bit version my memory usage has more than doubled. I suppose that has been said somewhere and I do believe i've read it somewhere as well. But is this normal? That much memory?

Sooo ... you're thinking this is a _bad_ thing?  Why? -- you paid for it -- it should be put to use!  :)


Seriously, how do you know more is being used, i.e. more than what?

---

### Post by christoforever on 2008-11-07
Under system monitor I went from, on a fresh boot, to having an initial 350 mb of ram used, with 64 bit, on start up im using 745. Not that i have any complaints, things are working great, its just chewing more memory. And I have it to spare, it just seemed like a big jump.

---

### Post by wfp on 2008-11-08
wayne@MyUbuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1887        453       1434          0         11        233
-/+ buffers/cache:        207       1679
Swap:         2588          0       2588
wayne@MyUbuntu:~$ 

This is my ram usage on amd64-bit. You could turn off some services at startup if you are not using them. That might free up some ram for you.

---

### Post by dabl on 2008-11-09
The bottom line on memory management is, Linux and Windows are exactly opposite and you can't look at it the same way.

In Windows, if you "run out" of memory, it's BSOD time.  So you always want unused memory available in Windows.

In Linux, unused memory is wasted memory. Memory that isn't needed for process execution is assigned to "cache", up to a point.  If it happens that physical memory is fully consumed, it uses swap space on the disk.  Only if you run out of swap space will you suffer significant performance degradation.  No BSOD.

---

