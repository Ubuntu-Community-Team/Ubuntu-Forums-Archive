---
title: "cpu 64bit running as 32bit"
date: 2008-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by makeiteasy on 2008-01-11
Installed Ubuntu (dual boot with XP64) and IMPRESSED with it.
Cube desktop, free software, easy upgrade and much more. a beauty.
I am trying to switch to Linux versus Windows. It seems I have to learn alot before doing so.

Have few things working wrong. 

For now, can somebody help me how to let my CPU run at 3700+ instead of 2.20Ghz
(AMD Athlon 3700+)

If you have the stamina for more.. , my system does not do sleep mode properly.
I have to turn off the system than on after "suspend".

The CPU in "System Monitor" is busy for about 10% most of the time. donno why.
I can tune up things in XP64 to an advanced level. but am clueless in Ubuntu.

My XP64 runs super fast. Ubuntu is much slower. Shall I accept that or something I can do to tune up Ubuntu.

Thanks
:(

---

### Post by Yellow Pasque on 2008-01-11
Your processor's stock speed is 2.2 GHz. It probably idles at 1 GHz, so it can undervolt and save power. Intel CPU's at that time had higher clock speeds, but generally did not perform as well (and ran much hotter). However, customers would still buy them because they thought more MHz = faster. So AMD slapped the equivalent P4 speed on their CPU's."3700" is the model number AMD used on this CPU, so it infers that your 2.2GHz chip is equivalent to a P4 @ 3.7GHz (actually, it's probably faster at most tasks).

The clock speed has no correlation with 32 or 64 bit. I think you need to find a site on CPU basics and review the basic terminology/concepts behind CPU's.

---

### Post by compwiz18 on 2008-01-11
> **makeiteasy said:**
> 
The CPU in "System Monitor" is busy for about 10% most of the time. donno why.
I can tune up things in XP64 to an advanced level. but am clueless in Ubuntu.

My XP64 runs super fast. Ubuntu is much slower. Shall I accept that or something I can do to tune up Ubuntu.
I suspect that the CPU is at 10% when the System Monitor is open because it requires 10% of the CPU's power to run the System Monitor.

As for Ubuntu being slower then XP - it depends what you are doing and how you have the systems set up.  XP will be faster at some things then Ubuntu, and Ubuntu will be faster at some things then XP.  If you google around a bit, you can find some ways to speed up Ubuntu, although not all of them actually increase the speed much, and some do so at the cost of other things.

[http://www.google.com/search?hl=en&q=speed%20up%20ubuntu](http://www.google.com/search?hl=en&q=speed%20up%20ubuntu)

You can try some of the results there: I'd recommend [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651) and [http://www.zolved.com/synapse/view_content/28311/Tune_Boot-Up-Manager_for_better_performance_of_Ubuntu](http://www.zolved.com/synapse/view_content/28311/Tune_Boot-Up-Manager_for_better_performance_of_Ubuntu)

Make sure only to change things you understand :KS

---

### Post by dptxp on 2008-01-11
XP will be faster, it was supposed to run with 128 MB RAM (not sure about 64 bit XP though).

So XP will be faster, till you run the anti-virus program. Or till you get some nice virus.

---

### Post by amadeus266 on 2008-01-12
> **makeiteasy said:**
> 

For now, can somebody help me how to let my CPU run at 3700+ instead of 2.20Ghz
(AMD Athlon 3700+)


:(

The 3700+ is the model number given by AMD not the speed. My AMD Athlon 64 is a 2800+ 1.8Ghz


Edit: Sorry, should have read the previous posts as Temujin already mentioned that.

---

### Post by makeiteasy on 2008-01-12
Thank you Temüjin, compwiz18, dptxp, amadeus266

I now understand better the CPU, frequency, registry, CPU time.

dptxp, it is true when you install an anti-virus program in XP, it slows down.
Don't have one there (so far)

It seems I need to learn Linux command. I started.

Any quick hint why the system cannot recover from "suspend" ?

The system goes to suspend mode. but doesn't resume on mouse click/move or any keyboard input. I have to press the power button. it starts somehow in a wrong way and I have to shut it down and restart.

---

### Post by Kilz on 2008-01-13
If you dont have anti virus in XP you are heading for problems. Get a free anti virus if nothing else. Agv and Avast are pretty good.

[This page is a great resource for learning about linux commands.]("http://www.ss64.com/bash/") I hope it helps you as much as its helped me.

---

