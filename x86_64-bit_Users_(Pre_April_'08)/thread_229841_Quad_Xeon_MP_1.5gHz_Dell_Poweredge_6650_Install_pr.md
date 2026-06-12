---
title: "Quad Xeon MP 1.5gHz Dell Poweredge 6650 Install problem..."
date: 2006-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by nrinzema on 2006-08-05
Hello to this stunning community first off!  I feel bad that my first post is to ask/request your help,input and action.

I am trying to install the big U on my newly acquired Dell Poweredge 6650 (new used, lol).  It has quad Intel Xeon MP processors which to my knowledge are 64-bit CPUs via Intel's IA32 spec that emulates good ole AMD64... (as well as it can, lol)  If my brain and thoughts are inline, haha.

Anyways... I can boot to both the 64-bit install disk and the i386 disk.. Both of these disks present me with the pretty initial install screen.

My actual question begins here: When I use the 64-bit disk if I select any option from the menu a graphical progress bar appears, as it moves up from zero the screen gets these little short corruption lines that run horizontally in sync with the progress bar.. Then I am presented a screen that tells me that my machine is not AMD64 and to use the i386 disk.  So... what are the screen corruptions? and is a Intel Xeon MP 1.5gHz 512k cache processor 32-bit or 64-bit?

I am by the way able to use the 32-bit install disk and it is currently looking as if it will install.. I will have to get back to you on that one...

Show some newbie love and let me know what you think!  I am anxious to do as much as I can in this community

---

### Post by rverrips on 2006-11-26
Hey 
I just got my hands on an old one of these Dell 6650's today and was thinking of doing the same thing - Did you ever get it working?  i386 or 64?

---

### Post by rverrips on 2006-11-30
I installed the normal (i386) Ubuntu 6.10-Server CD on my Dell PowerEdge 6650 with External PowerVault S220 and the install went through perfectly - Found the 20-Span RAID volume, both Onboard Broadcom Gigabit NIC's, 

Now, howto ensure all 4GB ram, and all four 1.4Ghz Xeon Processors are being used optimally?

---

### Post by RAOF on 2006-12-01
I'm pretty sure that's a 32bit only chip.  Although it's actually impossible to tell from just the name "Xeon MP" - that actually covers **all** of Intel's top-end chips.

According to Wikipaedia, the first 64bit Xeon MP was shipped in April 2005.  If your system is older than that, it's **definitely** IA32 only :).

---

### Post by rverrips on 2006-12-01
> **RAOF said:**
> According to Wikipaedia, the first 64bit Xeon MP was shipped in April 2005.  If your system is older than that, it's **definitely** IA32 only :).

Thank Raof, it's a 2002 vintage so definetly pre 64-bit :-)

---

