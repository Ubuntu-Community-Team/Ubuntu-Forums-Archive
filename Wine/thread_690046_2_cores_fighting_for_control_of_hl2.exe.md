---
title: "2 cores fighting for control of hl2.exe"
date: 2008-02-07
forum: Wine
---

### Post by Drone4four on 2008-02-07
When I play Counter-Strike Source (hl2.exe) through wine, the process swings back and forth between my 2 cores with a steady, uninterrupted rhythm.  It's as if the two cores are fighting for control.  Why is this? And what can I do to move hl2.exe to run on 1 core only? 

See attached for a screen shot of gnome-system-monitor.

---

### Post by Melhisedek on 2008-02-07
I noticed the same thing, I play mostly with bots and I thought it had something to do with AI... can't get online as game freezes, but bots work no problems

---

### Post by happyhamster on 2008-02-07
You can set cpu affinity for core 1 like this:

taskset -c 1 wine hl2.exe

But in your case, it will likely max out that core (I think), so performance could be worse. See:

man taskset 

for more info.

---

### Post by Ferrat on 2008-02-07
you might want to check out changing or removing any cpu scaling that you have installed, I had similar problem with WoW, the preformance was worse than with my old system and the workload kept jumping back and forth and it became unstable. 

I removed all the cpu scaling ect and the problem went away

---

### Post by Melhisedek on 2008-02-07
How do you do that? Remove cpu scaling? What is it anyway :)

---

### Post by shad0w_walker on 2008-02-07
As far as I understand it this is normal behavior, the kernel moves intensive tasks to the core with the least overall load, which ends up swinging processes back and forth between the cores. I don't see however why you would actually care. It doesn't make any difference to performance and it's certainly isn't getting in your way, my advice is let the kernel do what it wants to, in the grand scheme of things it knows what's best for the system.

---

### Post by jrharvey on 2008-02-07
I am not a gamer but i have noticed this with my Rendering program. The cores switch back and forth  from 100% to 0% and back. Can you not use both at the same time?

---

### Post by shad0w_walker on 2008-02-07
Wine is only capable of using one core per process at the moment, a sad limitation but I haven't been stung by it noticably. Hopefully they can figure something out about that but right now more work on the APIs is a better focus as the multicore thing is barely in existance outside of special areas (Gaming and heavy duty processing like rendering)

---

### Post by jrharvey on 2008-02-07
> **shad0w_walker said:**
> Wine is only capable of using one core per process at the moment, a sad limitation but I haven't been stung by it noticably. Hopefully they can figure something out about that but right now more work on the APIs is a better focus as the multicore thing is barely in existance outside of special areas (Gaming and heavy duty processing like rendering)

ahhhhh i understand. You know the weird thing is that I can render an image faster in wine than on the same computer running windows natively.

---

### Post by killermist on 2008-02-07
The way I understand multiprocessing to work (which I may admit may be wrong), you can only take proper advantage of multiprocessing if:
1.)  The OS is designed to make use of both processors (extremely likely with modern Linux kernels, unless you've intentionally disabled it, probably on a machine with only one processor)
2.)  The most processor intensive tasks you run were designed in a multi-threaded manner to take advantage of multiple processors.  

Almost all full-screen or 3d accelerated windows games are designed to consume as much processor speed as possible to keep rendering and responsiveness as smooth as possible.
Because of the nature of the task being single threaded, it can use a maximum of 100% of a single processor.  On a dual processor machine, the usage of this looks odd because the process will flip and flop between processors because of context switching (the OS and Processors working together to do task scheduling and switching).  It's not that the cores are fighting for control.  That's just the task flipping and flopping from one CPU to another.  And there's nothing wrong or harmful about it.
Because the program is running as a single thread, it just isn't capable of running on both CPUs simultaneously.  The best that can be done is for the task to flip and flop between CPUs.
Multi-threaded programs launch 2 or more threads that run until completion, and are not intended to rely on the result of any other already-running thread for input.  This allows the task to use processor usage efficiently.  Programs that transcode video and/or audio tend to be multi-threaded because they are good at breaking the task down into small tasklets that can be easily threaded.

As far as I know, there is no way to "fix" a program that is single threaded to use more processors.  But, having multiple CPUs (or cores) is still an asset because there's a likelyhood that your system daemons and other small usage tasks will likely gravitate to the CPU that's under less overall load when the scheduler schedules them to run.

As I said, I don't claim to be an expert on multiprocessor things, but from having run a P3/1Ghz Dual processor system back in the days of Windows 2000, this is my experience.
I hope this helps some.

---

