---
title: "Best strategy for 32-&gt;64 high memory"
date: 2008-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by pearlbear on 2008-02-09
I have a machine with an AMD Athlon 64, with 8G of RAM. For reasons I won't go into now, I ended up installing a standard 32 bit version of Ubuntu Gutsy (imagine fighting with a futsy CD drive in a Mobo w/o bootable USB, etc.)

So not only can't it see the 8G, but it's not using 64 bit.

So I could re-install with the 64 bit iso. I'd rather not do that, for obvious reasons. What are my options?

I don't see a specific kernel image for 64 bit. Or one for big memory. 

Suggestions?

---

### Post by Kilz on 2008-02-09
> **pearlbear said:**
> I have a machine with an AMD Athlon 64, with 8G of RAM. For reasons I won't go into now, I ended up installing a standard 32 bit version of Ubuntu Gutsy (imagine fighting with a futsy CD drive in a Mobo w/o bootable USB, etc.)

So not only can't it see the 8G, but it's not using 64 bit.

So I could re-install with the 64 bit iso. I'd rather not do that, for obvious reasons. What are my options?

I don't see a specific kernel image for 64 bit. Or one for big memory. 

Suggestions?

Did you try and install from the 64bit live Desktop cd or the Alternate cd? My advice is to try and install the 64bit version from the alternate cd to a separate partition if you have room. That way you could work out any issues and still have a working 32bit install to boot into while working out those issues. Then when the 64bit version is running, remove the 32bit to reclaim hard drive space.
[Go here to get the alternate cd.]("http://mirrors.gigenet.com/ubuntu/gutsy/")

---

### Post by DDuong on 2008-02-09
Hi Kilz,

When I installed 4gb into my laptop with 32bit gutsy, I had the same question as you.  So what I did before was that I recompiled the kernel and selected Big Memory (or somewhere along the lines of that).  I rebooted and voila!  The laptop saw 4gb of ram.

However, I've always wanted to try out 64bit so I installed that instead and never regretted and never going back to 32 bit :P

EDIT:
Oh and also, I used the latest kernel that was available on kernel.org and used that.

---

