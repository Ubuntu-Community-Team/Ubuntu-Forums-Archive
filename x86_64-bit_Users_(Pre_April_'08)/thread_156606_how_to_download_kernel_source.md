---
title: "how to download kernel source"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by eleach on 2006-04-07
I'm trying to install the nvidia driver:

   NFORCE-Linux-x86_64-1.0-8178-pkg2.run.

It is giving me the error:

   Unable to find kernel source tree

My kernel is:

   2.6.12-9-amd64-generic

How do I download this kernel source?

Thanks,

Ed

---

### Post by lnxpwr on 2006-04-07
try this, maybe it helps:

sudo apt-cache search linux-source

..this should print out the possible versions, and than install your choose:

sudo apt-get install linux-source-<your version>

---

