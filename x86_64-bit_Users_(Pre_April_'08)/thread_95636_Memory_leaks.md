---
title: "Memory leaks?"
date: 2005-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by almahtar on 2005-11-27
Hiya.  I've been running Breezy amd64 on my notebook for a few weeks, and I've noticed that upon initial bootup, ram use is 150 megs, give or take.  Six or so hours later (after running programs, etc), it won't go below 350.  After about 10 hours it gets unstable and sometimes locks up.  Are any of the other amd64 users getting this kind of behavior?  There's probably some specific program that's doing it (some desklet or something)... comments?

---

### Post by Emerzen on 2005-11-27
Are you running Azureus by any chance?  Older versions had that problem, but I've never seen it.

I'd try rebooting your computer and leaving it on for 6 hours without starting any apps.  See if it's the core system or a specific app w/ the leak.

---

### Post by almahtar on 2005-11-27
I should do that.  I'll do it tomorrow night.  Good advice.

Oh, and I'm not running azureus.

---

### Post by towsonu2003 on 2005-11-27
I believe firefox has a known leakage bug that's not fixed... you could take a look at system monitor (applications>system tools) to see what's occupying more memory. for me it's always xorg and it keeps going up some days... and finally, i believe linux just likes to write to free memory, but i'm not sure about that at all :) seen it somewhere but dont remember.

---

### Post by almahtar on 2005-11-28
Yeah, I figured it was cached libraries left in memory in case they were needed again, but if that was the case you'd think when that ram was needed by something that wasn't just library cache the cached libraries that weren't in use would be purged to make room.  If that was the case the system wouldn't get any less stable as the memory load increased, but it is.  That's why I think it's a leak.

You're probably right about the firefox thing.  What browser would you recommend I use?  Epitomy?  What do you use?

---

### Post by towsonu2003 on 2005-12-17
i use firefox but I've got plenty of memory. when I had firefox 1.0.7, I was using epiphany, which is almost as good and more stable than firefox... sorry for the delay in response.

---

### Post by koresho on 2008-03-31
I have the same issue with the 686-generic kernel. Question: if Linux likes to keep libraries in the memory, is there any way to force the kernel to purge them with a console command or something?

---

### Post by ASULutzy on 2008-03-31
You wouldn't want linux to purge things in memory, would you?

You have to understand that empty ram is wasted ram. If you have 4 GB of ram and you're only using 1 GB, then you currently have 3GB of paperweights.

The only time ram is useful is if it's filled with something, right?

---

