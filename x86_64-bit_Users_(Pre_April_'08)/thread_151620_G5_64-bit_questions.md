---
title: "G5 64-bit questions"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by jakemikey on 2006-03-28
Hi all,

In the lab where I work we've got an Xserve (G5) cluster that runs Panther (32-bit).  In the process of working with some very large sets of data we've run into the wall of 32-bit addressing capabilities.  I'd like to install a PPC 64-bit distro of Linux on one of the other hard drives of the head node so that we can get around the memory problems for this project, but still be able to go back to Panther to run the cluster as usual.

So my question is: is the PPC distribution of Ubuntu able to run 64-bit apps?  I know the kernel can be 64-bit enabled, but are there at least 64-bit libs, etc in the PPC distro?  I'm confused because there's just one PPC install CD whereas for x86 there are specific 32 and 64 bit versions.

Basically the only app this will need to run is R, which I will compile from source to enable its 64-bitness.

---

### Post by ssam on 2006-03-28
there is a 64bit kernel, but i think that everything else in 32bit.

yellowdog linux is focusing on high performance computing these days, that might be worth researching.

---

