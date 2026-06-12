---
title: "Xen 4gb ram issue"
date: 2007-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ejohney on 2007-11-03
I'm having issues with the xen kernel in gutsy not being able to see all of my 4gb of ram when running in amd64.

I can boot the 2.6.22-14-server kernel and the ram available is 4054300kb

However, when i boot into the xen kernel i only have 3457024kb.

Everything else is working fine with the xen kernel, i'm able to start up several domUs and everything.

What could the problem be, am i missing something?

---

### Post by burke3gd on 2008-03-12
I had the same problem with Debian etch, turns out it was a problem with grub:

[http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub](http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub)

---

