---
title: "swap not being used?"
date: 2007-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Goliath! on 2007-07-24
I have 7.04 running on a Dell 1501 with AMD64 2 GHz dual-core chip and 2G RAM.  I sometimes play Desktop Tower Defense, a flash game that is more addictive than crack.  Recently in the middle of play it sometimes comes to a virtual halt.  The laptop fan kicks in and game just sputters - it will move a character one pixel, pause for maybe half a second, then move another pixel.

I went to a terminal and ran top.  There are no zombies or run-away processes.  But it shows me that I am using 0 swap out of 4.8 G available.  How can that be right?  Why am I not using swap?  See attached screen shot.

---

### Post by jocko on 2007-07-24
You still have more than 400 Mb free ram, so there's no need to use swap.

---

### Post by dptxp on 2007-07-24
Swap sometimes gets used even if there is free RAM. But I think in low memory systems.

---

### Post by dabl on 2007-07-24
> **Goliath! said:**
> I am using 0 swap out of 4.8 G available

Yep, you followed the "2.5 x RAM" rule, approximately, didn't you?  Me too. I've been watching my setup for 6 months now, and I have yet to see 1 byte of swap used.  I have used Gnome Wave Cleaner on 2 different large audio files, simultaneously, and driven both my CPU cores to 100% for 5 minutes running, and still zero swap activity, mainly due to the fact that it was only using 500MB of my 4GB of RAM.  So, it appears we're still limited by the CPU throughput, not memory capacity, in these newer hardware setups.  Bottom line -- your swap space is about 4.3GB larger than you'll ever need, unless some _really_ memory-hungry app comes your way. :)

---

### Post by John.Michael.Kane on 2007-07-24
> **Goliath! said:**
>  I am using 0 swap out of 4.8 G available

I would try turning the swap file off, and running the machine on pure ram. This would allow you to gauge if you even need swap on your system.

---

### Post by Goliath! on 2007-07-24
Thanks for all the responses.

I have not changed my swap size - that 4.8G must be the installation default.  But anyway, it's not as if I'm short of disk space; there's no reason not to reserve that space.

---

