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

### Post by sayantan on 2006-04-07
Hi 

Assuming you want to download the whole kernel souce, you need to go [here]("http://www.kernel.org") and download the kernel source tree.

---

### Post by ShakingSpirit on 2006-04-08
No, he wants the ubuntu kernel sources.
Run:
```
# sudo apt-get install linux-headers-`uname -r` build-essential gcc
```

Then try installing the drivers again :)

---

