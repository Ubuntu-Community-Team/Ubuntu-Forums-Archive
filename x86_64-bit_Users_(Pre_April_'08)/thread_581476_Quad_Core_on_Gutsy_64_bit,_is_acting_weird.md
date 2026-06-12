---
title: "Quad Core on Gutsy 64 bit, is acting weird"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ConfinedSurrealist on 2007-10-19
Okay so I have been using 7.04 for the last month or so, and I have to say Ubuntu is fantastic. Was able to install my NVidia drivers within minutes, wine + steam, ya-da ya-da. Ubuntu is great.

Now I upgraded to Gutsy, everything went smooth, but I checked system monitor and 1 core was at 70-90% while the rest was at 1-3%. Any idea why Ubuntu would be only using 1 core?

Processor:     Q6600 (Intel quad core 2.4)
MotherBoard: EVGA NForce 680 SLi

---

### Post by shad0w_walker on 2007-10-19
More information about what you were doing would be useful. What program, version, what you were doing in that program, etc.

 It might be that the program you were running wasn't multithreaded for whatever reason or it could simply be that it doesn't require enough processing power to max out that core and so leaves your other cores for all your other tasks.

---

### Post by John.Michael.Kane on 2007-10-19
> **ConfinedSurrealist said:**
> Okay so I have been using 7.04 for the last month or so, and I have to say Ubuntu is fantastic. Was able to install my NVidia drivers within minutes, wine + steam, ya-da ya-da. Ubuntu is great.

Now I upgraded to Gutsy, everything went smooth, but I checked system monitor and 1 core was at 70-90% while the rest was at 1-3%. Any idea why Ubuntu would be only using 1 core?

Processor:     Q6600 (Intel quad core 2.4)
MotherBoard: EVGA NForce 680 SLi

I'm on a dual core setup, and depending on the app one core will have a higher percentage,however. when a high load is applied both cores percentage moves up. This is normal. 

To test simply put the machine under full load, and all core percentages should increase.

---

### Post by stmiller on 2007-10-19
Make sure you have the 64bit smp kernel installed. Do a uname -a in a terminal, and make sure it says SMP. If not, then install that kernel.

All four cores will not be running at all times unless you are running a certain application that  is multithreaded and multi-cpu aware. 

You can open up several terminals and type 
```

yes

```
and enter to get multiple threads going and run up all of your cpus to make sure they are working.

---

### Post by dfreer on 2007-10-19
I'm not entirely confident here, but I think that's normal behavior. I think most programs can only run on one core at a time, they do not evenly spread the load across all cores at the same time. Now, the OS can run mulitple programs on each core (say program A and program B are running at the same time, one program will run on one core and the other on the other core at the same time, whereas with a single core both programs would have to fight for processor time).

As always, I may be wrong.

---

### Post by steveneddy on 2007-10-19
sounds like Beagle doing an initial search. That would be a single core job.

I don't desktop search, so I always uninstall Beagle.

Takes up too much of my precious cpu time.

:popcorn:

---

### Post by ConfinedSurrealist on 2007-10-19
Wow! I knew this forum was fast at answering things but so many replies while I was at work, very cool. :)

To answer some questions:
I was running Firefox at the moment. (I am assuming Firefox is single threaded)
When I ran 4 terminals and typed in 'yes' in each one of them, all my processors went above 50% activity.
It did say SMP under uname command.

You guys are excellent, I think its because Firefox is very well single threaded.
But initially I was worried, because I previously had XP 64 bit installed, and it had the exact same problem and started hanging up because one core was becoming overloaded. Windows just has poor thread management I guess... O.o

Thanks again. :)

---

