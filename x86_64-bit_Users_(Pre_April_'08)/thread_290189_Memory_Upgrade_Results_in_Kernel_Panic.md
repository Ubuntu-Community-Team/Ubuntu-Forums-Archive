---
title: "Memory Upgrade Results in Kernel Panic"
date: 2006-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-10-31
Hi,

Interesting thing, I had Dapper Running with 2GB memory. My board supports a max of 4GB. I added 2GB more and I got a kernel panic. If I remove 1 1GB stick, the system boots, but the system monitor reports that I have 2.7GB total memory.

What could be the problem?

---

### Post by John.Michael.Kane on 2006-10-31
Have you ran memtest? 

Is the machine Overclocked?

Is the machine fully stable with out that one stick?

If the machine is stable without that one particular stick then you may have a bad ram module.

---

### Post by kuja on 2006-10-31
Boot into memtest. If you start seeing more error messages then get ready to RMA your new sticks of RAM. Also, if Linux is not seeing all of your memory, then it's probably a motherboard/bios thing, try playing around with your memory related settings, if applicable. If none of the above are the problem, check your motherboard manufacturers website and see if there is a firmware upgrade for your motherboard that resolves the problem.

---

### Post by bper on 2006-11-01
No, haven't run memtest but will and will reply with results.

No, not overclocking.

Yes, it seems stable with the 3 sticks other than that the system monitor reports 2.7GB rather than 3.

My motherboard manual states that the system may report less than 4 GB if I use 4 sticks due to chipset resource allocation. But since I'm using 3 sticks, I didn't expect to see that.

Now, I can look this up, but if you know this off the top of your head, how do I boot up into memtest?

---

### Post by uniko on 2006-11-01
When grub loads hit DEL or whatever it tells you to show the full menu. There should be a memtest86+ option. Select that and let it run a few times over. Even a single error means you've got defective RAM.

---

### Post by bper on 2006-11-01
OK thanks. I'll give it a try. I should also probably mention that the first two modules are from a different manufacturer than the second two. The have the same CAS Latency, though.

---

### Post by bper on 2006-11-03
OK,

Memtest runs and memory seems fine. When I run the two new sticks by themselves they run fine. The issue comes when I run the three or more sticks.

With only two sticks, I run at ddr400 CAS Latency 3.
3 or more sticks, I run at ddr333 CAS Latency 2.5.
With 3 sticks, I lose 256 MB RAM.
With all 4 sticks, I get kernel panic.

I have s/w & h/w dram over 4G remapping enabled in my bios. That is correct, isn't it? Any ideas as to what may be happening?

---

### Post by bper on 2006-11-06
OK,

Kernel Panic resolved. I removed the H/W & S/W DRAM remapping and the OS boots fine with 4GB RAM. The only thing is the speed and the timings are different. Is this to be expected? Is it because of the mixing of the RAM or because of 4GB?

The total memory is 4GB. 1 GB sticks X 4. 2 Kingston & 2 PNY.

The other thing is that the BIOS reports that I have 4GB installed and usable. The system monitor in Ubuntu says that I'm running 2.7 GB. I can't possibly be losing all of that memory, can I? If that's true, I might as well remove the extra 2 GB. 3 sticks give me 2.7 GB in the OS too. Where's the rest of the memory?
When I was running at 2GB, the OS saw all of the memory. Once I stepped up to 3GB, I saw a drop in speed and memory listed in the OS. The funny thing is that at 3GB (3 sticks) the bios doesn't see all 3 GB. It sees 3GB less 256 MB and the OS sees 2.7 GB. When I bump up to 4GB, assuming that somehow I'm going to lose 256MB when I go over 2GB ram, the BIOS sees all 4GB of RAM but the OS is still stuck at 2.7GB. I don't get it.

If I'm really stuck at 2.7GB, It doesn't pay to upgrade the RAM over 2GB. Even with 64bit Ubuntu. I'll just pull out the 2 extra sticks. Are there know issues with 64bit Ubuntu with over 4GB RAM?

I'll try and post this question as a new thread.

Thanks.

---

