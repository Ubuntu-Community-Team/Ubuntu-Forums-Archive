---
title: "how to get Synaptic to show me 386 repositories"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by gmoore777 on 2009-11-05
I just installed 64 bit Ubuntu Linux (HardyHeron).

What is the trick to edit /etc/apt/sources.list such
that SynapticPackageManager (or apt) will load up 
lists from i386 repositories?

No matter how I edit sources.list, Synaptic will always construct
its path by slapping on "binary-amd64/Packages.gz"
and then understandably erroring out with: "Failed to fetch..."

---

### Post by wkulecz on 2009-11-05
I don't know the answer, but it would be nice to have Synaptic show 32-bit versions at least of stuff that is not yet available in 64-bit packages that is known to work.

--wally.

---

### Post by dcstar on 2009-11-06
> **gmoore777 said:**
> I just installed 64 bit Ubuntu Linux (HardyHeron).

What is the trick to edit /etc/apt/sources.list such
that SynapticPackageManager (or apt) will load up 
lists from i386 repositories?

No matter how I edit sources.list, Synaptic will always construct
its path by slapping on "binary-amd64/Packages.gz"
and then understandably erroring out with: "Failed to fetch..."

You cannot, the whole structure of the APT repository system is designed only to offer packages in the correct architecture folders.

---

