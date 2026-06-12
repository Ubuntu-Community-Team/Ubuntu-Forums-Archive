---
title: "swapon help"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by mcough2 on 2008-05-14
I am running ubuntu 8.04, and added 0.5 GB of ramm to my machine. Which gives it a total of 1.5 GB of ram.
I seem to be have some performance issues, and I was told that I need to change the size of my /dev/shm partition. right now it is 750MB. I was also told that I should find a how to post about swapon. i can not seem to find one, so I was wondering if someone could tell me how to change the size of my virtual memory to 1.5Gb to match my ram.

---

### Post by az on 2008-05-14
> **mcough2 said:**
> I am running ubuntu 8.04, and added 0.5 GB of ramm to my machine. Which gives it a total of 1.5 GB of ram.
I seem to be have some performance issues, and I was told that I need to change the size of my /dev/shm partition. right now it is 750MB. I was also told that I should find a how to post about swapon. i can not seem to find one, so I was wondering if someone could tell me how to change the size of my virtual memory to 1.5Gb to match my ram.

How much swap do you currently have?

What performance issues are you having that you think you can solve by adding more swap or tmpfs?

---

### Post by mcough2 on 2008-05-14
I have 2GB of swap. Because I originally have 1GB of ram. The performance problem I am having is my computer is running slower then before I added the ram. 
I believe setting my swap to the correct size with solve this issue

---

### Post by az on 2008-05-14
> **mcough2 said:**
> I have 2GB of swap. Because I originally have 1GB of ram. The performance problem I am having is my computer is running slower then before I added the ram. 
I believe setting my swap to the correct size with solve this issue
How much ram is free when you find the computer running slow?  What are you running?

Swap is needed for stability, but more is not better.  You probably would be fine with a much smaller swap.  

I doubt adding more swap will improve your performance.

Is the ram you added the same density and timing as the ram you originally had?  Is your disk full?  Those two things can slow down your system.

---

### Post by mcough2 on 2008-05-14
About 75 percent is free when nothing is running. Usually just firefox, emacs, and/or rhythmbox. In the system monitor it says I only have 1GB of swap, but I was pretty sure I partitioned swap as 2GB.

The ram is the same as the ram I already had, and the disk is only about 65% full.

---

### Post by utUtu on 2008-05-14
> **mcough2 said:**
> About 75 percent is free when nothing is running. Usually just firefox, emacs, and/or rhythmbox. In the system monitor it says I only have 1GB of swap, but I was pretty sure I partitioned swap as 2GB.

The ram is the same as the ram I already had, and the disk is only about 65% full.

Can you post the results of these commands?

[I]sudo blkid
sudo df -h
sudo free -m[/I]

---

