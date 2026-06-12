---
title: "SMP on AMD 64 with Opteron 848"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by dhpeterson on 2005-10-26
Hi All,

I've just installed breezy on a SunFire v40z with dual opteron 848 processors. The kernel package that I'm using currently is linux-image-amd64-generic. I noticed that there is no -smp version for this package!

Is it possible to run breezy amd64 under SMP on my box? Do I need to compile my own SMP kernel to support this, or is a package available somewhere?

Thanks in advance.

Dave

---

### Post by RAOF on 2005-10-26
You could just install the linux-amd64-k8-smp kernel.  The Opterons use k8 cores...

---

### Post by dhpeterson on 2005-10-26
[QUOTE=RAOF]You could just install the linux-amd64-k8-smp kernel.  The Opterons use k8 cores...[/QUOTE]

Thanks fpr that! ... I didn't realise 'opteron == k8' .. . :)

---

