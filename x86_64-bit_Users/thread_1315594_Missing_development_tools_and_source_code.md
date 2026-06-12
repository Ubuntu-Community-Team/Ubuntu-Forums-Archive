---
title: "Missing development tools and source code?"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by wkulecz on 2009-11-05
Just installed 9.10 64-bit and after working around a grub2 issue (it ignored my BIOS selection as to if IDE or SATA was the "first" drive) things seem to be working OK.

But it seems some of the development tools I use are missing, particularly Glade3 and the Eclipse C tools.

Is this the case for 32-bit as well or is 64-bit still not really "there" yet.

Also can't seem to find the gstreamer sources in synaptic, i've added the source repros.  I can get them from freedesktop.org, but I was thinking the source actually used on my system would be a better starting point.

Ubuntu 9.10 has a new enough gstreamer that appsrc and appsink should be there, these are missing in the version used for 8.04.  I'm planning a project expecting to target 10.4LTS and need to evaluate using appsrc & appsink vs. writing a gstreamer plugin (which I've already done a toy version of on 8.04).  This is my main motivation for trying 9.10.

--wally.

---

### Post by timgood on 2009-11-05
Have you tried installing the Jaunty .debs?

---

### Post by wkulecz on 2009-11-05
> **timgood said:**
> Have you tried installing the Jaunty .debs?

No, but why would I want to do that?

I want to see if the state of 64-bit development is something I can make a commitment to now, not play around with "it might work" stuff.  

I did notice when I clicked the source repository it's box changed color but didn't checkmark, perhaps the source repos aren't up yet.

--wally.

---

