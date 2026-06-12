---
title: "64 bit out of memory with new kernel?"
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jouke74 on 2007-09-06
Yesterday I tried to run Merlin-regress, a statistical genetics program on my Feisty Fawn 64 bit, but the program stopped during the analysis. The statement was that the Kernel killed the proces because of lack of memory. 

I have AMD X2 4200, 2 GB of internal memory and 3 GB of swap (made for this situation).
If I check how many memory is free when the program starts it says about 1.5 GB. 
(Running XGL, Compiz, Avant and more junk).

Now in windows 32 bit XP having about 1.5 GB of memory free plus 3 GB swap, the same analysis runs fine (although much slower). 

The problem is that I compiled the program in 64 bit, and of course one is a windows version and the other one a linux version. My estimate is that it should use about 1.8 GB max. Under linux it seems like the kernel does not allow execution of the program when assigning memory to it, because the memory use goes up for a sec and then drops again with the kill of the program.

My question is, has ony one of you recently used a program that is really memory intensive and experienced something similar? That might be useful to know if I need to switch back to an old kernel or simply check the program compilation.

(I am going to try a Xubuntu live CD to see how that goes ).

---

### Post by kuja on 2007-09-06
I've never had nor heard of that problem before. 

I'm going to go out on a limb and assume something is wrong with the program.

---

### Post by utUtu on 2007-09-06
> **Jouke74 said:**
> Yesterday I tried to run Merlin-regress,....

I have AMD X2 4200, 2 GB of internal memory and 3 GB of swap (made for this situation).
If I check how many memory is free when the program starts it says about 1.5 GB. 
(Running XGL, Compiz, Avant and more junk).



Have you tried running it alone ( no other apps running ) ?

At this point you can add more, or make your swap bigger.  AFAIK, swap should be at least 2x of your memory.

I would love to try it on my box if you could post the data and the .deb package of your program.. if you don't mind.

---

### Post by Jouke74 on 2007-09-06
@ Kuja : Yes I tried running it under failsafe with only the terminal running. The end result was the same error message. 

@ uTUTu : I am afraid that I only have a binary file. The second problem is that the data (althought not useful in the hands of people who do not understand it) is confidential. Hence I cannot give it to someone. 

I assume now, that it is the program that is causing the problem. I tried another program with the same data, and it did not give any problems. That means I need to recompile and find the problem :(

Thanks anyway for your help.

---

### Post by Rui Pais on 2007-09-06
hi,
are you sure that your program is a big memory consumer? usually those kind of programs are very cpu hunger but relatively light on memory (according with today RAM sizes). 
I doubt that even huge amount of data on a single app would exhaust 2G+3G of ram+swap... and that don't even happens on 32 version.

I have run lately  several programs of like (protein folder, Poisson eqs. on large grids, etc.) and  memory is never an issue.  

I would suspect a memory leak on the code. 
If you have access to the code, check any 'malloc' (or 'new' if code is C++) inside loops that don't have a correspondent 'free' (or 'delete'). 
A big loop, as usually appear on this kind of code, that created big arrays (or pointer for that) recurrently but didn't release the space each time, sometimes for millions of function calls, could very easily lead to that. 

good luck

---

### Post by Jouke74 on 2007-09-06
Thanks so much for that information. Yes I have the code, but it's huge and I have not written it. I am quite sure it is a program bug now, since a previous analysis I was doing earlier runs fine. It consumes more than 5 GB of memory if I don't constraint it. 

The progam calculates all possibilities of inheritance for non-independent genetic markers. Of course the first constraint is CPU power, that's why I run these over weekend. The second constraint is memory, as the number of possibilities increases exponentially with the number of family members. All the possibilities need to be stored in memory to calculate the likelihood of a given observation.

---

### Post by Rui Pais on 2007-09-06
> **Jouke74 said:**
> The progam calculates all possibilities of inheritance for non-independent genetic markers. Of course the first constraint is CPU power, that's why I run these over weekend. The second constraint is memory, as the number of possibilities increases exponentially with the number of family members. All the possibilities need to be stored in memory to calculate the likelihood of a given observation.

Well i don't know of course the size that your data is taking with calculation, but seems that 5G is completely insane for any reasonable situation, even huge populations with exponential growth... And you say that the error don't happen with 32bits, so seems to indicate something that 64bit compilers are more sensible dealing with, then the characteristics of the problem analyzed.

An possible way is put prints on each function that print the name of it (if it's C or alike a simple macro makes easier) and run the program from a terminal opened side by side with some memory control tool (configured for a short period checking) like conky or even gnome-system-monitor. You may find the one that make memory use grow by searching for peaks or jumps on graphics if the tool has a GUI and check what it's been called in that moments .

Or you can use ddd (again assuming a C variant of code) to visualize the assignment and values of variables. Some IDEs, like Code::blocks, do that automatically. allowing to go line by line or function by function and watch the value of variables or set breakpoints on suspicious code.

Never an easy task anyway, catching bugs like that.
Good luck, Jouke74.

---

### Post by Jouke74 on 2007-09-07
The memory indeed increases consistently with the time the program runs. 
The algorithm behind it is called the "Lander Green" algorithm.
([http://www.sph.umich.edu/csg/abecasis/class/666.22.pdf](http://www.sph.umich.edu/csg/abecasis/class/666.22.pdf) if you are really interested.)

My pedigree size is max 58... for 800 genetic markers, there lies the problem.

Also geneticists are not professional programmers I guess.

I'll work it out and thanks again.

---

