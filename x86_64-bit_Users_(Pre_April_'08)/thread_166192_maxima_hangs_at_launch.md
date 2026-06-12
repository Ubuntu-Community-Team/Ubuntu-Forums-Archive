---
title: "maxima hangs at launch"
date: 2006-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Seth Quarrier on 2006-04-25
I have installed Maxima on my mini (running Drake) and when I launch Maxima it just hangs totally unresponsive eating as much CPU as it can get until I kill it. If I try to launch it from a graphical program eg. wxmaxima I see the maxima process spawn and run once again eating full CPU in top and wxmaxima gives the message maxima started, waiting for connection indefinitely. Has anyone had any luck with the Ubuntu maxima packages on PPC?

Seth

---

### Post by rquint on 2006-05-25
There is something wrong with the Ubuntu ppc binaries for maxima. On a i386 box maxima runs fine.

Under Breezy I had to install libgmp3 from Debian to get maxima 5,9,1-7 to run.  I've just recently let my ppc iMac upgrade to the Dapper beta and that automatically upgraded maxima to 5.9.2, after which I had the same problem you had.  I'll try downgrading to 5,9,1  tomorrow and see what happens (assuming I can find libgmp3, and downgrading libgmp3c2 back to libgmp3 doesn't break something else.  I'll also experiment with using the Debian packages.  Wish me luck.

---

### Post by ssam on 2006-05-25
[https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169](https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169)

---

### Post by rquint on 2006-05-27
As reported by others

[https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169](https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169)

there is a bug, but maxima 5.9.3 compiled from source on a G3 iMac without any problems.

---

### Post by kellogs on 2006-06-01
I tried  to compile maxima again but cmucl lisp is not available in latest dapper repositories (ppc). Clisp package (from universe repos) causes a Segfault and does not install on dapper... and I couldnt find any lisp compiler that compiles maxima, ppc here. 

the bug [https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169](https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169) says it is fixed compiling with clisp, but i couldnt.

So by now lets wait maxima people can create a working version of maxima for ppc linux.

edit: it seems this problems is unique to ppc platform, on x86 it works well. If  anyone could compile maxima with a version of lisp that is available on dapper repos, please post it here if you can, thanks.

---

