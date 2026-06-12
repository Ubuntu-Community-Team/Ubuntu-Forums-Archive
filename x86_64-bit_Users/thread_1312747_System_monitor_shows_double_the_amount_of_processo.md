---
title: "System monitor shows double the amount of processors"
date: 2009-11-03
forum: x86 64-bit Users
---

### Post by Suiname on 2009-11-03
I have a user who has a 64-bit workstation that has 2 Xeon X5550 processors in them.  These processors are quad cores.  Since there are 2 of them, that should total 8 processor cores.  The previous version of ubuntu (64-bit 8.04) showed 8 processors (as I expected it to), however, after upgrading to 64-bit 9.10, it now shows 16 processors in the gnome system monitor.  Is this just incorrect, or is something else going on here?  Any help is much appreciated

---

### Post by sanderj on 2009-11-03
Your CPU's have HyperThreading, I guess. That doubles the amount of CPU's in your system monitor.

---

### Post by Suiname on 2009-11-03
Thanks, I think that answers my question.

---

### Post by tgalati4 on 2009-11-03
It's nice how linux doubles your processing power with little work on your part.

---

### Post by Suiname on 2009-11-03
I believe you can only take advantage of hyperthreading if your application is specifically coded to do so though, so it doesn't double up everything.

---

### Post by insane_alien on 2009-11-03
if the program is multi-threaded then it works with hyper threading. 

if its single thread then it will use a single thread of a core. but you can run more instances without slowdown.

---

### Post by sanderj on 2009-11-04
About this subject:

My Atom N270 netbook also shows two CPU's in 9.10's System Monitor: single core CPU with hyperthreading. A bit silly: I don't think HT does extra performance like an extra core does.

So I asked myself: how can I see the difference between real cores, and HT-fake CPUs? I think I have found the answer in dmesg:

First my Core Duo, with two real core on one die:

```
ubuntu@ubuntu:~$ cat dmesg.core-duo.txt | egrep -i -e "Processor Core ID" -e "Initializing CPU" -e "Physical Processor ID"
[    0.000000] Initializing CPU#0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] Initializing CPU#1
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: **1**
ubuntu@ubuntu:~$ 
```

And my N270 single core with HT:

```
ubuntu@ubuntu:~$ cat dmesg.samsung-nc10.txt | egrep -i -e "Processor Core ID" -e "Initializing CPU" -e "Physical Processor ID"
[    0.000000] Initializing CPU#0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] Initializing CPU#1
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: **0**
ubuntu@ubuntu:~$
```


Conclusion / hypothesis: if the "Processor Core ID" of the second CPU ("CPU#1") is 1 (or: 1 higher than the previous core), it's a real core. If it's 0 (or the same as the previous core), it's just HT.

---

