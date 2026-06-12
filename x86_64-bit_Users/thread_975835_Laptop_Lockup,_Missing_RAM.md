---
title: "Laptop Lockup, Missing RAM"
date: 2008-11-08
forum: x86 64-bit Users
---

### Post by metroidnemesis13 on 2008-11-08
I have a Compaq Presario V2000 and it's acting strangely.  I just installed 64 bit Ubuntu 8.10 and it's freezing and locking up constantly.  The system monitor says its running at 40-5 percent CPU power and it's using anywhere from 80 to 100 percent of RAM and taking up 400 MB in swap.  It's a 1.6 GHz CPU with 512 MB of ram (it says so in the bios, and on the chips).  In the sys monitor it says I only have 370 MB of RAM total.  Does this have something to do with 64 bit processors?  So far I'm not very impressed by the AMD 64 bit (this is my first time using it).  Where did that RAM go, first of all?  Secondly, can I dual boot Ubuntu 64 with Ubuntu 32 bit?  Thirdly, would these problems go away if I had 1.5 gigs of ram?  

Thanks,

Harlan

---

### Post by metroidnemesis13 on 2008-11-08
Anyone?

---

### Post by Steveway on 2008-11-08
This sounds like faulty RAM. You should run Memtest for half a day or more.
Also do NOT bump your thread after 50 minutes! That is very rude.

---

### Post by metroidnemesis13 on 2008-11-08
When I don't bump it I usually don't get an answer :/ sorry.  Still have questions about sound stuff... but that's beside the point.  Yeah I'll look into that.  The bios says it has 512, but yeah I've used dodgy memory before, and it could be.  Thanks.

---

### Post by metroidnemesis13 on 2008-11-08
Yeah in memtest it only sees 383 MB where there should be 512.  Wait.  What's reserved mem? it says Cached: 383 MB Reserved: 129 MB.  Total that's 512.  Why is it reserving that much?  It passed error free once so far.

---

### Post by Kilz on 2008-11-08
> **metroidnemesis13 said:**
> Yeah in memtest it only sees 383 MB where there should be 512.  Wait.  What's reserved mem? it says Cached: 383 MB Reserved: 129 MB.  Total that's 512.  Why is it reserving that much?  It passed error free once so far.

What graphics card does it have? Does the card use system ram? If so your system is going to run pretty poorly with only 128 megs of ram left.

---

### Post by metroidnemesis13 on 2008-11-08
It has an ATI graphics card.  Can graphics cards do that?  like take ram for themselves?

---

### Post by cariboo on 2008-11-08
The reserved memory could be for your video card, I would still run memtest just to be sure as there is something wrong with your installation.

I had a a ram module go bad about a week ago, it didn't cause any lock ups or anything, but eventually it caused my raid array to go into a race condition, which made the array unmountable. After 8 hours of running fsck the array is useable, but I lost about 20Gb of data, fortunately I had good backups so everything is as good as new.

---

### Post by metroidnemesis13 on 2008-11-08
Mem-test ran through fine without errors three times.  I have a better ATI graphics card in my desktop and it's not reserving ram.  Can I tell the graphics card to not reserve ram?

---

### Post by jocko on 2008-11-09
No, you can't, but there may be a bios setting to lower the amount. Most integrated graphics cards don't have their own RAM, so they need to use some of the system RAM (seems like yours use 128 Mb, so you have only 384 Mb left for system use).

384 Mb RAM is quite low (and so is 512), but I don't think it should cause crashes or freezes unless you run out of swap space. How large is your swap partition?

---

### Post by metroidnemesis13 on 2008-11-09
About a gig.  It was using up about 400 MBs in swap.  It wasn't really crashing, just locking up (it would take me ten minutes to open a browser).

---

### Post by metroidnemesis13 on 2008-11-10
Anybody else have memory reserved in notebooks, or is it just mine?  Compaq specifically?

---

### Post by Kilz on 2008-11-10
> **metroidnemesis13 said:**
> Mem-test ran through fine without errors three times.  I have a better ATI graphics card in my desktop and it's not reserving ram.  Can I tell the graphics card to not reserve ram?

Three times is not enough, it doesn't let the hardware build up enough heat and strain. You need to run it over night, or at least for a few hours. Let it run 30 or 40 times.

---

