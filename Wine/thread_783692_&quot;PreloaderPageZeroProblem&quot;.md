---
title: "&quot;PreloaderPageZeroProblem&quot;"
date: 2008-05-05
forum: Wine
---

### Post by VMC on 2008-05-05
I searched and couldn't find anything on this, so I thought I would report it as F.Y.I.

When I start Wine under Harty Heron, I get the following error:
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space,
please report

Bug #114025 in wine (Ubuntu)

It appears to be kernel related per this comment:
"It seems to be caused by kernel 2.6.24-16, if you boot into 2.6.24-15 you don't get the errors but you do with the newer kernel so my guess is the problem lies with the kernel rather than wine. In this case wine is just showing a problem."

It has been reported as a bug in Wine HQ and in case you run across it here is the workaround:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

