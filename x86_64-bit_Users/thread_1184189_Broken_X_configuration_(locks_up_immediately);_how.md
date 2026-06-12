---
title: "Broken X configuration (locks up immediately); how to fix?"
date: 2009-06-10
forum: x86 64-bit Users
---

### Post by elmccarthy on 2009-06-10
Hi,

I just upgraded to 9.10 today and was trying to get my dual-head display setup working.  Something I've done is apparently terribly wrong, because now whenever X starts, the entire machine locks up (i.e.: I can no longer even SSH in to the box...)

I have an onboard ATI Radeon X1250 graphics card.  Due to the degree that the computer stops responding, it seems likely that my attempt to use the fglrx driver is the problem (this has got to be a kernel-level problem, no?)

My problem is that restoring a known-good xorg.conf doesn't seem to fix the problem.  I haven't used Ubuntu since 7.10 and apparently at some point since then there is a new mechanism for X configuration that I'm not aware of.

So, unless someone has a better idea, how can I stop X from trying to use the fglrx driver given that I have only the command line to work with (the gnome display preferences widget I used to cause the problem is obviously unavailable now) and xorg.conf seems to be ignored?

I should also mention that even trying to run xinit directly from the command line causes the lockup, so it's not specifically a gdm thing.

I should mention 

Cheers,

Luke

---

### Post by elmccarthy on 2009-06-10
...and never mind.  Uninstalling the fglrx driver from the command line was enough to be able to get back into the desktop and use all of the nice configuration tools therein to get the dual-head setup working.  Cheers,

Luke

---

