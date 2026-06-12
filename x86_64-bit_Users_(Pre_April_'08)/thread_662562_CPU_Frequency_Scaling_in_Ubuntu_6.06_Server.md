---
title: "CPU Frequency Scaling in Ubuntu 6.06 Server"
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by pongtawat on 2008-01-09
On my Ubuntu 6.06 Server (amd64) installation on a machine with Athlon X2 BE-2350, CPU frequency scaling doesn't work. The CPU keep running at its full speed. 

Checking dmesg, I found the following message:

powernow-k8: Processor cpuid 60fb1 not supported

I try to compile new powernow-k8 driver from AMD without success. It seems that the new driver requires mutex support which is not in Dapper's kernel.

Is there any way to enable CPU frequency scaling without replacing the kernel with newer version?

Thank you.

---

### Post by 6568912 on 2008-01-09
upgrade to 7.10 gutsy gibon?:-k

---

### Post by kuja on 2008-01-09
Hmm, it's also possible that your CPU could be newer than your BIOS, in which case you might need to update your BIOS to get scaling support for your CPU ('tis what I had to do for mine). If that's the case then proceed with caution.

---

