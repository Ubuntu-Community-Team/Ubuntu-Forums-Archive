---
title: "Only 2.9 GB out of 4 GB of RAM available"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ioannis on 2006-02-06
I have a dual Opteron 280 with 4GB RAM installed (confirmed by the BIOS) and I am running 2.6.12-10-amd64-k8-smp, but when I run System Monitor, it reports that my User memory is 2.9 GiB. Is there something I have to adjust so that the full 4 GB is recognized and available?
I apologize if this is a basic question, but this is my third day in linux, and I looked around in many forums but haven't found an answer.

---

### Post by earobinson on 2006-02-06
I have heard some place that this is a bug that is going to be fixed.

I could be wrong confirm/deny anyone?

---

### Post by ioannis on 2006-02-14
For future reference: Thanks to Ben Collins who interpreted my dmesg for me and found that the problem was in the BIOS/hardware. After a LOT more searching around, I found that I had to tweak the BIOS settings to set:
MTRR mapping to "discreet",
Memory Hole Mapping to "software" and
IOMMU "enabled"

I have no idea what these all mean, but I found this on:

[http://lists.suse.com/archive/suse-amd64/2005-Jul/0120.html](http://lists.suse.com/archive/suse-amd64/2005-Jul/0120.html)

Now Ubuntu reports 3.8 GB \\:D/

---

### Post by earobinson on 2006-02-15
thanks for the update!

---

