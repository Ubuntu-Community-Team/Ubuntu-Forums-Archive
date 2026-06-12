---
title: "kernel BUG"
date: 2005-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by wateenellende on 2005-12-30
On my amd64 machine I get a kernel BUG in mm/page_alloc.

Kernel is the stock ubuntu 2.6.12-10 amd64-k8. The bug can be reproduced very easily (*sigh*) by copying some GB of data over the network (NFS, kernel server) whilst running dvdrip.

It looks like:
[http://lists.debian.org/debian-kernel/2005/11/msg01028.html](http://lists.debian.org/debian-kernel/2005/11/msg01028.html)
except this is on an AMD64. This would imply the problem is fixed in 2.6.14 series kernel.

Should I report this, and if so, where ?

How do I get rid of this problem ? Is there a newer (2.6.14) kernel available somewhere ?

Thanks in advance!

---

### Post by ytene on 2006-01-06
Looks to me like you've done some good background analysis of this problem and have a repeatable issue. I'd suggest that you post this in Ubuntu's bugzilla bug tracking system. Check out

[http://bugzilla.ubuntulinux.org/](http://bugzilla.ubuntulinux.org/)

I'm very much a Newbie when it comes to Linux admin and problem diagnosis, though I've been using Linux as a casual user for a couple of years now. I'm tracking 2 issues on bugzilla that impact my AMD64 SMP machines and have found the experts and ubuntu testers to be ready, willing and able to help.

Before you put a new post on, however, do please do some basic searches of the database, just to see if anyone else has listed a similar issue. Adding your data to an existing entry is much more effective than creating a new one...

I hope you find the fix you're looking for. 

Best Regards,

Clive

---

### Post by wateenellende on 2006-01-14
Compiling a new kernel (2.6.14.5) solves the problem.

---

