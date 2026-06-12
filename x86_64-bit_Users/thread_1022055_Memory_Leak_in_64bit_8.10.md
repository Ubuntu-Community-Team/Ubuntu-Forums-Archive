---
title: "Memory Leak in 64bit 8.10?"
date: 2008-12-26
forum: x86 64-bit Users
---

### Post by aerojad on 2008-12-26
Greetings.

I've been using 32-bit flavours of Ubuntu all the way back to 6.x series.  Recently I put together a new computer for myself that had 8GB of RAM and so I knew I had to go 64-bit to be able to use the memory.  8.10 is the first 64-bit Ubuntu I've used, and after a week or so of using it I'm noticing some really strange things going on with my memory usage.

Then and now I've had Conky running all the time and before my memory usage would hardly ever get over half of the 2GB I had, but now the machine chews through more than 4 of my 7992MB in a little over 12 hours.

I have htop running right now and the top 5 processes are using a combined 8.4% of the RAM, so that'd only be .66 gigs.  I do keep Vuze/Azureus running all the time and before I killed it just now it was single handedly using 5% of the RAM, but that's still only 1.05 gigs.  If I add up all the processes I see in htop, it comes to 18.35% of 7992MB, or 1.43 gigs.  Both Conky and htop see my memory usage stuck at 46 - 50%.  Is this something I need to be concerned about?  How do I figure out where the leak is?  Thank you.

---

### Post by fjgaude on 2008-12-26
From what I know about Unix and Linux, the memory management is such that it uses and places code, data into cache all the memory that is available. Thus you have a really fast system going to disk seldom.

As you use programs they stay in memory, cached. That's the way it is and that way is very good.

---

### Post by soxs on 2008-12-26
One program reports cached data as used memory the other doesn't.
As far as I know, if more memory is needed than available without flushing cached data, the oldest, not used gets flushed until enough space can be given to the program starting up. Gerneally there is always totally unused memory, so the programs can start very quickly.
This makes linux run like a.. well.. there is nothing comparable fast. :D
Plx correct me if I am wrong.

---

### Post by aerojad on 2008-12-26
ahh well if the two of you are right then I won't worry about it :)

---

### Post by wabre on 2009-02-11
...unused memory is wasted memory...

i have nothing against my 4 GB ram being used entirely. why would i want to have 700 MB used and the rest on disk? i want the system to use all my RAM i have so that everything is faster. but memory leaks are only a problem if the system gets slower because ....it leaks... :confused:

---

