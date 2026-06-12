---
title: "dpkg error in Kubuntu 5.10..."
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by twokatmew on 2006-03-04
I've been running Ubuntu 5.10 on my 32-bit AMD system for several weeks now, and I even managed to get Dapper running on it.  I also have a 64-bit system and thought I'd like to try Kubuntu.  I gave up on Dapper, as the install CD hangs on the xserver-xorg config, and the live CD won't work either.

Anyway, I now have a running Kubuntu 5.1 64-bit system.  But .... when I try to update (apt-get), it updates quite a few packages and then bombs telling me:

Manually run "dpkg --configure -a"  so I do this (using sudo, of course), but then I get the following error:

dpkg: ../../src/packages.c..191: process_queue:Assertion dependtry <= 4' failed
.
Aborted

Any idea how to fix this?  I've been playing with multiple distros on different machines, and I've seen the first error before, but running the specified command has always fixed it.

TIA,

---

