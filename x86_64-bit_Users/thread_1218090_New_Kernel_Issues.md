---
title: "New Kernel Issues"
date: 2009-07-20
forum: x86 64-bit Users
---

### Post by kneewax on 2009-07-20
I did something silly.  I was trying to fix an issue my x64 Jaunty machine has with constant 'spasms' where the current application freezes or locks up for a minute at a time, seemingly randomly.

One article I found on this forum suggested updating to the most recent Kernel (2.6.29) to fix this.  So I did.

However this has screwed my NVIDIA driver setting and caused Jaunty to run only in low-graphics mode.

No amount of tweaking seems to get the NVIDIA proprietary drivers running.

I used Grub to boot the previous kernel (2.6.28-13) and the systems runs fine.

Can anyone give me tips on how to either get NVIDIA drivers running in 2.6.29 OR restore the default version of Jaunty to the working Kernel.

Thanks

---

### Post by p0cky84 on 2009-07-20
Did you google this before asking? ...

---

### Post by kneewax on 2009-07-20
thanks and this is helpful why?  

Yes, believe it or not I did, but this forum has always been a place where you could ask even obvious questions without being flamed or narked at.  

I googled it and found the work around of changing the default grub selection.  This I did.  BUT that leaves me with the system locking up.  I'd like to find help on getting the NVIDIA drivers working in the newer Kernel.  Also I have no idea what the implications are, if any,  of using the older Kernel when you've updated to a newer one.

So thanks, but no-thanks.

[Edit] OK I admit, that was a bit grumpy - sorry.  I am just getting frustrated, and really it is better not to post at all than to post a message with no real help in it.  [/Edit]

---

### Post by p0cky84 on 2009-07-20
Sorry, don't be offended.

I just did a google search and there was several titles concerning the same issue as you had.

---

### Post by Arup on 2009-07-20
Try installing nvidia drivers via .sh downloaded from nvidia site. To install that you must remove all existing nvidia drivers and also remove linux restricted moduels common.

---

### Post by regala on 2009-07-20
> **kneewax said:**
> thanks and this is helpful why?  

Yes, believe it or not I did, but this forum has always been a place where you could ask even obvious questions without being flamed or narked at.  

I googled it and found the work around of changing the default grub selection.  This I did.  BUT that leaves me with the system locking up.  I'd like to find help on getting the NVIDIA drivers working in the newer Kernel.  Also I have no idea what the implications are, if any,  of using the older Kernel when you've updated to a newer one.

So thanks, but no-thanks.

[Edit] OK I admit, that was a bit grumpy - sorry.  I am just getting frustrated, and really it is better not to post at all than to post a message with no real help in it.  [/Edit]

the problem you have is simple, your new kernel does not have a suitable nvidia-driver. you can tweak it all you want, it won't have any effect until you have a driver that your kernel can load: you have to rebuild it from "source" against your very running kernel version. How to do that, on the contrary, I know, but I guess I'd search for your particular system (Ubuntu) a saner way than just build it and install it boldly into your system. There must be a way to build a deb package from the source, that will install the new driver.

---

### Post by tgalati4 on 2009-07-20
nVidia driver will almost always need to be built from scratch with a new kernel.  If this fails post a bug at kernel.org.  

When you run proprietary drivers you get better performance at the expense of installation/upgrade issues.

---

### Post by cenwesi on 2009-07-20
You will need a patch. I recompiled a kernel 2.6.31-rc3 yesterday and followed this link [http://www.nvnews.net/vbulletin/showthread.php?t=134779](http://www.nvnews.net/vbulletin/showthread.php?t=134779)

---

### Post by philcamlin on 2009-07-20
> **cenwesi said:**
> You will need a patch. I recompiled a kernel 2.6.31-rc3 yesterday and followed this link [http://www.nvnews.net/vbulletin/showthread.php?t=134779](http://www.nvnews.net/vbulletin/showthread.php?t=134779)

try filing a bug report too

---

### Post by regala on 2009-07-21
> **cenwesi said:**
> You will need a patch. I recompiled a kernel 2.6.31-rc3 yesterday and followed this link [http://www.nvnews.net/vbulletin/showthread.php?t=134779](http://www.nvnews.net/vbulletin/showthread.php?t=134779)

if someone told him to go 2.6.30, I wouldn't stress out enough the fact that 2.6.31-rc3 is not stable, and that with 2.6.30, he wouldn't need a patch :)

---

### Post by kneewax on 2009-07-23
> **p0cky84 said:**
> Sorry, don't be offended.

I just did a google search and there was several titles concerning the same issue as you had.

Hey there, I'm sorry, I just got back from trip away and saw how grumpy my post was.  There is no excuse for that, you were trying to help - and I chewed you out.  Sorry.

Kneewax

---

### Post by kneewax on 2009-07-23
> **regala said:**
> if someone told him to go 2.6.30, I wouldn't stress out enough the fact that 2.6.31-rc3 is not stable, and that with 2.6.30, he wouldn't need a patch :)

too true!

Thanks for all the posts guys, I've been away hence my not replying sooner.

Not sure  I want to go too far down the 'recompiling drivers from source' route etc.

For now,  I've reset the default in Grub to boot my previous kernel version. As I clearly didn't understand the implications of going to a newer version :oops: I will see if I can find a better solution to my 'freezing' issues.

cheers

---

