---
title: "Dual core 64-bit CPUs not fully utilized..."
date: 2007-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tonohono on 2007-04-23
Howdy,

As far as functionality goes, I've had no issues with running 64-bit Feisty on my machine.

However, I don't believe my dual core processor is being utilized to its fullest potential. When running *any* highly CPU-intensive process, the two cores will never both reach 100% CPU load, though the total load of each core will add up to roughly 100%.
I hope this graph helps explain.
[IMG]http://sadisticslinky.com/crap/cpuload.jpg[/IMG]

When running a CPU-intensive process, I would expect both CPUs to be at 100% load to achieve maximum efficiency. Is this a limitation with Linux, or is their something I can do in order for Ubuntu to fully utilize dual core processing power?

Thanks for the help!

---

### Post by solidunit on 2007-04-23
if you're running one very demanding single-threaded process, then you will only see one CPU being utilized.

Only if the process is multi-threaded will you see one process utilize multiple CPU's.

I would say most applications in general are single threaded.

---

### Post by Tanker Bob on 2007-04-23
I was too slow in typing.  What solidunit said...

---

### Post by SL666 on 2007-04-23
Its the same in XP, except that your other CPU looks busier because its working harder just to keep things running.

Try running two intensive applications like the other guys said, as long as they aren't trying to both thrash the disk, the load should be much higher... I was thinking about trying this myself.. except i can't think of two processes to run :P


Cheers Steve.

---

### Post by Ocxic on 2007-04-23
2 instances of glxgears will utialize both cores, at almost 100% try it out.

---

### Post by SL666 on 2007-04-24
[http://www.sl666.net/misc/screen.png](http://www.sl666.net/misc/screen.png)

worked for me.. ~93% each... playing mp3's too.. 

Athlon 64x2 4200+

---

### Post by Jouke74 on 2007-04-24
Technically speaking the two CPU's cannot be using 100% of their capacity as the AMD X2s share the memory & memory controller part of the processor. However this effect is very small.

---

### Post by nyinge on 2007-04-24
You'll also be utilizing full capacity of multiple cores if you add the "-j#" to the "make" command, where # = 2 * num of cores, when you compile.

---

