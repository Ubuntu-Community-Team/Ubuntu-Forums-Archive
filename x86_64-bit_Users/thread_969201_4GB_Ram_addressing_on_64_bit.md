---
title: "4GB Ram addressing on 64 bit"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by luke74 on 2008-11-03
Hi all,
i have a 64 bit machine with ubuntu 64 installed on it. I have 4gb Ram but i currently see only 3.7 gb installed. how can i solve this problem?

Any help is welcome!

thanks

luke

---

### Post by mirca_sp on 2008-11-03
Hi,
Do you have on-board video? Try checking the ´free´comand.
It might help.

---

### Post by cocokiwi on 2008-11-04
> **0101 said:**
> I have a related issue. I just upgraded my memory capacity and would like to run memtest to check the memory. Every time I run memtest it will crash within a few seconds, even if I run it off the live cd. If I take out the new sticks of ram memtest  will run fine. Also, although memtest crashes ubuntu will boot and run for hours/days without a hitch.

My set up is:
AMD 65 3500+
ASUS A8V deluxe Mobo
2X512MB  OCZ Dual Channel DDR400
2X1GB  OCZ Dual Channel DDR400(New Sticks)
Ubuntu 7.10 x86-64

-thanks.

p.s. Sry if this doesn't relate to the previous post but this seemed like the most logical place :biggrin:.
To ALL in this thread!

 I would GUESS!  You did NOT update your BIOS since you got your computer or Motherboard! RIGHT ?

   Do it NOW cause THAT is your problem! a nasty bug popped up when 64 bit OS's came along.people with VISTA 64 or XP 64 suddenly found out they could NOT install without removing 2 gig of memory before doing it! MS came out with a fix that did allow 4 gig...problem was you had to have it installed already!and either way one only had 3 gig of memory to use,if more is installed BSOD would appear...and you would not be able to install! linux just don't see it!
at the beginning of last year,it finaly got back to the BIOS programmers whom FIXED the Memory mapping problem that caused this! HENCE the BIOS update! so get the LATEST update and install it!

Cheers Dennis

---

### Post by luke74 on 2008-11-04
This is the result of the command free:


             total       used       free     shared    buffers     cached
Mem:       3889696    3005380     884316          0      43456    1293580
-/+ buffers/cache:    1668344    2221352
Swap:      7871808          0    7871808

---

### Post by luke74 on 2008-11-04
I have a laptop so it could be that the video card is getting memory from the RAM?
I have an hp pavillion dv6000 laptop model

---

### Post by handydan918 on 2008-11-04
> **luke74 said:**
> I have a laptop so it could be that the video card is getting memory from the RAM?
I have an hp pavillion dv6000 laptop model

Yeah, that is normally what video cards do if they don't have enough on-board memory-they "appropriate" some from system memory. Perfectly normal.

---

### Post by agathian on 2008-11-04
Well, it might be a motherboard issue... check this out.

[http://www.codinghorror.com/blog/archives/000811.html](http://www.codinghorror.com/blog/archives/000811.html)

Couple of months back i ran into similar issue. Installed 32 bit first and then switched to 64-bit, still didn't see the whole 4G. Googling around i found several references to the problem mentioned in the above post. There were some workarounds mentioned like memory remapping.

It took me a while to get that far - and i didnt have time to do more research and confirm "absolutely" if that was the case with my machine, or figure out the workarounds.

Hope this helps!

-A

---

### Post by grep65535 on 2008-11-05
> **luke74 said:**
> I have a laptop so it could be that the video card is getting memory from the RAM?
I have an hp pavillion dv6000 laptop model

I have 4GB in my system and my 'free' output for total = 4,055,772
I just upgraded to 64-bit a few days after I upgraded from 2GB > 4GB, and noticed when I was in 32-bit land that my free memory was exactly what you report(3,889,696).


1.) Check BIOS regarding memory sharing with video
2.) Check uname -a to make sure you actually are using x86_64 (just in case ;-) )
3.) Look into an upgrade for your BIOS
4.) It might just be your laptop's way of doing things...

:popcorn:

---

### Post by Dixon Bainbridge on 2008-11-05
> **luke74 said:**
> Hi all,
i have a 64 bit machine with ubuntu 64 installed on it. I have 4gb Ram but i currently see only 3.7 gb installed. how can i solve this problem?

Any help is welcome!

thanks

luke

64bit systems address and use memory differently to 32bit systems. There is nothing wrong with 3.7Gb reading.

---

### Post by Kevbert on 2008-11-05
I have 3.96Mb reported on my desktop for 4Gb installed. It's more than likely that the video card is using some of the memory. You may have an option in bios to memory remapping. It may come up as something like 'use memory hole' as this was an old idea that no-one would ever use more than 3.2Gb of memory. The idea was to use the memory addresses above this limit for the various PC peripherals such as I/O control.

---

