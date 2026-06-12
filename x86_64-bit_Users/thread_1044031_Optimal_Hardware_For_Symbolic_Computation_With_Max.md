---
title: "Optimal Hardware For Symbolic Computation With Maxima and Sagemath"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by csaratchand on 2009-01-19
1. I use Maxima for symbolic computation tasks that arise as part of my research work in macroeconomics. I presently use Ubuntu 8.10 32 bit with the 2.6.27-9 server kernel. The Maxima Version is 5.17.0 compiled with GNU Common Lisp 2.6.7; the deb packages are from Debian Sid. 
2. When I posted a query in the mailing list of Maxima, I was informed that shifting to 64 bit (and possibly better hardware) can result in better performance to some extent in terms of computational speed.
3. As a result I have been looking around for hardware that can adequately support a 64 bit installation. I have met with indifferent results. For instance many motherboards (which are not server based) have a maximum capacity of 8 GB RAM (=4 sticks of 2 GB each) but have a number of problems running at full RAM capacity (e.g. 4 GB RAM [=2x2 GB] is OK but 8 GB RAM is not OK) or running full capacity with the best of the supported RAM is not possible (e.g. 8 GB of DDR2-800 RAM is OK but 8 GB DDR2-1066 RAM is not OK). I am looking forward to any suggestions about motherboards that can run its best supported RAM (e.g. 8 GB DDR2-1066)  RAM without hitches. Given the motherboard any suggestion of the appropriate CPU would also help matters. 
4. I am currently using the following hardware: 
a. AMD Athlon X2 5600+ Dual Core Processor
b. Asus M2A-VM Motherboard
c. 4 GB DDR2-800 Corsair RAM TWIN2X4096-6400C5DHX
5. Along with the shift to a 64 bit installation I also plan to start using Sagemath which (unlike Maxima it seems) does have support for parallelization. I will seek to use Sagemath to run Maxima. In this light ATI Catalyst 8.12 has announced support for ATI Stream Computing that allows the GPU to partake of hitherto CPU based tasks. So a recommendation of an appropriate GPU is also called for.
C. Saratchand

---

### Post by cariboo on 2009-01-19
If you want support for more than 8Gb ram, you will have to stay away from normal consumer motherboards.

Check out [Tyan]("http://www.tyan.com/index.aspx").

Jim

---

### Post by csaratchand on 2009-01-20
1. Tyan seems to be a manufacturer of server motherboards among other things. I think one will go to this option when all other options have been well and truly exhausted.
2. I seemed to have over-emphasized the RAM part of my question. What I meant to say was the following: are there any motherboards (+CPU+GPU) which can comfortably run a 64 bit operating system. Even if only 8 GB RAM can be run, will it run well, without the hitches that get reported in the forums of hardware manufacturers. If required I will post specific examples of such problems.
c. saratchand

---

