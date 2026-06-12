---
title: "Not detecting all my memory"
date: 2008-09-19
forum: x86 64-bit Users
---

### Post by darkproteus66 on 2008-09-19
I just upgraded my system to 6GB of ram and installed Ubuntu 8.04 64-bit. I boot in and the system is only detecting 3.2 gb of ram. My system is an HP a1606n with an Intel Pentium D 805, an nvidia  8600gt w/ 256 ram, an Asus P5LP-LE.

---

### Post by kjohansen on 2008-09-19
It could be that your motherboard can not handle that much memory despite having a 64 bit OS.

---

### Post by phenest on 2008-09-19
That's the same with my laptop. I have 4GB of RAM, but the 512MB video card takes its share and some for the system, leaving about 3.2GB. That's quite normal. Nothing to do with the OS.

---

### Post by Kilz on 2008-09-19
The 8600gt has 

NVIDIA® TurboCache™ Technology

    * Combines the capacity and bandwidth of dedicated video memory with dynamically allocated system memory to dramatically turbocharge performance.

That says it takes and uses system memory.


Second the [Spec's of your computer]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00797512&lc=en&dlc=en&cc=us&lang=en&product=3321063").

Memory
Component 	Attributes
Memory Installed 	1 GB
Maximum allowed 	4 GB* (4 x 1 GB)

*Actual available memory may be less


So It only can handle 4gb, and the video card is using some.

---

### Post by jhenager on 2008-09-19
> **darkproteus66 said:**
> I just upgraded my system to 6GB of ram and installed Ubuntu 8.04 64-bit. I boot in and the system is only detecting 3.2 gb of ram. My system is an HP a1606n with an Intel Pentium D 805, an nvidia  8600gt w/ 256 ram, an Asus P5LP-LE.

All three replies are correct.
Hardware issue.
[http://www.nvnews.net/vbulletin/showpost.php?p=792041&postcount=2](http://www.nvnews.net/vbulletin/showpost.php?p=792041&postcount=2)

---

### Post by darkproteus66 on 2008-09-20
Okay thanks for the help people.

---

