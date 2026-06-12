---
title: "x86_64 advantage (?)"
date: 2008-05-18
forum: x86 64-bit Users
---

### Post by alcatris on 2008-05-18
I saw that there are some threads related to building ubuntu for a specific architecture and  about the "fact" that a i686 optimized OS would perform better than a i486 optimized one. 
 So my question is: Given the fact that x86_64 arch is relatively new, a OS compiled specially for this arch would not perform better merely because it does not have to be backward compatible with all the processors starting with 486 and it can harness the full power of the system? 
If that is the case maybe it should be listed as a pro for the x64 ubuntu version given all the noise around arch specific compiled OS. 
Also I have noticed something else when switching from hardy x32 on hardy x64(besides the fact that the system responds more quickly) the battery lasts more on the x64 version and I think that this is related with the os being more efficient.
 Anyhow I'm more than happy with the x64 install and the way the entire process went. I don't have java support in firefox (but I'm pretty sure that one of the 3 sticky posts in this section will help so thanks in advance) but for what I care I must say a big THANK YOU for the x86_64 version of ubuntu.  
( I may be wrong on the battery life because I don't have a side by side installation of x32 and a x64 but all I can tell for sure is that on x32 version the battery life was about 2.5H and on x64 is about 3H. Maybe a patch was released at the time that I installed the x64 version but anyhow due to this fact regarding battery life I'm one step closer of dumping the windows install I have )

---

### Post by stmiller on 2008-05-18
There is nothing new about 64bit. Computers have gone:

8bit > 16bit (windows 3.1) > 32bit (majority now) > 64bit > 128bit (distant future!)

64bit Linux has been around in the world since probably 1999 or 2000. That is when the first 64bit cpus started becoming mainstream, though mainly in the server market at first.

---

### Post by Sef on 2008-05-19
[QUOTE]64bit Linux has been around in the world since probably 1999 or 2000. That is when the first 64bit cpus started becoming mainstream, though mainly in the server market at first.[QUOTE]

Actually 64-bit have been around since the 1960s, but they didn't hit the server market until the early 1990s.

---

### Post by DizzyTech on 2008-05-19
I'll describe 64-bit practically.  Computers interpret numbers in the form of bits at the core of their processor.  Put simply, 64-bits interprets numbers twice as large and twice as fast as 32-bit systems.

To properly use 64-bit, software must not only be recompiled with 64-bit tools, but also must (or should) use numbers in a 64-bit method.  Right now, many 64-bit software is just 32-bit software recompiled without too many optimizations.  However, you'll see more and more native 64-bit applications soon.

---

### Post by jdong on 2008-05-19
Currently for 95% of applications, the difference between 32-bit and 64-bit performance is negligible (sometimes a bit faster, sometimes a bit slower, sometimes equal).... Some multimedia and encryption apps have been hand-tuned to reap benefits of 64-bit integers for arithmetic and also the additional general-purpose registers, and those show on the order of a 10% performance increase....

Ultimately, IMO, pick whichever one is easier for you to set up. The primary advantage of 64-bit mode is to allow RAM-heavy server and computational processes to address more than 4GB of virtual memory.

---

### Post by jespdj on 2008-05-19
> **alcatris said:**
>  So my question is: Given the fact that x86_64 arch is relatively new, a OS compiled specially for this arch would not perform better merely because it does not have to be backward compatible with all the processors starting with 486 and it can harness the full power of the system?
Yes, there is some truth in this.

One example is [SSE instructions](http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions). SSE already existed before 64-bit extensions were added to x86 processors. Because of this, if you have a processor that is 64-bit capable, you can be sure that it also has SSE instructions. So 64-bit software can always use SSE instructions. On the other hand, there are 32-bit processors that do not have SSE instructions, so if you write 32-bit software that you want to be able to run on as many computers as possible, you cannot use SSE instructions (if you do, some people won't be able to run the program).

---

### Post by jdong on 2008-05-19
> **jespdj said:**
> Yes, there is some truth in this.

One example is [SSE instructions](http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions). SSE already existed before 64-bit extensions were added to x86 processors. Because of this, if you have a processor that is 64-bit capable, you can be sure that it also has SSE instructions. So 64-bit software can always use SSE instructions. On the other hand, there are 32-bit processors that do not have SSE instructions, so if you write 32-bit software that you want to be able to run on as many computers as possible, you cannot use SSE instructions (if you do, some people won't be able to run the program).

It should, however, be noted that most applications that benefit from SSE and similar instruction sets do have runtime branching logic that detects the type of CPU in use and activates additional CPU instruction sets if necessary. But indeed, lowest-common-denominator of x86-64 is more featureful than i386.

---

