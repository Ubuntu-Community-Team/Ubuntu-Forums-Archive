---
title: "Any progress on the newer Prefetch?  How does it compare against Preload in testing?"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by DanglingPointer on 2009-06-04
Hi Masters of the Universe,

Has there been any progress on the newer Prefetch?  How does it compare against Preload in testing?  Is it finally compatible with ext4 file system

Will there be concurrent and parallel development for Preload (currently v 0.6.4)?  Will it ever reach version 1?

If both of the above develop in parallel, well, it would be great as competition creates better products! ;)

Prefetch: [https://wiki.ubuntu.com/DesktopTeam/Specs/Prefetch](https://wiki.ubuntu.com/DesktopTeam/Specs/Prefetch)

Preload: [http://sourceforge.net/projects/preload](http://sourceforge.net/projects/preload)

I have never run Prefetch but I am currently running Preload 0.6.4.

Also does anyone know if there is any project at the moment to come up with something like ReadyBoost cache for ubuntu for files smaller than 300KB?

---

### Post by DanglingPointer on 2009-06-07
Either now one knows or people are unsure, or perhaps, I have posted in the wrong forum.

Feedback anyone?  :confused:

---

### Post by Arup on 2009-06-07
The fact that preload is in the repos means it works with all the file formats available for Ubuntu. I have tested preload in past, the fact is that Jaunty with ext4 loads all programs quick by default and therefore I noticed no significant difference in speed of apps loading etc. after running for a month with preload. However having said that I am sure slower, older systems can benefit from preload being that their I/O may not be as fast as the current multi core PCs.

---

### Post by DanglingPointer on 2009-06-07
Thanks for the reply Arup, 

I've only had Preload 0.6.4 for a week.  To be honest I do not know if things are quicker than what they would be without Preload as I have only been using ubuntu for 3 weeks!  The first two of which was spent moslty configuring and tweaking it or working via Citrix XenApp to a M$ Server 2003.  

I'll tell you this though, ubuntu is fast and faster than the original Vista Ultimate that came with this notebook.

However, I did come across the Prefetch web page in my previous post, I also came across this presentation (see pdf in link):[http://prefetch.googlecode.com/files/gsoc-prefetching-presentation.pdf](http://prefetch.googlecode.com/files/gsoc-prefetching-presentation.pdf)

It describes deficiencies in Preload and other current software techniques and how they are addressed by Prefetch.  However I haven't been able to find any recent documentation (as in from this year to the nearest couple of months). Whether there has been any progress or whether it will be included in any future release of ubuntu.

I'm also wondering if anyone, group, or team is working on a flash cache technique for ubuntu for files smaller than ~300KB?  For M$ it is called ReadyBoost.
I believe there is an opportunity for ubuntu to come up with something similar.  Have a read of this idea: [http://en.wikipedia.org/wiki/ReadyBoost](http://en.wikipedia.org/wiki/ReadyBoost)
ubuntu is fast, yes, everyone agrees; but if there is opportunity to make it faster, why not?

---

