---
title: "4gb RAM eaten by cache, causing machine to freeze"
date: 2007-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by lmellor on 2007-12-10
Hi, I have searched the forum for an answer to this problem, I have a pretty new machine (2x2ghz core2duo, nvidia 8600gt, 4gb ddr2, sata dvd+/-rw, 250gb sata2hdd, 500gb sata2hdd, nforce 650 mobo) and have recently come back to the wonderful world of ubuntu.

My computer seems to run fine for anything up to 2 days but it will always lock-up eventually.  I have put a system monitor in my panel which shows me that at first my comp is using 5% RAM for applications, ~30% fo cache but it is very swiftly moving up to 30% apps, 70% cache.  At this point it freezes and I can do very little other than hit the reset button, ctrl+alt+F1 does nothing, nor does the mouse.

As you can imagine this is getting to be rather annoying.  I am running 64bit Gutsy and cannot wait to hear any suggestions as to how I can get to the bottom of this.

TIA.

Luke.

---

### Post by fjgaude on 2007-12-10
It's normal for a Linux system to use all available memory in cache. As apps need it the cache gives it to them. Does your machine lockup as all memory is used?

---

### Post by crjackson on 2007-12-10
Are you using the restricted video driver from the repos...?

I noticed you have an 8600 card and it's well know that the current driver from the repos has a memory leak that requires you to reboot now and then to reclaim video memory (which caused many machines to lock up otherwise).

It's normal for Linux to use all available memory for cache until released or needed by applications.

Unused memory is waisted memory...

---

### Post by RAOF on 2007-12-11
Your system should be using as close to 100% of your RAM as possible.  All that cache is stuff that won't have to be read from the hard drive next time you use it, making it approximately 1000 times faster to access (hard drives are slow!).

However, if you find that your computer crashes once you reach a certain RAM utilisation you may be exposing a bad RAM module.  I'd suggest trying a [memcheck]("https://help.ubuntu.com/community/MemoryTest") as the first port of call.

---

### Post by tighem on 2007-12-11
If you are running compiz and nvidia, make sure you have indirect rendering turned on, otherwise you will be exposed to a nasty memory leak.

---

### Post by lmellor on 2007-12-11
I'm glad I posted in here, I've done a memtest, all is fine, though I did expect it to be, it's all paired corsair RAM (and the slightly more expensive stuff at that too, CAS 4 as I remember).

How do I turn on inderect rendering?, I am running all of the above, hence my wonderful theme.

---

### Post by lmellor on 2007-12-13
nevermind, I've turned off compiz, emerald and the restricted rivers until nvidia fix it, I'm not one for instabilities no matter how pretty they look.

---

### Post by lmellor on 2008-01-02
hi, I've been testing different scenarios for the past couple of weeks and have noticed that it is actually the buffer part of the ram that is slowly filling up (reported by system monitor), I've just upgraded my graphics driver via envy and am seeing if this fixes anything, though if anything the problem seems to be getting worse, computer has been on for around 30 mins and already it's using over half of my ram as buffer, is this bad? can anybody help?  I have re-enabled compiz at the moment too as disabling it didn't seem to make my computer any more stable.

---

### Post by chrisccoulson on 2008-01-02
> **lmellor said:**
> hi, I've been testing different scenarios for the past couple of weeks and have noticed that it is actually the buffer part of the ram that is slowly filling up (reported by system monitor), I've just upgraded my graphics driver via envy and am seeing if this fixes anything, though if anything the problem seems to be getting worse, computer has been on for around 30 mins and already it's using over half of my ram as buffer, is this bad? can anybody help?  I have re-enabled compiz at the moment too as disabling it didn't seem to make my computer any more stable.

AFAIK, the buffers are data waiting to be written to disk

---

### Post by chewearn on 2008-01-02
I have also been facing random system freezes, which didn't show up on any system logs.  
I tried various stuffs for a few weeks, also muddling through one or two long threads here about random system freezes.

Finally, right before Christmas, a new kernel was released, followed by nvidia new driver 169.07.  Since then, the problem has gone away.

---

### Post by lmellor on 2008-01-25
I found the root of my problem, it seemed odd that whether I was in ubuntu or windows my computer would only stay alive for so long (a random time period though the period was much longer in ubuntu).  After much scouring of google and these forums I came across a problem with the 650i boards whereby the ram wasn't being supplied with enough power to withstand 4 sticks, I upped the ram voltage in my bios from an auto rating of 1.78v to 2v and my computer hasn't crashed since!  I can't guarantee that this will help anybody else, nor am I accepting responsibility for blown rigs but it definitely worked for me.

---

