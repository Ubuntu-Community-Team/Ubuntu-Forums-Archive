---
title: "Just Curious about something regarding multicore support"
date: 2007-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bobbwhy on 2007-12-10
This is a question out of curiosity... 
I just upgraded from Fedora 6 to Ubuntu 7.10.. using an AMD 64x2 4200.

I have written some heavily recursive code in Python to test ideas for later, more difficult code.  This code is not written with threading or processes at all.. Just typical sequential coding.. lots of recursions.

When I wrote similar code on Fedora 6.. and would watch the system monitor while it ran.. one cpu core would spike for a bit while the other just sat there.. NOW.. on Ubuntu.. both CPU cores spike.. 

Not to sound ungrateful.. but .. how is this possible?  in Fedora 6 and Ubuntu.. running python 2.5.. 

My guesses are: 
1. Somehow the kernel is offloading processes from one cpu to the other to clear space for the python code to run on one... This sorta makes sense.. but prior to running this, very little else was running.. One cpu was at 6% load the other at 3%.. While running the python code..... both processors were running between say.. 65 and 100%.. 

So.. for this possibility to be true.. one processor running tasks is like 10x less efficient than two sharing the tasks.

other guess: 
2. Somehow the kernel is threading my single-thread python app? .. .. The recursions I am pretty sure could run in parallel ... 

So.. My question is: where is this happening?  Why not on Fedora 6?  This code is similar , but not identical to what I was using on Fedora, but Fedora is pretty much gone now.. I might try testing some of the older code on Ubuntu.. 

Meanwhile.. did some little load-sharing miracle occur in the last year? 

and if somehow the kernel is doing some kind of load-sharing.. how much is to be gained by using something like parallel python.. or other more explicit load-sharing instructions.

Thanks for indulging my curiosity.
Robert

---

### Post by Jouke74 on 2007-12-10
Which version of Fedora Core 6 were you using the 32 bit or 64 bit version? If you have used the 32 bit version I can understand. The AMD 64 bit version of Ubuntu is still Debian based, and at Debian it shows this at the site:

A complete 64bit userland

The AMD64 port is thoroughly 64bit, allowing the user to benefit from all advantages this architecture has compared to i386:

    * no memory segmentation in low and high memory
    * up to 128TiB virtual address space per process (instead of 2GiB)
    * 64TiB physical memory support instead of 4GiB (or 64GiB with the PAE extension)
    * 16 general purpose registers in the CPU instead of 8
    * gcc defaults to SSE2 math instead of 387 FPU
    * gcc omits frame-pointers by default at -O2
    * compilation time optimization uses a common base for AMD64/EM64T instead of legacy i386 cruft
    * memory pages are not executable by default

And I think that the -O2 parameters and the SSE2 instructions make your indeed make your recursive program go into multithreaded mode.... The thing is that it is done for GCC and not for Python as far as I can tell :-k Hmmmmm

---

### Post by bobbwhy on 2007-12-10
Thanks for the answer.. very complete in fact.  Now I will have to head over the a tech manual to understand everything.. but I think i get part of it.. 

I was pretty sure the fedora was 64 bit ... .. maybe it was not installed correctly.. or maybe the code I wrote for that had recursions that affected the outcome of the pending recursions and was therefore more sequential.. Will have to look it over again.. or try it on new install..

I can't believe the kernel would have so fundamentally changed in about a year.. but maybe it did 

As for Python getting mutli-threaded.. i am guessing this is a result of it compiling to C at some point.. but at this point I can't do more than speculate.

In any event, I must say, I am enjoying Ubuntu very much..  Can't wait till someone posts a fix for the flashplugin-nonfree so I can stop using my old powerbook

---

### Post by saru411 on 2007-12-10
> **bobbwhy said:**
> Can't wait till someone posts a fix for the flashplugin-nonfree so I can stop using my old powerbook

there are a few options for flash. one is to install and run a 32 bit browser with flash([http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)). this is the option i use until java 7 comes out with proper browser support. there is also a nice addition to our open source community called java iced tea. this can be found in restricted drivers i believe. then there is also the unsecured java blackdown option, which i do not recommend. look for posts by forum java guru Kilz. his posts will make getting java applets/flash working simple and pain free.

---

### Post by CowsCanFly on 2008-01-28
> **bobbwhy said:**
> 
.... While running the python code..... both processors were running between say.. 65 and 100%.. 


That **IS** strange, are you sure?. Python by itself **cannot** take advantage of the second core unless you are using some mpi port like mpi4py, mympi etc. Look up GIL to see what I mean.

Is your prog running faster or slower on Ubuntu? (numbers, not *"feels like"*, please) could it be that the kernel is switching between procs very fast? (then it should run slightly slower).

---

