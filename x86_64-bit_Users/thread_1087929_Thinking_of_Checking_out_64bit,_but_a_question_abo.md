---
title: "Thinking of Checking out 64bit, but a question about my laptop in concern!"
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by Firestem4 on 2009-03-05
Well i've been reading up about 64bit. Although there isn't too much information that I either don't know or the kind I want and can't seem to find.

Anyways. I have a few questions if anyone can help (And yes, I did read the sticky at the top, these questions are different).

I have an HP Laptop with an Intel Core2Duo (1.5ghz), and 2gb of RAM.

I know the most prevalent advantage with 64bit architecture is the increased ram support (4gigs to multiple exabytes), And the larger data pipes. However, I am curious if there is any drawback from 32bit OS using a 64bit with only 2 gigs of RAM. (Considering at least the hardware requirements of most heavyweight Linux Distro's, I expect performance to sill outperform Vista/XP).

Also, I am certain that due to the physical construction of the technology (64bit pipes) and utilising more resources, that Energy Consumption must be higher. Does anyone have any performance statistics for energy consumption vs 32bit? (I am concerned about this because I am going to put this on a Laptop that has limited battery performance as it is. And I tell you - Vista on a laptop does not bode well for battery life as it is lol)

Thanks in advance!

---

### Post by Vince4Amy on 2009-03-05
If everything is working fine for you I wouldn't bother upgrading to 64bit yet. Just keep what works.

---

### Post by dcstar on 2009-03-05
> **Firestem4 said:**
> 
........
Also, I am certain that due to the physical construction of the technology (64bit pipes) **and utilising more resources, that Energy Consumption must be higher**. Does anyone have any performance statistics for energy consumption vs 32bit? (I am concerned about this because I am going to put this on a Laptop that has limited battery performance as it is. And I tell you - Vista on a laptop does not bode well for battery life as it is lol)


You are not using "more" resources, you will be using the existing ones more efficiently. If it takes two CPU cycles to move data using 32 bit transfers then using one CPU cycle to move the exact same data in 64 bit mode is inherently more efficient. The power use per cycle would be virtually the same in 32 or 64 bit mode, your 64 bit hardware is draining (virtually) the same amount of power whether you use it with 8, 16, 32 or 64 bit software.

As far as consumption goes, that is irrelevant to the hardware mode used, it is up to how the software implements any energy saving features.

AFAIK Vista use more power because of the useless "eye candy" that gobbles up lots of resources to deliver fancy screen effects, if you set up Ubuntu (in 32 or 64 bit) to do similar things then the battery life will be just as poor.

---

### Post by 3Miro on 2009-03-05
64 bit apps are generally bigger (not 2 times bigger, just little bit bigger). Thus they will use more ram and more more energy. Overall the increase is small so it is generally worth the trouble compared to the gain.

On a 2GB machine, the gain would also be small. Unless you are doing a lot of video editing and/or numerical simulations and/or something else that requires/strongly-benefits from 64-bit, the difference would be negligible.

When I was running dual boot 32bit - 64bit Kubuntu on my desktop, I noticed that the 64bit version works slightly faster (for regular applications). However, the difference was very small (AMD CPU I don't know about Intel).

Vista uses ridiculous amount of RAM even for the simplest tasks. Ubuntu, even with all the compiz effects running, uses half to a third less. It is guaranteed to give you better battery life than Vista.

---

### Post by Firestem4 on 2009-03-05
Thanks for the replies. At the moment I still don't know what I'll choose. I don't think that it will matter either way then. 

Although I guess depending on how long it takes for Chakra 64bit liveCd to come out, or wait for a new version of Kubuntu before I reformat this laptop.

---

