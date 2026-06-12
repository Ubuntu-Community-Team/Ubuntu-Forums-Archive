---
title: "move back to 32 bit"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by radi0j0hn on 2008-01-01
I need to know what I have gained (and lost) by moving to 64 bit. In other words, what daily , typical uses are improved.  Since there seems to be a number of apps that are not able to run under 64, and it is unclear to me how to "force" my AMD to run 32, I need to know how to put the 32 bit OS on my drive. Can I install over the 64 bit OS?  I am currently dual booting, and do not want to wreck my Windows partition.  TIA  John

---

### Post by ~LoKe on 2008-01-01
There isn't really anything that doesn't work under 64bit.  There are guides to installing any troublesome app.  Is there any specific reason you want 32bit back?  In any case...you could format the / partition and install 32bit over it instead.

---

### Post by ZootNerper on 2008-01-01
Hi,

You should read this post:

[http://ubuntuforums.org/showthread.php?t=655385](http://ubuntuforums.org/showthread.php?t=655385)

-- Zoot

---

### Post by radi0j0hn on 2008-01-01
Thanks for the replies.  I still am not finding really clear (to me) step by step how-to to force a 32 bit app to run on 64.  I need to use Kompozer (Nvu).  I'd like to try CNR.

Thanks!

John

---

### Post by rsambuca on 2008-01-01
> **radi0j0hn said:**
> Thanks for the replies.  I still am not finding really clear (to me) step by step how-to to force a 32 bit app to run on 64.  I need to use Kompozer (Nvu).  I'd like to try CNR.

Thanks!

John

It is in the standard repos.  

```
sudo apt-get install kompozer
```

---

### Post by S3Indiana on 2008-01-02
> **radi0j0hn said:**
> I still am not finding really clear (to me) step by step how-to to force a 32 bit app to run on 64.  I need to use Kompozer (Nvu).  I'd like to try CNR.The CNR Client has not yet been built against the 64-bit repository, so using the CNR Client will not function on a 64-bit system (without being recompiled)...

---

### Post by chewearn on 2008-01-02
Does this work:
```
sudo dpkg -i --force-architecture *packagename_i386.deb*
``` Ref:
[http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)

---

### Post by dcstar on 2008-01-02
> **radi0j0hn said:**
> I need to know what I have gained (and lost) by moving to 64 bit. In other words, what daily , typical uses are improved.  Since there seems to be a number of apps that are not able to run under 64, and it is unclear to me how to "force" my AMD to run 32, I need to know how to put the 32 bit OS on my drive. Can I install over the 64 bit OS?  I am currently dual booting, and do not want to wreck my Windows partition.  TIA  John

Either find 4GB of space in your hard drives and install the 32bit version there - you can select which to boot from (works well with a separate /home filesystem), or do what I have done and install **vmware server** and then install 32bit Ubuntu as a virtual machine.

Then you can run both (simultaneously), and the performance of the vm is quite good.

---

