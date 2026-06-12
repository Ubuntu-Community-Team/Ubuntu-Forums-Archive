---
title: "Installing 4gigs of ram on laptop"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by Eezyville on 2008-10-16
I tried to install 4gigs of ram on my HP DV9000 laptop a little while ago and it kinda crashed my system. I don't understand what happened. I used two 2 gig sticks and replaced my 2 one gig sticks and ubuntu recognized it the first time i booted into it gut then after a restart things went wrong and I had no choice but to reinstall. Did I do something wrong? What was the proper way to upgrade my ram in ubuntu on a laptop?

Thanks for your help.

---

### Post by Amorget on 2008-10-16
From a quick search it seems that the HP DV9000 won't read 4 gigs of ram due to the Intel chipset that is used (945), which isn't a 64 bit chipset.  However, having 4 gigs installed shouldn't affect anything.

---

### Post by rbringh on 2008-10-16
I have a DV9000 and run 64Bit Ubuntu. It's not 4 gig though, only three. The processor is a AMD Turion64 x2.

---

### Post by jespdj on 2008-10-17
Are you sure the memory is OK? From the GRUB boot menu, choose the memtest86+ option to start the memory testing program. Let it run for a few hours to test if there are problems with the RAM.

If it finds errors, then you have broken memory chips.

---

### Post by Eezyville on 2008-10-17
I think I'll run the memtest when 8.10 releases because I will be doing a fresh install then. But I think the memory was good because I did recognize them when I first installed them.

---

### Post by Kevbert on 2008-10-17
It may recognize them via the bios and performs a rough test on switch on (POST - Power On Self Test), but it would still be worth running memtest (which is a good way of exercising the memory) as you may get random failures due to the seating of the memory sticks or just faulty memory.  It could cause an OS installation failure.

---

### Post by MikeDK on 2009-01-21
By default dv9000 series dosnt support 4gigs of ram, only 2gigs my laptop is an dv9232eu and max ram is 2gigs 

CPU TL-52 Turion amd64 Level2 cache 512KB Geforce 7600 GO 256MB 2 gigs of kingston 533Mhz ram,

Kind Regards MikeDK

---

### Post by stchman on 2009-01-21
> **Eezyville said:**
> I tried to install 4gigs of ram on my HP DV9000 laptop a little while ago and it kinda crashed my system. I don't understand what happened. I used two 2 gig sticks and replaced my 2 one gig sticks and ubuntu recognized it the first time i booted into it gut then after a restart things went wrong and I had no choice but to reinstall. Did I do something wrong? What was the proper way to upgrade my ram in ubuntu on a laptop?

Thanks for your help.

What are the specs on your laptop.

Processor, video, etc.?

---

