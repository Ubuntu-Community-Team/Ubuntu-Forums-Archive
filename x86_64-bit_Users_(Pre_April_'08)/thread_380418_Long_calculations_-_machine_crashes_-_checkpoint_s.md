---
title: "Long calculations - machine crashes - checkpoint software?"
date: 2007-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Floren on 2007-03-09
Hi,

I run some calculations in parallel on a 2 processor double core AMD64 (with Ubuntu, 2.6.15-28-amd64-generic) and for some reason the computer crashes from time to time.

The problem is these calculations sometime take more than a day and I lose everything when the computer crash. Obviously, this makes me quite... unhappy.

I heard there is 'checkpoint' software that could help me with this. Anyone knows about a good checkpoint program that could work or maybe another alternative?

Thanks a lot,
  Floren

---

### Post by spin2cool on 2007-03-10
Are you monitoring your process -- Is the machine running out of memory?  

Have you tried running memtest to rule out memory/load issues?

---

### Post by chalex on 2007-03-10
Yeah, perhaps you should figure out the cause of the crashes.

As for checkpointing, the software has to support it.  For example, the folding@home client writes out its results to disk every 15mins.  You could modify your software to do the same.

---

### Post by Floren on 2007-03-11
Hi,

Thanks for the answers.

I don't think the memory is the issue. I noticed sometimes there is an 'atievent' that is using 100% of one of the processes and I have to go and kill it myself. I'm afraid the real problem may have to do with the graphics card (?)

In any case, I'm more concerned about software that could help me to run those long calculations. I didn't write the software, and modifying it would require a really MAJOR effort which I don't think is worthy at this point...

Thanks,
    Floren

---

### Post by Jouke74 on 2007-03-13
The big question is, what software? and what does it do when it  crashes?
Was it compiled under Ubuntu?

---

