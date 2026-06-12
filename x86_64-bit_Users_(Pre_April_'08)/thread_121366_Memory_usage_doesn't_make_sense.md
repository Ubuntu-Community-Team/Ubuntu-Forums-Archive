---
title: "Memory usage doesn't make sense"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by kripkenstein on 2006-01-25
I just moved from 32 bit to 64 bit, and something odd is happening. Top reports that 'java' is using 1.5 GIGABYTES of virtual memory (VIRT) - which is more physical + virtual memory than I have! A few other programs also have ridiculous values in the VIRT column. The RES column seems fine though, and applications all seem to work. When I check memory usage (free), I am using 600 megabytes (400 physical + 200 swap).

Can anyone please explain this?

---

### Post by d1337 on 2006-01-25
oops...shouldn't have replied so quickly before reading the post more closely.  My apologies...

Could you post the outputs for us to see?

d1337

---

### Post by kripkenstein on 2006-01-25
[QUOTE=d1337]oops...shouldn't have replied so quickly before reading the post more closely.  My apologies...

Could you post the outputs for us to see?

d1337[/QUOTE]

Sure, I guess I should have done that in the first place, sorry. Here: top starts with

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
11917 food      17   0 1576m 198m  26m S  3.7 40.0  25:05.00 java

```
while free gives me
```

             total       used       free     shared    buffers     cached
Mem:        508784     503576       5208          0      23588      98040
-/+ buffers/cache:     381948     126836
Swap:       939760     212892     726868

```

---

### Post by doclivingston on 2006-01-25
The "virtual memory size" doesn't mean what you think it means - it's the size of the application's address space. That includes a *lot* of things that don't take up actual memory.

A reasonable approximation to how much memory an application is using is "Resident + Swapped - (Some of)Shared".

---

### Post by d1337 on 2006-01-25
From man top
     ```
 o: VIRT  --  Virtual Image (kb)
          The total amount of virtual memory used by the  task.   It  includes
          all  code,  data  and  shared  libraries  plus  pages that have been
          swapped out.

          VIRT = SWAP + RES.

       q: RES  --  Resident size (kb)
          The non-swapped physical memory a task has used.

          RES = CODE + DATA.

```
The words "have been" and "has used" makes me think that this is a running total of memory used, thus the inflated numbers most likely after some java apps have been executed.  I haven't paid as much attention to this before, but I appear to have some crazy VIRT values as well.  Hope that helps.

d1337

---

### Post by kripkenstein on 2006-01-25
Thanks d1337 and doclivingston, but things still don't add up.

Hmm, reading the SWAP man I see
```

SWAP  --  Swapped size (kb)
          The swapped out portion of a task's total virtual memory image.

```

So, this plus your quote d1337, still leaves me confused. doclivingston, you say that the "virtual memory used by a task" means "address space", and not memory actually used? If so, the man page seems misleading to me.

So, RES is the physical memory used. Then what is the name of the field of 'memory actually used, but swapped out' - i.e. that actually takes up room in virtual memory (but just not in physical memory)? If you're right, doclivingston, then there is no such field to view in top? (it's not SWAP nor VIRT)

Trying to use your formula of "resident + swapped - (some of)shared", I still can't make sense of things. Look at this:
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  SWAP COMMAND
11917 alon      15   0 1576m 203m  26m S 14.3 41.0  30:48.23 1.3g java

```

Here resident + swap - shared is equal to 1.5 gigabytes. Which is equal to VIRT, more or less. So again, I have a program that uses more memory than physical + swap... it just doesn't add up :(

---

