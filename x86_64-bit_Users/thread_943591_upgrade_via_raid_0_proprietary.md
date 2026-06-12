---
title: "upgrade via raid 0 proprietary"
date: 2008-10-10
forum: x86 64-bit Users
---

### Post by giangiweb on 2008-10-10
In Ubuntu 7.10 I used proprietary drivers from Via to use a RAID 0 on chipset VT8251

Now that I have upgraded from 7.10 to 8.04 I can boot only old kernel 2.22 casue Via haven't released drivers for 8.04
Now that 8.10 is coming I think it will not boot on 2.22 kernel.

What can I do to let 2.24 and future kernels see my Raid zero?

Can I build, from 2.22 a software raid who work on 2.24 and see my via raid?
Is it a solution?

Ciao
Giangi

---

### Post by cariboo on 2008-10-10
Have a look at this howto:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I'm using it on my server, mind you I'm running raid1 as I don't really need the speed on a server. I started out with the last lts version 6.04 and up graded tp 8.04.1 with no problem at all. I'm using a 250Gb ide drive to boot and just use the raid array for storage.

Jim

---

### Post by giangiweb on 2008-10-11
yes, I know but this is a good howto for a new install...
I need something to see an existing via raid...

---

