---
title: "Small victory for 64 bit."
date: 2007-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jouke74 on 2007-09-16
I question many doubtful 32 / 64 bit users ask is "how much faster is 64 bit really?" Usually people answer that for things requiring many calculations it is faster, however, not many state exactly what is the improvement. Of course, a lot depends on what programs you're running. So here is some "real" data on how much faster calculations can go:

I am doing statistical calculations with the MX program to get the likelihood of a model with a gene that is responsible for blood pressure and the same model without that gene. One of these calculations takes 15.3 seconds under 32 bit. Under 64 bit the program takes 12.6 seconds. It's the same machine using live CD's of Ubuntu Feisty. So the difference is roughly 2.7 seconds (17%).

Now, that does not seem much of a difference, however I need to do this analysis about 3600 times for different locations on the genome and that makes a difference of 2.7 hours. Usually I test about three of these models, and therefore within such analysis I am saving almost a full working day. 

64 bit does make a difference. :guitar:

---

### Post by jtn on 2007-09-16
Great to hear :)
I wish i would save a day with my x86_64 install but i mostly listen to music wich doesnt really go any faster ;P

---

### Post by saru411 on 2007-09-18
keep up the good work. i feel this type of research might get us all off of the pill popping bandwagon and yes amd64 for the win!

:)

---

### Post by Jouke74 on 2007-09-26
Thanks Saru411.

Some more real data. I have done new calculations using a different program. Here are the results of a single scan in that program under various systems:

AMD X2 4200 2.2 Ghz, Xubuntu 64 Bit, Program compiled for 64 bit time for 1 scan = 40 minutes on 1 CPU.
AMD X2 4200 2.2 Ghz, Xubuntu 64 Bit, Program compiled for 32 bit time for 1 scan = 64 minutes on 1 CPU.
AMD X2 4200 2.2 Ghz, Xubuntu liveCD 32bit, Program compiled for 32 bit time for 1 scan = 61 minutes on 1 CPU.

Intel P4 2.6 Ghz, Windows 32 bit, Program 32 bit, 1 scan = 90 minutes.

My bosses Intel Xeon 3.0 Ghz Quadcore, Windows 2003 server 64 bit, Program 32 bit, 1 scan = 60 minutes on 1 CPU.
My bosses Intel Xeon 3.0 Ghz Quadcore, Windows 2003 server 64 bit, Program 64 bit, 1 scan = 38 minutes on 1 CPU.

Edit: Made an update of the post with more results

:lolflag:

---

### Post by scourge on 2007-09-26
Well, I've written a chess engine which was designed for 64-bit systems. The 64-bit version is about 60 - 80 percent faster than the 32-bit version. So to me getting access to more registers and "native" 64-bit integers is definitely worth it.

---

### Post by Kilz on 2007-09-26
> **scourge said:**
> Well, I've written a chess engine which was designed for 64-bit systems. The 64-bit version is about 60 - 80 percent faster than the 32-bit version. So to me getting access to more registers and "native" 64-bit integers is definitely worth it.

Right now we are just starting to see the 64bit applications written for 64bit appear. Glad to hear it isnt just number crunching applications that will receive a benefit.

---

### Post by scourge on 2007-09-26
> **Kilz said:**
> Right now we are just starting to see the 64bit applications written for 64bit appear. Glad to hear it isnt just number crunching applications that will receive a benefit.

In most cases there's no need for developers to specifically target 64-bit platforms. My chess program is an exception because it cleverly uses 64-bit "words" to represent the chess board (there are 64 squares on a chess board). It's actually a pretty neat and fast trick even on 32-bit systems, but really shines on 64-bit. Many operations that previously needed 2 or 3 cpu cycles now take only 1.

---

