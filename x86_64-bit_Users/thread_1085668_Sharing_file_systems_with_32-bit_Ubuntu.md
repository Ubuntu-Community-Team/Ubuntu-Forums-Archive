---
title: "Sharing file systems with 32-bit Ubuntu?"
date: 2009-03-03
forum: x86 64-bit Users
---

### Post by darlinsk on 2009-03-03
Hello,

I am currently running 32-bit Ubuntu 8.04 and am about to install the 64-bit version along side of my current instance in a multiple-boot environment.  Below is a list of my 32-bit file system setup. 

linux-swap - 1.46 GB (Drive 0)
linux-swap - 1.46 GB (Drive 1)
/ - 14.65 GB (Drive 1)
/usr - 14.65 GB (Drive 1)
/home - 267.33 GB (Drive 1)

My question is, can I share the linux-swap files and/or the /home file system with my new 64-bit version?  I'm less concerned about the swap files, as they are relatively small.  But I would really like to share the /home file system -- although I suspect that will be the more problematic one.  Any advice greatly appreciated.

---

### Post by philinux on 2009-03-03
The files in home are mainly text config files, pics and videos etc that dont care about 32 or 64 bit.

---

### Post by darlinsk on 2009-03-04
Thanks for the reply.  Does anyone have any thoughts about whether I can use the same swap partitions for both systems?

---

### Post by int on 2009-03-04
> **darlinsk said:**
> Thanks for the reply.  Does anyone have any thoughts about whether I can use the same swap partitions for both systems?

You can use the same swap partition with all *nix/BSD/.. systems. One at once..

/home/ have lots of config files, and extensions... I don't know if none of them have ref. to 64bits (lib,...)

---

### Post by 3Miro on 2009-03-04
I have shared 32 - 64 bit Linux systems for years. Now I moved to 64 only, but in either case, sharing the swap is not a problem at all. Swap clears on reboot anyway, so just share it.

Sharing /home, however, is tricky. For example, 32 bit Linux has a lib folder, while 64 bit ones have lib64 and lib32. Most of the content of /home is indeed text files that would not care (actually I was moving xorg.conf files between the 32 and 64 bit with no problem at all), however, all you need is one config file referencing something in lib vs lib64 to break the entire system. I would not share /home.

If you wish, you can create one swap partition, two small /home partitions for the 32 and 64 and one large partition (call it Data) for media (movies, picks, music), installations for wine games and other such "neutral" data which would be shared between the 32 and 64 bit boots.

This was more or less what I had done.

---

### Post by darlinsk on 2009-03-04
Thank you, 3Miro.  I had been concerned with instance specific files in the  /home directory.  That seems like a very reasonable approach.  I'll move things around, then do the 64 bit install.

---

### Post by marcelkoopman on 2009-03-04
On thing I noticed, you have two swap partitions, you only need one. Both ubuntu installations will automatically use it.

---

### Post by darlinsk on 2009-03-04
Actually, I use both swap partitions for my 32-bit instance, and was planning on using both of them for the 64-bit, as well. Back when I was setting up my 32-bit system, I read somewhere that splitting the swap between two physical disks improved performance.  The reality is that I have plenty of memory, and probably only use the swap files when running virtual machines in VMware.

I've been wondering how large the swap should be for the 64-bit installation.  Given that I've maxed my machine out with 8 GB of ram, I figured I would be fine with the two swap partitions already allocated.  Please let me know if I'm missing anything.

---

### Post by marcelkoopman on 2009-03-04
> **darlinsk said:**
> Actually, I use both swap partitions for my 32-bit instance, and was planning on using both of them for the 64-bit, as well. Back when I was setting up my 32-bit system, I read somewhere that splitting the swap between two physical disks improved performance.  The reality is that I have plenty of memory, and probably only use the swap files when running virtual machines in VMware.

I've been wondering how large the swap should be for the 64-bit installation.  Given that I've maxed my machine out with 8 GB of ram, I figured I would be fine with the two swap partitions already allocated.  Please let me know if I'm missing anything.
Please let go of the swap file paranoia. You cannot gain any significant performance with that. And i wonder if anything is swapped with that much ram.

---

### Post by Yellow Pasque on 2009-03-04
The only reason you would need more swap than what you already have is if you somehow need more than 11GB of virtual memory, or if you want to hibernate. Either way, you could use a swapfile instead of the swap partitions.

---

