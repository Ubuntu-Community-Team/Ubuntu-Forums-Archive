---
title: "Memory problems cause slowdown..."
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by underwog on 2008-01-09
So I have an interesting problem. My system works and works fine for with 4x1GB dimms and Folding, but slowsdown after awhile. 2x1GB dimms always work. Also memtest/prime95 smp/windows work fine either way.

I hate to do this and I hope it isn't against the rules, but I have been troubleshooting this problem on foldingforums for awhile and don't want to repost everything. Here is the link:
[http://foldingforum.org/viewtopic.php?f=12&t=417&p=5623#p5623](http://foldingforum.org/viewtopic.php?f=12&t=417&p=5623#p5623)

Thanks.

---

### Post by NFITC1 on 2008-01-09
NEVER UNDER ANY CIRCUMSTANCES MIX THOSE RAM TYPES!!! Timing issues will make the problem even worse. Phew, now that that's out of the way....

Windows almost always has a pagefile (Swap files for those of us who "grew up" on Win95 and Win98) that it uses for RAM. It really likes this pagefile. So much so that sometimes it defaults to it rather than use the actual onboard RAM. If you're still using a pagefile in Windows I say get rid of it and see if the problem is similar. The other possibility is if your MoBo isn't set correctly it won't identify all 4GB. I had to change a setting in my BIOS to get it to acknowledge there were 4.0GB instead of 3.2GB. Windows will still not recognize more than about 3.5GB even then.
Like I said at the very beginning, don't mix Crucial and OCZ sticks, but it's even better to have 4 IDENTICAL sticks from one or the other. For every RAM speed rating there are at least four types of sticks (ECC/Registered and Un/Buffered, not to mention different voltage requirements) all that potentially different timing. The MoBo can correct this to an extent by clocking down to the lowest denominator IF it has that option.

I guess what I'm saying is it sounds like a hardware problem since Windows will correct it with the pagefile. Make sure the board is recognizing all 4GB then see what the OSs report the memory as.

---

### Post by underwog on 2008-01-09
Manual timings/voltages vice using the SPD would allow me too mix them, but I haven't tried since I don't think that is the problem. There isn't a JEDEC memory standard for anything over DD2-800, if I recall correctly. My Crucial DDR2-1066 is really just DDR2-800 memory that was binned. Also, OCZ doesn't make memory chips; I'm pretty sure that when I researched this RAM, they were using Crucial chips (DB9's I think, which is what Ballistix uses). The other major player is Samsung and Infinity is there too, but small compared to those two for this market.

I have 4 identical 1GB Crucial Ballistix DDR2-1066 sticks and 4 identical 1GB OCZ DDR2-800 sticks. Mixing and matching amung the four identical sticks (2x1GB setup) doesn't change anything and swapping all RAM from one machine to the other doesn't seem to either.

I am dual booting Ubuntu 64bit and Windows XP64. Both recognized 4GB of RAM when I have it installed. I think I tried disabling the page file on Windows XP64 and the results didn't change, but I will try again. Needless to say with 4GB installed and recognized, the pagefile usage was very small (just Windows being over zealous).

I am pretty certain it is just the MB not handling 4 full dimms well (a google search shows that various voltage settings can overcome this and I have tried some, but haven't had any success, but haven't gone too high since this is a 24x7 Folding rig). The weird thing about it is I only notice the problems under Linux/Folding, which is why I thought it was a software problem. However, I haven't tried Folding under Windows, but other stress testing programs are just fine.

---

### Post by NFITC1 on 2008-01-09
> **underwog said:**
> ...Also, OCZ doesn't make memory chips; I'm pretty sure that when I researched this RAM, they were using Crucial chips (DB9's I think, which is what Ballistix uses)...

This may be, but there is still a good chance the timings are different. Within a single channel of RAM, the sticks should never be mixed.
The rest of your post convinces me you know the rest and that it does sound like a Folding issue. Which, I must confess, my experience is in the "None to noob" level with leaning toward the "I've never heard of this until now" end of the spectrum. :D I was just making sure you're convinced it's not a hardware issue. Sorry for getting your hopes up at seeing a reply.

---

### Post by underwog on 2008-01-09
I am pretty sure it is a hardware related problem, but I do not know if it is only a hardware problem. 4x1GB takes a performance hit, but works fine for awhile and 2x1GB works all the time (so far). The interesting thing about this is that is seems (still have more testing to do to rule everything out...lots of combinations!) that the problem is limited to Linux and 4x1GB. So my question becomes:

If it works for awhile and then performance degrades, but doesn't fail (no reboots, failed WU, etc.) is this:
1. A chipset only problem (Abit IP35-Pro...which others have gotten to work with 4 dimms)
2. Or is it some weird bios/os/4dimms interaction?

I haven't exhausted every combination of memory/cpu/chipset voltage/timing/etc. If it is a number 2 problem, how/what info should I collect? Also, Folding works fine with 2x1GB of RAM regardless of time or other usage.

---

