---
title: "[Waiting for headers] apt-get update"
date: 2009-06-20
forum: x86 64-bit Users
---

### Post by televisi on 2009-06-20
Hi All,
are you experiencing "[waiting for headers]" long process today?

I'm doing "sudo apt-get update" from Ubuntu server 8.04 64 bit version, and it's taking me almost 2 hours...

My original source is Australia, but then I remove "au" in front of the site, still very slow...

Ps: this is only happening in Ubuntu server 8.04 64 bit version, the other Ubuntu server 8.04 32 bit version is okay...

---

### Post by MrHyde on 2009-07-10
Hi, 

Did you find a fix to your problem.  I am experiencing the same today on my AMD 64 bit machine as well.  I have also tried removing the au. from the sources, but no change in behaviour.

Cheers.

---

### Post by televisi on 2009-07-11
Hi,
My problem was with my Gigabit NIC card (Click here for [Thread]("http://ubuntuforums.org/showthread.php?t=1193107")).

Change your /etc/apt/sources.list to other site, eg: [http://mirrors.uwa.edu.au/ubuntu/](http://mirrors.uwa.edu.au/ubuntu/)

---

