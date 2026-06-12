---
title: "4g memory"
date: 2008-08-19
forum: x86 64-bit Users
---

### Post by MrKlean on 2008-08-19
I installed 4g ram on my acer aspire 5720z.  It keeps locking up..I was wondering if anyone has successfully used 4gig on ubuntu 8.04 64bit ??
Thanks ; )

---

### Post by tuxxy on 2008-08-19
Yes I use that amount on a secondd system, is the RAM new, could it be bad?

---

### Post by insane_alien on 2008-08-19
4G in my inspiron 1525 here running fine. 

run a memtest on it and maybe see if theres a firmware update for your mobo

---

### Post by stchman on 2008-08-19
> **MrKlean said:**
> I installed 4g ram on my acer aspire 5720z.  It keeps locking up..I was wondering if anyone has successfully used 4gig on ubuntu 8.04 64bit ??
Thanks ; )

My Toshiba laptop has 4G (DDR2 667) and my desktop has 6GB (DDR2 800) all using 8.04.

You may have the wrong type(speed) of RAM.  What type of memory does your laptop need?

---

### Post by soxs on 2008-08-19
A: Did you plug additional 2GB in AFTER having a running system with 2 GiB of RAM or did you build up a fresh system with a fresh install? If the fisrst applies to your system, you may change your memory ranges (Which is a little more compilcate, but before you attempt to do that do B.).
B: Do a RAM check, insert the ubuntu disk and sleect ramtest.
C: Running 4GiB with x86_64bit Hardy Heron just fine. Didn't get single lockup since fglrx 8.6 :-P

---

### Post by stchman on 2008-08-19
> **soxs said:**
> A: Did you plug additional 2GB in AFTER having a running system with 2 GiB of RAM or did you build up a fresh system with a fresh install? If the fisrst applies to your system, you may change your memory ranges (Which is a little more compilcate, but before you attempt to do that do B.).
B: Do a RAM check, insert the ubuntu disk and sleect ramtest.
C: Running 4GiB with x86_64bit Hardy Heron just fine. Didn't get single lockup since fglrx 8.6 :-P

I originally had 2GB in both PCs.  I upgraded and the Ubuntu saw the extra RAM.  No problem.

---

### Post by felker2 on 2008-08-19
> **MrKlean said:**
> I installed 4g ram on my acer aspire 5720z.  It keeps locking up..I was wondering if anyone has successfully used 4gig on ubuntu 8.04 64bit ??
Thanks ; )

I'm running Ubuntu 8.04 64-bit on my 4GB Athlon64 X2. No problems at all.

In case of possible memory problems, I would run memtest from the Ubuntu boot menu

---

### Post by elmoosecapitan on 2008-08-19
If your question is really to anyone using more than 2GB of RAM, then yes, 64-bit Ubuntu is running finely with 3GB of RAM. Advice: memory test.

cheers

---

### Post by MrKlean on 2008-08-19
well, it's pc25400 which is supposed to work on here. As far as I know..there isn't any diff between the pc2 5300 and pc2 5400, but I've been wrong before LOL!!  I'll try the memtext...
thanks ; )

---

### Post by soxs on 2008-08-20
> **stchman said:**
> I originally had 2GB in both PCs.  I upgraded and the Ubuntu saw the extra RAM.  No problem.
It doesn't apply to all boxes, having problems recoginzing added RAM, but some do have serious stability problems afterwards.

---

### Post by jespdj on 2008-08-20
> **MrKlean said:**
> I installed 4g ram on my acer aspire 5720z.  It keeps locking up..I was wondering if anyone has successfully used 4gig on ubuntu 8.04 64bit ??
The problem is not with Ubuntu because 4 GB (or more) of RAM works without any problems for many people using 64-bit Ubuntu 8.04, including me (on my XPS M1530).

In the GRUB boot menu, boot the memtest86+ option. Let the memory test run for a number of hours and see if it comes up with any errors. If it does, then there is most likely a hardware problem with your RAM.

Please give more details about your problem. When does it lock up? At boot? Or at some random moment?

---

### Post by Roaster on 2008-08-20
I don't know if this will help in your instance but, I had many problems after I installed 4g of ram in my computer. Finally figured out, with the help of people here, that by going into the bios and setting memory remapping to 'enabled',( it's disabled by default on this motherboard), it is working beautifully now and showing ALL of my memory. Hope you can get it sorted out.

---

### Post by cocokiwi on 2008-08-20
> **MrKlean said:**
> I installed 4g ram on my acer aspire 5720z.  It keeps locking up..I was wondering if anyone has successfully used 4gig on ubuntu 8.04 64bit ??
Thanks ; )

there is a bug in the BIOS,go get the Latest BIOS update to fix!

I,m using 4gig with Ubuntu and Vista/XP 64bit:lolflag:

the memory mapping of the BIOS was cutting off at 3gig and not allowing the full 4 gig memory to be used,if 4 gig was installed it crashed when memory over what the BIOS allowed was accessed.

That's what I thought anyway!:confused:

So older motherboards need the BIOS replaced to fix this!](*,)


Dennis:biggrin:

---

