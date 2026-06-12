---
title: "ie4linux takes too much ram on xubuntu 64"
date: 2009-02-13
forum: x86 64-bit Users
---

### Post by lnthai2002 on 2009-02-13
Hi guys,

I wonder if any one has experienced an large amount of RAM consumed by IE on a xubuntu x64 (installed with ie4linux). From the moment i start ie the used RAM is increasing non stop every haft a second and eventually eat up all my ram then swap files. I googled around but it does not seem that anyone has reported memory leak on IE. So here i am the first asking for help.

Hope anyone has something to share
Thai

---

### Post by badpointer on 2009-02-24
Hi lnthai2002,

have you got a solution to the mem leak of ie4linux?

We see the same symptoms with 8.04 (hardy) on Intel Duo. The memory leak starts  as soon as a https://  session is involved and remains even the IE has been closed. (The IE is still running as process). Together with memory wasting the CPU is at 100%. (Reported also from other people:  [http://www.winehq.org/pipermail/wine-bugs/2008-March/098295.html  ]("http://www.winehq.org/pipermail/wine-bugs/2008-March/098295.html") or Bug [https://bugs.launchpad.net/bugs/205895](https://bugs.launchpad.net/bugs/205895)  .  Killing the IE process stops the symptoms but most the time you have kill the wine service as well in order to get the IE back running.  
My next step is to follow the directions in [http://bugs.winehq.org/show_bug.cgi?id=13734](http://bugs.winehq.org/show_bug.cgi?id=13734)
using another version of wine and see what happens in terms of memory leaks.

I need this fixed because we do long term downloads from the MSDN subscriber site
and we don't want to deal with virus protection all time.

Please let me know if you found a solution in the meantime. 

best regards

---

### Post by lnthai2002 on 2009-02-24
hey pointer,
I havent found any solution yet. I have Intel Core2 Duo CPU T8300  @ 2.40GHz runnung on my laptop, despite the fact that all of my RAM and swap files are used up, CPU usage is still low (<40% for both core).

---

