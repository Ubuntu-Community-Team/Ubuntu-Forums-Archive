---
title: "64 bit need more RAM than 32 bit?"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by garton on 2007-09-18
In general, does Ubuntu 64 bit require more RAM than Ubuntu 32 bit in order to show equivalent performance? I.e., does the 64 bit system itself consume more resources before the user starts an application than a 32 bit system does?

---

### Post by marco123 on 2007-09-18
No.  It can address more RAM than a last gen OS, but doesn't need more RAM.

---

### Post by bigtom2 on 2007-09-18
As Always The More Memory The Smother Things
Run I Have A Gig On 64 Bit Amd 3800 It Works Very
Good An Fast. But You Dont Have To Have More
Ram To Run 64 Bit.at Least 256mb To Have Good Resluts.

---

### Post by tanchao on 2007-09-18
that's no true!!!

---

### Post by Kilz on 2007-09-18
The idea that 64bit uses more ram is something some people use as a reason to not use the 64bit version. The 64bit version may use slightly more ram, but that ram isnt wasted, its being used. The benefits far outweigh the drawbacks. If you have 512 of ram you will do ok, and that is most often the low point on 64bit systems. I had 1 gig and rarely used swap. I now have 2 gb and never use swap.
Ram is so cheap nowadays why worry if it uses slightly more ram? For $54 I got a gig of ram at tiger direct. The performance increase was well worth the $54 bucks.

---

### Post by garton on 2007-09-19
> **Kilz said:**
> The idea that 64bit uses more ram is something some people use as a reason to not use the 64bit version. The 64bit version may use slightly more ram, but that ram isnt wasted, its being used. The benefits far outweigh the drawbacks. If you have 512 of ram you will do ok, and that is most often the low point on 64bit systems. I had 1 gig and rarely used swap. I now have 2 gb and never use swap.
Ram is so cheap nowadays why worry if it uses slightly more ram? For $54 I got a gig of ram at tiger direct. The performance increase was well worth the $54 bucks.

How much more? Do you know what it is used for?

(I agree that RAM is so cheap it is worth buying some to get the extra boost.)

---

### Post by Jouke74 on 2007-09-19
The usage of RAM is fully dependent on the program, the coding and the program architecture. A 32 bit program running under 64 bit will use 64 bit libraries as well as 32 bit libraries and thus the amount of RAM used will be increased for this program. Furthermore the "32 bits" blocks are stored in "64 bits" blocks, hence increase of the use of RAM. However the increase it not twice as much. Some things that take 2x 32 bits may be programmed / compiled to use 1x 64 bit. A a result the program will use less memory as it stores "64" instead of "2" for index and "32" and "32". 

The inevitable answer on how much more memory you will use is: burn a live CD with 32 bit and 64 bit. And try the programs that you want to test. Check the memeory use withthe system monitor or another tool. (These CD's are made to try out aspects of the linux distro both for hardware and software).

---

### Post by Bill_Gates on 2007-09-19
> **garton said:**
> In general, does Ubuntu 64 bit require more RAM than Ubuntu 32 bit in order to show equivalent performance? I.e., does the 64 bit system itself consume more resources before the user starts an application than a 32 bit system does?

Yes. 64 bits programs eats more memory. From wikipedia [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

The main disadvantage of 64-bit architectures is that relative to 32-bit architectures the same data occupies slightly more space in memory (due to swollen pointers and possibly other types and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization.

---

### Post by garton on 2007-09-19
> **Jouke74 said:**
> The usage of RAM is fully dependent on the program, the coding and the program architecture. A 32 bit program running under 64 bit will use 64 bit libraries as well as 32 bit libraries and thus the amount of RAM used will be increased for this program. Furthermore the "32 bits" blocks are stored in "64 bits" blocks, hence increase of the use of RAM. However the increase it not twice as much. Some things that take 2x 32 bits may be programmed / compiled to use 1x 64 bit. A a result the program will use less memory as it stores "64" instead of "2" for index and "32" and "32". 

The inevitable answer on how much more memory you will use is: burn a live CD with 32 bit and 64 bit. And try the programs that you want to test. Check the memeory use withthe system monitor or another tool. (These CD's are made to try out aspects of the linux distro both for hardware and software).

Very useful information, thank you.

What my question boils down to, then, is: has anyone tried to boot equivalent Ubuntu Live CDs x86/x64, started the system monitor and noted the RAM consumtion right after boot, with no apps started? That, I guess, would at least be a hint about the increased RAM usage on a 64 bit system compared to 32 bit.

Again, I don't regard this as very much of a drawback to 64 bit desktop systems, since RAM is so cheap.

---

### Post by Kilz on 2007-09-19
> **Bill_Gates said:**
> Yes. 64 bits programs eats more memory. From wikipedia [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

The main disadvantage of 64-bit architectures is that relative to 32-bit architectures the same data occupies slightly more space in memory (due to swollen pointers and possibly other types and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization.

But isnt calling it a disadvantage based on a point of view? That the next section after the one you quoted on that page says
"Currently, most commercial software is built as 32-bit code, not 64-bit code, so it can't take advantage of the larger 64-bit address space or wider 64-bit registers and data paths on 64-bit processors, or, on x86 processors, the additional registers in 64-bit mode. However, users of free or open source operating systems have been able to use exclusive 64-bit computing environments for years. Not all such applications require a large address space or manipulate 64-bit data items, so they wouldn't benefit from the larger address space or wider registers and data paths; the main benefit to 64-bit versions of applications that wouldn't benefit from them would be that x86 versions would be able to use more registers."

Isnt having the information in ram so it can be used a benefit? Doesn't performance decrease when the processor has to keep moving information in and off of ram? 
Secondly, what amount of ram is to little for a 64bit machine? When is the use of more ram by applications a problem? Because if 64bit processors run fine on 512 meg (I know from experience they do) and that is the low end of ram in 64bit systems. Does the ram usage even matter?

---

### Post by crjackson on 2007-09-19
> **garton said:**
> In general, does Ubuntu 64 bit require more RAM than Ubuntu 32 bit in order to show equivalent performance? I.e., does the 64 bit system itself consume more resources before the user starts an application than a 32 bit system does?

I have 2 low end AMD64 systems with 384MB installed for the kiddies.  I have installed both the 32-bit and the 64-bit versions of Ubuntu 7.04.  Both versions worked well, but the 64-bit is snappier and detected all the hardware on the 1st and only install attempt.  I had to tinker more with the 32-bit version for the most part.  I reccomend the 64-bit version.

---

### Post by Sockerdrickan on 2007-09-19
Yes it takes more ram but I have 2048mb so it's ok

---

### Post by |Eric| on 2007-10-01
you guys are getting it upside down ! 64bit uses the registers in the CPU so it does not increase the ram usage it uses the memory you where NOT using (ie : the 32bit part of the register that you didnt use in 32bit) 

the increase ram usage is from loading a 32bit library in a 64 bit environment (thus duplication of program code) but that is marginal in linux becose you can recompile most apps to run in 64bit thus taking advantage of those 64bit registers !! twice as fast for the same $$ thats great! the only downside is drivers some lack devlopment in the 64bit range ...

---

### Post by Jouke74 on 2007-10-02
When I run Xubuntu 64 bit I am using 151 Mb of internal memory. When using Ubuntu I am using about 380 Mb. When additionally using XGL and Compiz it is about 450 MB mostly because of running XGL server.
All under 64 bit. Happy now? :)

---

