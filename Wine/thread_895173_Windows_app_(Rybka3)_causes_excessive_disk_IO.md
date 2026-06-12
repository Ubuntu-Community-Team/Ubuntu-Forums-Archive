---
title: "Windows app (Rybka3) causes excessive disk I/O"
date: 2008-08-19
forum: Wine
---

### Post by brunjes on 2008-08-19
Hello,

I have purchased an excellent Windows chess program called Rybka3. It uses chunks of RAM to store evaluations of various chess positions in a "hash table". Virtually all chess programs do this. The strange thing is that when I tell Rybka3 to use 512 MB of RAM for hash tables (I have a Ubuntu-8.04 64-bit system with 3 GB RAM installed and recognized by Ubuntu) and then start Rybka3 off to analyze a position, gnome system monitor shows huge amounts of wait for I/O happening and the disk I/O meter shows huge amounts of disk writes. vmstat shows 90% or more of the CPU time spent in "wa" state (waiting for I/O). I should mention this program is a Windows app that runs under wine. I have installed the latest wine (1.1.2) but that made no difference. I get the same behaviour using Ubuntu 8.04 32-bit as well as OpenSuse 11.0 (I had to try it to see if it would change the behavior but it did not).

free -tm shows zero bytes of swap used. If I specify more RAM for hash table usage than I have RAM installed, I would expect swapping to occur but this is not the case here and as expected, no swap space is being used. Of course while the disk is being hammered, the CPU cycles available to the chess engine are virtually zero and the engine makes almost no progress in its analysis.

It has been documented by the programmer of Rybka 3 that Rybka uses MORE RAM than you give it for hash tables (it should want to use 512 * 2 (I have 2 cores) + 75 MB * 2 (a private table of some sort). But even that is only about 1200 MB of RAM -- much less than I have on my system.

Some Linux users report this problem also, but others say they can set the Hash table size to 512 MB with no such problem. 

Does wine have parameters I can set to make it not do something like this? What about kernel parameters? I've spent more than a week on this problem and have proved to myself I'm not capable of fixing this myself.

Thanks,

Roy

---

### Post by syxbit on 2008-08-21
go to the rybka forum and check out microwine
i think it's supposed to fix this

---

### Post by brunjes on 2008-09-05
Microwine is for running a 64-bit engine and in this case, I'm happy to get the 32-bit engine to run under Linux/wine (if I could address this strange performance hit). I've run the 64-bit engine with microwine and it has the same problem.

I'm going to have to stop using Rybka 3 (having wasted my money) because of this issue. I'm waiting for an improved Toga engine ("Mara") to see light of day -- it promises to be almost as strong as Rybka 3 (we'll see if that really is true) and I've run the previous toga engines for years without such memory issues.

---

