---
title: "[SOLVED] How to maximize the RAM on ubuntu 64-bit"
date: 2008-06-29
forum: x86 64-bit Users
---

### Post by speedup on 2008-06-29
I guys, I just want to know what is the command to maximize the RAM using Ubuntu Hardy Heron-64 bit. I have installed 5 GB of RAM (I need such amount memory for the application I am using)

When I run free -m it says under total 3891 it does not detect the remaining 2 GB memory. I hope you can help me guys I really need this working. Thank you.

---

### Post by kuja on 2008-06-29
Maybe the problem can be resolved in your motherboard's BIOS. If there's any BIOS option about remapping memory, try flipping the setting for it. While on that topic, when you're in BIOS how much RAM does it say it has detected?

---

### Post by blastus on 2008-06-29
> **speedup said:**
> I guys, I just want to know what is the command to maximize the RAM using Ubuntu Hardy Heron-64 bit. I have installed 5 GB of RAM (I need such amount memory for the application I am using)

When I run free -m it says under total 3891 it does not detect the remaining 2 GB memory. I hope you can help me guys I really need this working. Thank you.

You've got a BIOS setting issue. I have 8GB of RAM and 8GB of SWAP. Here is the output from free -m on my machine

```
             total       used       free     shared    buffers     cached
Mem:          8002       6422       1580          0         32       5963
-/+ buffers/cache:        426       7575
Swap:         8191          0       8191

```

---

### Post by speedup on 2008-06-29
@blastus and @kuja

Your both correct, as I checked in my BIOS it says 4032. It should be a BIOS problem but I cannot see an option to remap the memory. I am using Asus P5B mobo. Do you have an idea on how to do this?

---

### Post by speedup on 2008-06-30
I installed windows vista with sp1 32-bit. It was able to detect my 5 GB when I go to system properties. Can you give me an I dea what's going on.

---

### Post by techstop on 2008-06-30
> **speedup said:**
> I installed windows vista with sp1 32-bit. It was able to detect my 5 GB when I go to system properties. Can you give me an I dea what's going on.

Vista 32-bit SP1 can "detect" the 5GB of memory, it certainly can't use it. Go to the Task Manager and tell us how much memory Vista thinks it has. ;)

If 64-bit ubuntu can't detect your full amount of memory, it is a hardware issue. I am running 64-bit hardy on my Dell XPS M1210 laptop, it only sees about 3.3GB, same as Windows 32-bit. It's a hardware limitation.

EDIT: A google for "p5b 4gb ram" came up with this as the first result;

[http://episteme.arstechnica.com/eve/forums/a/tpc/f/77909774/m/125007225831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/77909774/m/125007225831)

Apparently you need to enable "memory remapping" which you can find in the bios under advance>chipset>north bridge configuration.

---

### Post by Dixon Bainbridge on 2008-06-30
It definitely a hardware issue. My motherboard can only support 4gb memory. Check your MB manufacturers website for details on what your model can support.

---

### Post by speedup on 2008-06-30
@techstop

Thank you for the reply, Vista 32-bit did detect under Task Manager just 3.xx GB but I don't have the money to upgrade to Vista-64 bit that is why I went for Ubuntu 64-bit to maximize the RAM size. I will check the link that you have posted since the person talking have the same mobo (I just scan the first paragraph)

@Dixon Bainbridge
My mobo is Asus P5B and base on the manual it should support 8 GB of RAM. Maximum of 2 GB per RAM slot.

As of this moment my current configuration is, I have 2x2G RAM and 2x512 MB RAM. Would this be the culprit you think?

---

### Post by speedup on 2008-06-30
@techspot,

I just downloaded the manual for Asus P5B and its very unfortunate that under BIOS->Advance Chipset -> North Bridge, it does not have an option for Memory remapping. 

Should I really look for this option I asked this cause based on the link that you provided one of the forumers mention that in the BIOS it did not detect the 4GB but as I could remember (I am at work right now)it was able to mention that it was able to detect 4032 MB usable memory (I need to verify this when I go home). Haaayyyy, I think I need to upgrade my mobo, but it will take a long time haaaayyyyy!!!!!! 

I hope I can still fix this without buying a new mobo.

---

### Post by speedup on 2008-06-30
Hi guyz,

Just got home and decided to remove the 2x512 MB RAM. After rebooting and checking the BIOS->Advance->Chipset->North Bridge. The RAM mapping appeared and I was able to enabled it. After enabling it it was able to detect the 4 GB RAM. 

I would really like to thank you all for helping me in this problem. Without your help I would not be able to fix the problem.

---

### Post by d4v1dv00 on 2008-06-30
In mine, the BIOS reads 4GB but Hardy reads 3.9GB

---

### Post by techstop on 2008-07-01
> **speedup said:**
> Hi guyz,

Just got home and decided to remove the 2x512 MB RAM. After rebooting and checking the BIOS->Advance->Chipset->North Bridge. The RAM mapping appeared and I was able to enabled it. After enabling it it was able to detect the 4 GB RAM.

Be sure to mark the thread [SOLVED].

> **speedup said:**
> I would really like to thank you all for helping me in this problem. 

Well go on then. ;)

---

### Post by hyper_ch on 2008-07-01
> **blastus said:**
> 
```
             total       used       free     shared    buffers     cached
Mem:          8002       6422       1580          0         32       5963
-/+ buffers/cache:        426       7575
Swap:         8191          0       8191

```

How can you fill 6.4 GB ram?

---

### Post by Dixon Bainbridge on 2008-07-01
> **speedup said:**
> Hi guyz,

Just got home and decided to remove the 2x512 MB RAM. After rebooting and checking the BIOS->Advance->Chipset->North Bridge. The RAM mapping appeared and I was able to enabled it. After enabling it it was able to detect the 4 GB RAM. 

I would really like to thank you all for helping me in this problem. Without your help I would not be able to fix the problem.

Excellent! One tip with RAM, dont mix different sizes of RAM, its not efficient, so you did the right thing with getting rid of the 512MB sticks. Also, 64-bit systems address and page memory differently to 32-bit systems, which is why it looks like 64-bit systems are using up more resources, or aren't "seeing" all of the memory (eg 3.9GB when you have 4GB installed).

---

### Post by speedup on 2008-07-01
Again thank you so much guys your the best

---

### Post by techstop on 2008-07-01
> **techstop said:**
> Well go on then. ;)

> **speedup said:**
> Again thank you so much guys your the best

Haha, I didn't mean for you to *literally* thank us, I meant you should click on the "thanks" icon in the thread under helpful posts like this --> [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG]

But anyway, good to hear you got it sorted!

---

### Post by blastus on 2008-07-01
> **hyper_ch said:**
> How can you fill 6.4 GB ram?

Watch a DVD movie :popcorn:

---

### Post by Dixon Bainbridge on 2008-07-01
> **blastus said:**
> Watch a DVD movie :popcorn:

Or my favourite - batch convert 100 90MB image files in a virtual install of lightroom in XP. Watch the useable ram drop like a stone.

---

