---
title: "Kernel Panic on fresh install"
date: 2005-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by CzarAlex on 2005-12-26
I bought me a new computer a couple days ago and want to put Ubuntu on her. Ive used ubuntu for 6 months or so on a way older system without too much problem. That was i386 based...this new one is AMD 64 3000+

I aquired the "for your 64 bit" version of Breezy, threw the disc in and restarted. The initial ubuntu window shows up asking me to press enter or type `server`. I type enter..and about 20 seconds later I see a kernel panic. 

Is my disc from the shipit service busticated? Am I using the right version? ..Is it just me? (.....does it have anything to do with the fact that the 2nd hard drive i want to install ubuntu on shows up as a floppy drive in winblows?)

---

### Post by dna on 2005-12-27
The newest linux 64 kernel seem to have a serious problem with AMD machines. Had to build my own 2.6.14 kernel to fix my opteron box after upgrading to Breezy the other day. Doesn't really help your situation trying to do a fresh install but if your really determined:
1. install the last version of Ubuntu-> Hoary
2. change the /etc/apt/source.list to Breezy
3. apt-get dist-upgrade
4. reboot into old kernel
5. get kernel sources from dapper archives
6. read howto on building a new kernel
7. ???
8. Profit

---

### Post by CzarAlex on 2005-12-27
Is an 64 bit version of Hoary still available for download or is everything Breezy now?

---

### Post by mpk on 2005-12-29
Hoary 64-bit is available right here:
[http://releases.ubuntu.com/hoary/](http://releases.ubuntu.com/hoary/)

I'm going to give it a try since kernel panics are just one of the merry bunch of random weirdos hanging around my machine when ever I dare to attempt an installation. I've been at it for weeks now.

---

