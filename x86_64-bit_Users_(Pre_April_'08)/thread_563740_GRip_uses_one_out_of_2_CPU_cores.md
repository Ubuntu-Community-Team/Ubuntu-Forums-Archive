---
title: "GRip uses one out of 2 CPU cores"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by crashtestyyz on 2007-09-30
Okay, so I have both cores recognised, and when running GRip, I can see it pinning one core to 100% while the other one sits idle and/or takes care of other system processes.
I've checked off "use 2 cpus" but still nada.
I get the following complaints from GRip:

Couldn't disable kernel command translation layer

So is the kernel stopping grip from using the 2nd cpu?  anybody else come across this with grip or other programs?

 2.6.15-29-amd64-generic #1 SMP PREEMPT Wed Aug 29 13:24:06 UTC 2007 x86_64 GNU/Linux

any insight is appreciated!
--C

---

### Post by nss0000 on 2007-10-01
Yep. Write your own C-code without a fork();  one CPU gets frisky the other waits around for another task.

---

### Post by stmiller on 2007-10-01
Did you do this setting?

Config>Encode>Options> Specify 'Number of CPUs to use'-> 2

Encodes multiple threads for me okay with LAME here.

---

### Post by crashtestyyz on 2007-10-03
I'm not a C coder, so option 1 is out..

stmiller: I had that configured from the start.. no diff...
ah well.

---

