---
title: "ia32-libs - maximum allowed RAM ?"
date: 2009-01-17
forum: x86 64-bit Users
---

### Post by odejoy on 2009-01-17
hi,

if i am running a 32-bit (i386) executable via the ia32-libs on x86_64, how much is the maximum RAM allowed/addressable by the 32-bit executable?

i have a custom program that only available as a 32-bit binary and i would like to know if having 8GB RAM on my system would be of any advantage...

thanks!

---

### Post by jespdj on 2009-01-18
32-bit software cannot address more than 4 GB, it doesn't matter if it is running on a 32-bit or 64-bit system. So, installing 8 GB RAM in your computer will not help for this program.

---

### Post by odejoy on 2009-01-18
Thanks! That makes my decision a lot simple.

---

### Post by michael37 on 2009-01-19
The only advantage of 8GB of RAM is that you can run two instances of this program...

It may get handy with a multicore CPU if the presumably older 32-bit program is single-threaded.

---

### Post by dcstar on 2009-01-20
> **odejoy said:**
> hi,

if i am running a 32-bit (i386) executable via the ia32-libs on x86_64, how much is the maximum RAM allowed/addressable by the 32-bit executable?

i have a custom program that only available as a 32-bit binary and i would like to know if having 8GB RAM on my system would be of any advantage...

thanks!

The application may be able to only address 4G, but the base O/S and any other 64 bit apps running will be able to use the other 4G, so there is some advantage to having 8G.

---

