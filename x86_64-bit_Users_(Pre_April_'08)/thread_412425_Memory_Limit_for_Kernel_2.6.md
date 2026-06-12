---
title: "Memory Limit for Kernel 2.6?"
date: 2007-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Long on 2007-04-18
In Neal Krawetz's article  "Hacking Ubuntu to Improve Performance ",

[http://www.extremetech.com/article2/0,1697,2114115,00.asp](http://www.extremetech.com/article2/0,1697,2114115,00.asp)

he siad "***the second limitation comes from the Linux 2.6 kernel used by Ubuntu's Dapper Drake (as well as other Linux variants). The kernel can only access 1 GB of RAM. Any remaining RAM is unused*.**" Is this statement correct for 7.04 AMD64 version? I am very serious about it. Thanks.

---

### Post by hardyn on 2007-04-18
responding with no technical knowlege... i would say a 'fault' like this would have been brought to public scrutiny by now if it were true; however, its usually a good idea to be sure of your facts before immotalizing your words in print media... its a very good question.

---

### Post by heimo on 2007-04-18
> **Long said:**
>  Is this statement correct for 7.04 AMD64 version? I am very serious about it.

I'm using 32-bit kernel from 7.04 with over 1GB without problems. It was also easy to use a different prepackaged version of kernel with over 1GB support back in Dapper (limitation was in the default kernel). I'm 99% sure 64-bit version doesn't have 1GB (or it was actually something like ~900MB) limitation.

---

### Post by prince_niceguy on 2007-04-18
this i not correct... 32bit OS has a restriction of 4GB RAM. 64 bit removes that restriction.

My friend has ubuntu with 2 GB running great. no problem reported so far.

---

### Post by heimo on 2007-04-18
Further reading on this subject:
[http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)
[http://www-128.ibm.com/developerworks/linux/library/l-memmod/](http://www-128.ibm.com/developerworks/linux/library/l-memmod/)

---

### Post by BoneKracker on 2007-04-18
In short, it's true, but it doesn't much matter.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by Kilz on 2007-04-18
> **BoneKracker said:**
> In short, it's true, but it doesn't much matter.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

That link is to a gentoo wiki so the information is ify at best. It gives information on gentoo , not ubuntu. Secondly it gives x86 information on a limit, not x86_64 or 64bit. 

> **Long said:**
> In Neal Krawetz's article  "Hacking Ubuntu to Improve Performance ",

[http://www.extremetech.com/article2/0,1697,2114115,00.asp](http://www.extremetech.com/article2/0,1697,2114115,00.asp)

he siad "***the second limitation comes from the Linux 2.6 kernel used by Ubuntu's Dapper Drake (as well as other Linux variants). The kernel can only access 1 GB of RAM. Any remaining RAM is unused*.**" Is this statement correct for 7.04 AMD64 version? I am very serious about it. Thanks.

From that link, [a few pages into the article.]("http://www.extremetech.com/article2/0,1697,2114123,00.asp")
[INDENT]
Computing Swap
There is a limit to the amount of usable RAM. **A 32-bit PC **architecture like the Intel Pentium i686 family can only access 4 GB of RAM. This is a hardware limitation. Assuming you can insert 16 GB of RAM into the computer, only the first 4 GB will be addressable. The second limitation comes from the Linux 2.6 kernel used by Ubuntu's Dapper Drake (as well as other Linux variants). The kernel can only access 1 GB of RAM. Any remaining RAM is unused. For this reason, it is currently not worth investing in more than 1 GB of RAM. Also, since the total virtual memory (RAM + swap) is limited to 4 GB, you should not need to allocate more than 3 GB of swap on a 1 GB RAM system.

Note: If you compile the kernel from scratch, there is a HIGHMEM flag that can be set to access up to 4 GB of RAM on a **32-bit architecture**. Unfortunately, there is a reported performance hit since most hardware drivers cannot access the high memory. If you set this flag, then do not bother with any swap space&#8212;the total amount of memory (RAM + swap) cannot be larger than 4 GB.[/INDENT]


As you can plainly read, **the author is talking about a 32bit kernel.** Not a 64bit kernel
Secondly he is talking about Ubuntu Dapper Drake 6.06 not Feisty Fawn 7.04 witch is 2 versions later. I would not follow any instructions that are 2 versions old. The information is going to be useless for the most part.

You are asking if the apple is in fact an orange.

---

### Post by dumbo on 2007-04-18
I'm not sure exactly what he means there.

From a practical point of view [feisty, but it worked in edgy as far as I remember]:

```
 

dmesg | grep Memory
[   45.160997] Memory: 2052900k/2097088k available (2217k kernel code, 43800k reserved, 1162k data, 304k init)

```

```

free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1984         27          0        201        797
-/+ buffers/cache:        985       1027

```

e.g. the machine has 2 gig of RAM, and as far as I know it will happily use that 2 gig of ram in 'real world' situations.

---

### Post by deadspider187 on 2007-04-18
I think what you're thinking of is the kernel option "highmem" which when disabled limits the available addressable RAM  to reduce kernel overhead if not needed.  I would assume that this would be enabled in both 64-bit versions of ubuntu and feisty.  There's also a 1 GB option to allow for 1 GB of RAM without the overhead of highmem, but I believe that's in mm- or ck-sources.

[http://www.linux-mips.org/wiki/Highmem]("http://www.linux-mips.org/wiki/Highmem")

---

### Post by Jouke74 on 2007-04-18
I don't know whether the **Kernel** will use more than 1 Gb of ram. To be honest, I hope my kernel uses as little resources and memory as possible. That leaves most memory free for programs. The question is can it allocate more than 1GB of Ram for these programs, and that answer is definitively a "yes". My program's go over 2 GB without any problem.... :D The problem comes when they start to use swapspace.

---

### Post by nss0000 on 2007-04-18
I run Dapperx54 with 2gigs ram installed and they are reported by dmesg etc.

nss
******

---

### Post by BoneKracker on 2007-04-18
> **Kilz said:**
> That link is to a gentoo wiki so the information is ify at best. It gives information on gentoo , not ubuntu. Secondly it gives x86 information on a limit, not x86_64 or 64bit. 

I added that link to supplement the ones just above it already given by another person.  They had more than adequate discussion about the 32-bit vs 64-bit hw limitations, the nature of memory zones, etc.  What they didn't talk about much was kernel configuration.  And Gentoo is a GNU/Linux distribution just as Debian is -- it's all the same kernel.  The memory management features in question here have been standard since kernel 2.4.  The gentoo link was useful because they provide more documentation regarding kernel configuration than most distributions, because they assume most of their users will, in fact, custom compile their kernel.  The information is not "ify".

I think there was one useful part of your largely non-constructive post though.. you reiterated the fact that some readers (including the thread starter) were apparently confused by the author's statements and misinterpreted them to imply an overall limitation on the usage the memory.  I think many of the people who had responded assumed everyone understands the concept of virtual memory management (which you and I probably used for the first time around 1991).

However there are other important points that contrary to your negative assessment of the posts, did need to be said:
[LIST]
[*]technically there is a limit to how much RAM the kernel can directory address - that's true regardless of 32-bit, 64-bit, etc.
[*]it's solved by virtual memory management, which has been included in the kernel for years
[*]it is a compile-time configuration option (which depends to some degree on the arch)
[/LIST]

---

### Post by Kilz on 2007-04-18
> **BoneKracker said:**
> I added that link to supplement the ones just above it already given by another person.  They had more than adequate discussion about the 32-bit vs 64-bit hw limitations, the nature of memory zones, etc.  What they didn't talk about much was kernel configuration.  And Gentoo is a GNU/Linux distribution just as Debian is -- it's all the same kernel.  The memory management features in question here have been standard since kernel 2.4.  The gentoo link was useful because they provide more documentation regarding kernel configuration than most distributions, because they assume most of their users will, in fact, custom compile their kernel.  The information is not "ify".

I think there was one useful part of your largely non-constructive post though.. you reiterated the fact that some readers (including the thread starter) were apparently confused by the author's statements and misinterpreted them to imply an overall limitation on the usage the memory.  I think many of the people who had responded assumed everyone understands the concept of virtual memory management (which you and I probably used for the first time around 1991).

However there are other important points that contrary to your negative assessment of the posts, did need to be said:
[LIST]
[*]technically there is a limit to how much RAM the kernel can directory address - that's true regardless of 32-bit, 64-bit, etc.
[*]it's solved by virtual memory management, which has been included in the kernel for years
[*]it is a compile-time configuration option (which depends to some degree on the arch)
[/LIST]

No, the kernel in Gentoo is not the same kernel that is in Ubuntu. The Gentoo kernel is compiled by the user. The compile options of the Ubuntu kernel and the Gentoo kernel will be different. Mainly because the Gentoo kernel is compiled per machine , and the user can set the flags. The ubuntu kernel is already compiled
The Ubuntu kernel is in a package made by the Ubuntu developers. That makes the Gentoo information useless. That it is talking about x86 makes it even more useless on the 64Bit section of the UBUNTU forums.
There is always a limit, but the limits of 32bit (4gb) and 64bit (64gb) are also different.

---

### Post by BoneKracker on 2007-04-18
No, it is the same kernel.  It's precisely the same source code.  They will have some different patches applied, but right now there are none that I'm aware of that any bearing on memory management.  The options that control memory management are features of the Linux kernel.  There are memory management patches, but the major distributions are all using the kernel's core memory functionality as far as I know.

```
The compile options of the Ubuntu kernel and the Gentoo kernel will be different.
```
Yes, that's correct, in general.  But it is irrelevant.  Unless whoever is doing the compiling is a incompetent, both will have the appropriate memory management configuration options selected.  So for any given hardware configuration, their memory management configuration options should be identical (other than for unusual use-cases that are not relevant to this discussion).

What is not moot is having a user understand why the 1GB kernel address space limitation has little or no bearing on their performance.  That involves understanding the principles of Linux virtual memory management and kernel configuration.  Granted, a Debian or Ubuntu page that addresses both the principles of Linux virtual memory management and the relevant kernel configuration options would have been more apropos.  I didn't see one, though.

Members of the Linux, GNU, and free software community in general should be careful about developing the "Not invented here." mentality.  There is very little in Ubuntu that WAS "invented here".  Users of different distributions, members of different communities, even developers of competing technologies should respect and support each other's work.  Making disparaging remarks about other Linux distributions isn't productive.  Debian, Redhat, SUSE, Gentoo, and many other communities have built and shared with each other the bits and pieces that make up Ubuntu.  And the knowlege and documentation that exists in those communities is relative and part of the overall GNU/Linux community of which Ubuntu is a growing part. 

I do understand your point about the 32-bit / 4 GB limit.  Some of the readers were in fact misreading that author's point.  Some of the other people responding though, were beyond that and trying to explain other relevant facts.

Let's not argue.

---

