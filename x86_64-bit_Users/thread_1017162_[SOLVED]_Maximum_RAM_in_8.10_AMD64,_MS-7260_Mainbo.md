---
title: "[SOLVED] Maximum RAM in 8.10 AMD64, MS-7260 Mainboard"
date: 2008-12-20
forum: x86 64-bit Users
---

### Post by Nation5 on 2008-12-20
What is the maximum RAM I can have with this combination?

My mainboard manual says there is a max of 4GB.  This thread: [http://ubuntuforums.org/showthread.php?t=559325]("http://ubuntuforums.org/showthread.php?t=559325") shows my board to have a max of 8GB.
I am running 8.10 x86-64. Is there a way to tell for sure,(i.e. right-click properties on my computer for windows)?
Since I am running 64 bit, does that somehow bypass the physical limitations of the mainboard's 4GB?
Is that thread I referenced incorrect?
I am running a Athlon64 3500+ w/ 2x512 PC6400 DDR2, and there is a great deal where after mail in rebate I can get 4x2gb for $40 total.  I just want to know if it's possible to run 8GB like the other thread says.
Thanks in advance for any help.

---

### Post by madverb on 2008-12-20
A BIOS update may have increased the maximum RAM capacity. With 64 bit you can increase your RAM but only if the motherboard is capable of handling more RAM.

---

### Post by Nation5 on 2008-12-20
Is there a way to check on BIOS version through ubuntu, or the terminal?

---

### Post by cariboo on 2008-12-20
If you had clicked on the link to MSI's web site you would have seen the the 8Gb is a typo:

Qoute from [MSI]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=255&maincat_no=1&cat2_no=171")
> Main Memory

&#8226; Supports Dual DDR II 533/667/800
- 4 DDRII DIMMs (240pin / 1.8V)
- Supports a maximum memory size up to 4GB.

A BIOS upgrade would not fix your motherboards limitations :(

Jim

---

### Post by Nation5 on 2008-12-23
I was at the MSI site, *and* had my manual open and both said 4GB.  So I just wanted to make sure there wasn't something cool that I didn't even know about my motherboard in combination with Ubuntu.  Thanks for clearing that up though, I'm off to purchase 4GB of ram.

---

