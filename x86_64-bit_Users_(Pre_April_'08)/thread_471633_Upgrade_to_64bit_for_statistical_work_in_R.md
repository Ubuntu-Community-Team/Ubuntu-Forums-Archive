---
title: "Upgrade to 64bit for statistical work in R"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by dohyedan on 2007-06-12
Would appreciate any advice with the following dilemma:

I Am using a 32 bit version Ubuntu 7.04 on my Dell latitude D820 Intel core 2/duo with 2GB RAM.
I am using the R statistical package to model growth curves using the gamlss package. This is a complicated statistical procedure which eats up a lot of memory and takes a fair amount of time (I'm talking hours).

I am thinking about doing two make things run faster:
-add an extra 2GB of RAM
I have read some things about a 3.2GB limit of what the system can recognize but am not sure if this applies to my set up as well.
and even if this does apply do people think it would still be useful?

-upgrade to the 64bit version of UBuntu 7.04
I am not that experienced with Ubuntu so if I decide to do this this will probably cost me a fair amount of time and effort.
I would like to know if You think this upgrade is worth the trouble for the increase of speed that it might result in (that is assuming this would make things work faster)

Also if there is anyone out here with any experience in compiling R on a 64bit machine it would be great to hear your experiences.

Thank you for talking the time to help out a lost stranger.

Cheers,
Daniel

---

### Post by Cappy on 2007-06-12
I went ahead and looked for it in the repos.
It's version 2.4.1-1 while the newest version on the website is 2.5.0
I see they don't precompile 64-bit ubuntu on their site either =(

I'm not sure how much performance gain you'll see switching to 64-bit. It may be as little as 10% or as high as 40%. The only way to know for sure is to try it.

---

### Post by Bokonon on 2007-06-12
I would think you will see a benefit.  I see it going to 64 bit with Java apps, zipping files and doing light DVD burning.  During heavy computations is where the 64 bit system is supposed to shine.

I think the 3.2 GB limit depends on your board and OS.  32bit OS's probably won't be able to access the whole 4 GB, but your motherboard might also limit you.  Best to check with the manufacturer to see.  Even so, getting an extra 1.2G is going to help, so I would do it.

You might also check with the developers of R to see what they say.  For me, jBoss recommends a 64bit OS and JavaVM, so I went with it and have been pretty happy.  I use 32 bit firefox for flash/javaws applications and 32 bit skype, but everything else works well for me.

---

### Post by dohyedan on 2007-06-19
Sorry for the late reply, somehow thought I would be getting an email advising me that someone had responded to my post but no such thing.

Okay I think it is clear that I'm just going to have to give it a try and see the actual benefits are. Now just to find enough time to actually sit down and do it.

If I do get everything up and running I'll post back my experiences and otherwise you'll probably be seeing my crying or tearing my hair out in a different thread.

Thanks again for taking the time and help me out.

All the best,
Daniel

---

### Post by Cappy on 2007-06-19
You have to either set your posts to subscribe you to the thread in your forum preferences or you can do it at the top right of this page at " Thread Tools " (near report button).

---

### Post by incubus on 2007-06-19
Before compiling R from scratch, make sure you actually need the new features and bugfixes from version 2.5.0.  I've been using version 2.4.1 for a while and never had any issue.  It might be good experience to compile from the sources, but it may not be worth the trouble.

incubus

---

### Post by Jouke74 on 2007-06-21
> You could also keep it to 3 GB of ram...  
Higher than 3 GB is depending on your motherboard and other hardware. 

> Configure your swap file to be used as well, and limit your startup programs and processes. You might want to consider Kubuntu or Xubuntu as it will use less system memory. If you really need all your memory you could also start up with just the command prompt, although I am unfamiliar if R wants to start without gui.

> Your number crunching times will decrease. 
I run genetic simulations, likelihood maximizations on 64 bit and I do notice a big difference. 

> Safe you home directory somewhere (including hidden stuff) and reinstall ubuntu 64 bit. Most of your settings will be saved in your home dir (if you are not switching to Kubuntu or Xubuntu).

---

