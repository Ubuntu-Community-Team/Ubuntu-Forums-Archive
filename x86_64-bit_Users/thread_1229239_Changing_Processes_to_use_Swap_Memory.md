---
title: "Changing Processes to use Swap Memory"
date: 2009-08-01
forum: x86 64-bit Users
---

### Post by coldReactive on 2009-08-01
Is it possible to force files/processes to use Virtual/swap memory instead of physical memory? If so, how?

---

### Post by QIII on 2009-08-02
Do you have any reason to slow your processes down like that?

---

### Post by coldReactive on 2009-08-02
> **QIII said:**
> Do you have any reason to slow your processes down like that?

I don't want folding@home to take up my physical memory =/ (it takes up about 600 MiB)

---

### Post by movieman on 2009-08-02
The program has to be in physical memory to run. You could change the swappiness setting so that the operating system is more likely to swap out programs to make space for disk cache:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Yellow Pasque on 2009-08-04
Virtual memory is not the same thing as swap. [http://www.redhat.com/magazine/001nov04/features/vm/](http://www.redhat.com/magazine/001nov04/features/vm/)

Also, note that the memory manager keeps as many pages as it can in physical RAM.  Just because F@H reports 600MB in use, that doesn't mean some of that data wouldn't get swapped out if you started to fill all of your physical RAM.

---

### Post by dcstar on 2009-08-07
> **Temüjin said:**
> Virtual memory is not the same thing as swap. [http://www.redhat.com/magazine/001nov04/features/vm/](http://www.redhat.com/magazine/001nov04/features/vm/)
.........

Virtual memory is a combination of RAM **and** "Swap" - the OS has *Virtually* the amount of memory to use that is the sum of the fast memory (RAM) and the slower memory (Swap), it is how well it manages those two resources as to how well it performs whatever purposes it is supposed to.

Active processes need to be in RAM for the processor to have access to them at an adequate read/write rate, when not active a smart OS can "Swap" portions of dormant memory out of RAM to another resource so the RAM can be used for another purpose.

Any BOINC process is almost always going to be running constantly so there is almost nothing that will be moved to swap, unless the available RAM is crowded out by processes running with higher priorities (then the whole BOINC process will be kicked out of the active process list and into Swap).

---

