---
title: "Memory usage over 2100 MB"
date: 2009-05-20
forum: x86 64-bit Users
---

### Post by helliewm on 2009-05-20
Anyone any ideas as to how I can reduce my memory usage? I am using over 2 gigs! I am using 64 bit Jaunty.

I have Firefox, Evolution, Banshee, Gwibber, Gnome Do and Open Office running.

Attached is a screenshot of HTOP.

Helen

---

### Post by Yellow Pasque on 2009-05-20
What is the output of: free -m ?

---

### Post by helliewm on 2009-05-20
free - m is attached.

Helen

Edit: Reattached it!

Its here I have cut and paste it vanishes in the screenshot, odd.

helen@helen-barnaby:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3898       3848         50          0        151       1436
-/+ buffers/cache:       2260       1638
Swap:        11421          0      11420
helen@helen-barnaby:~$

---

### Post by Yellow Pasque on 2009-05-20
Wow, your Xserver is consuming almost a GB by itself. Memory leak?

---

### Post by helliewm on 2009-05-20
Anything I can do about this? Is it a bug?

Helen

---

### Post by Yellow Pasque on 2009-05-20
Do you have intel graphics?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319)

---

### Post by markoschlegel on 2009-05-21
Any Linux system (or any well designed unix) that runs long enough will use almost all the RAM.  This is normal.  Notice you're not using any swap and if you look at the second line in your free output you have 1638MB of free memory if you account for the buffer and caching.

The kernel will release buffer or cache as needed for use by applications and it does that fast enough that there's no point in leaving a bunch of RAM unused but rather it's used for buffering/caching.

---

### Post by Gen2ly on 2009-05-21
well put marko.  yeah, if you got the ram for it the kernel isn't going to throw it out.  This makes for quicker load times, blah, blah, blah...  If you had the machine up for a long time this isn't a problem.

---

### Post by QIII on 2009-05-21
There is a regression in Xorg.  The bug was recently reopened.

It appears that when certain graphical objects are opened and then closed, Xorg does not release the memory.

They have the fix as 

Priority: High
Severity: Major

I don't remember the url at the moment, but if you go to [www.x.org](www.x.org) and look for their buglist, you'll be directed to bugzilla.

You can search for "memory leak Xorg" (I think).

I hope this gets fixed before the Redmond Fanboyz find out, or our community will take quite a beating.

---

