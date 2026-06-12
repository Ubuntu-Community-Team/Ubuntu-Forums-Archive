---
title: "Dell Laptop Dual boot question"
date: 2006-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dambrosio on 2006-07-21
I just bought a laptop for college and it has a 100 gig hard drive. I want to dual boot windows and linux, should i do 20 gigs linux 20 gigs windows, and the rest fat32 for a shared music library? How do i install ubuntu over the pre installed linux? Do i just pop the disk in or what? And how do i get a os chooser when im booting up the computer?
Thanks a bunch,
Dan Ambrosio

---

### Post by Jagot on 2006-07-22
It's up to you how you partition your disk.  It depends on how many programs you install in Uindows and Ubuntu.  You may want to read this:

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

If you have a preinstalled Linux partition on there then you should just be able to overwrite that with Ubuntu's partitioner.

GRUB, the boot loader (or indeed OS chooser) will be installed by default - you don't need to worry about that.

You may want to have a read through these guides:

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Dambrosio on 2006-07-24
OK so I looked into the dual boot partitions and I came up with this idea. Windows 25 gigs (NTFS), Linux 15 gigs(Ext3), Shared remaning gigs (Fat32). Does that look logical? Also for my swap partition if I have 2gigs of ram should I make 2 swaps that are 2 gigs or just make one swap with 2 gigs.

---

### Post by arkaos on 2006-07-26
> **Dambrosio said:**
> OK so I looked into the dual boot partitions and I came up with this idea. Windows 25 gigs (NTFS), Linux 15 gigs(Ext3), Shared remaning gigs (Fat32). Does that look logical? Also for my swap partition if I have 2gigs of ram should I make 2 swaps that are 2 gigs or just make one swap with 2 gigs.

The swap doesn't need to be that large and it doesn't depend on how much ram you have. I use only 1 gig for my swap partition and that is probably overkill, anyway. My system runs great with 1 gig swap. (I got 1 gig ram, but that really shouldn't matter). The only time you really need a large swap space is if your machine doesn't have enough ram to run memory-hog programs, but most linux programs (stable ones) are designed very well and aren't memory-hogs, anyway.

---

