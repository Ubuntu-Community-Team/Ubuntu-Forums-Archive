---
title: "Raid 10 installation"
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by pnotequalsnp on 2007-09-06
Thanks for taking time to help me with my question.

I have 5 HD's, an IDE for the OS, and four SATA's for storage.  I want to configure the four SATA's in a raid 10 configuration (mirrored with striping on top if I am getting it right).  I have the 64 bit version of Ubuntu installed and I was wondering if anyone had tips for getting Raid 10 (not Raid 1, 5 etc) working (tutorials would be invaluable).

---

### Post by NiN on 2007-09-06
You could use a softraid mirror for the sata drive pairs and build an LVM on top of it.

Raid: apt-get install mdadm (no link ready, sorry, but web is full of howtos)
LVM: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

Maybe you should also consider using raid6 when raid5 is not enough? Or is there a special reason for this kind of setup?

[edit]
Just read the man page of mdadm: Looks like there are 2 possibilities:

  - Stack 2 software raids on top of each other ( a raid 0 on top of 2 raid 1 arrays)
  - Just create a raid10 directly ;)

A Guide to linux sw raid: [http://www.howtoforge.com/linux_lvm_p9?](http://www.howtoforge.com/linux_lvm_p9?)
[\edit]

---

### Post by glee on 2007-09-12
Hi pnotequalsnp, 

I too am interested in setting up raid 10, and am happy to exchange ideas, if that helps.  I have experience setting up and managing software raid level 1 under linux using mdadm, but not raid 10. At present I am trying to decide whether to implement raid 10 using mdadm or fork out for a hardware controller. I intend to build the array this coming weekend. 

This link may be helpful: [http://www.sanitarium.net/golug/Linux_Software_RAID.html]("http://www.sanitarium.net/golug/Linux_Software_RAID.html")

There is a description about half way down the page of how to initialise a raid 10 array with mdadm. How well these instructions map to other scenarios remains to be seen. 

I'll report back any successes.

---

