---
title: "AMD 64 X2 processor 'race' condition"
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Footer on 2007-04-24
I built this system back in January and started running Kubuntu Feisty Fawn 64-bit on it:

[INDENT]Asus M2N-SLI Deluxe motherboard
AMD Athlon 64 X2 4200+(65W) Windsor 2.2GHz Socket AM2 processor
Corsair XMS2 2GB (2 x 1GB) DDR2 800 (PC2 6400) Dual Channel memory
Albatron 7600GS 256MB GDDR2 PCI Express x16 video card
2 X 250GB Seagate SATA
430W Antec Neo HE[/INDENT]

I've been having a problem where my processors will 'race' ... That is, when sitting idle overnight, some mornings the processors will be alternating at 100% usage.  After clicking around a bit and waiting for a response, it usually goes away or I am able to log off/on and all is back to normal.

At first I thought perhaps it was because Feisty was still in beta but now that it's gone final, the problem still occurs.  Also, I suspected Firefox may be causing the problem as I usually leave two windows open with a dozen or so tabs each.  But this 'race condition' with the processors happens even with Firefox closed.

Here's the kernel I'm currently using:  2.6.20-15-generic

One final note, if I could run KSysGuard, I would to try find out what process or processes are hogging the processors but they are so consumed, I can't launch another program or by the time I'm able, the activity has stopped.

Any help or insight with this problem would be GREATLY appreciated!  Thanks.

:)

---

### Post by Jouke74 on 2007-04-24
The AMD uses frequency scaling, that means that the processors' CPU frequency is scaled down to what they need in order to run current processes. After a night of idle they probably run at the minimum frequency (e.g. 1 GHz instead of 2.2). Therefore if you start to run something calculation intensive, they need to get back into their high frequency state, which is done automatically, but probably not instantly. You can turn it of under preference > session > untick CPU frequency scaling. Or in the BIOS of your motherboard (see also AMD cool & quiet). This means the frequency will be kept at 2.2 Ghz, but it also means you are using more power...

---

### Post by Footer on 2007-04-25
Thanks for the reply.

However, I'm a bit confused about your solution:  preference > session > untick CPU frequency scaling.  Is this referring to the Gnome window manager?  I should have mentioned in my original post that I'm using Kubuntu so is there an equivalent setting in KDE somewhere?

I apologize if this is not the correct place for this post but the Kubuntu forums don't get near the traffic that this forum does so I thought I'd have a better chance at a response here!

Thanks!

PS.  I haven't checked the BIOS for my mobo yet (I hate rebooting!) nor have I looked at AMD's site about the Cool N Quiet technology.  But I suspect it's probably a little thin on information when it comes to Linux ... ?

---

### Post by Tom Mann on 2007-04-26
I have very similar hardware to you (AMD X2 3800+, Asus 7600GT, Corsair 1GB RAM, M2N-SLI Deluxe) and I have had no such trouble with Kubuntu. However in my BIOS, I have disabled ALL frequency scaling, as my cooling is enough to run quietly and comfortably without it. Maybe the BIOS is your friend...

---

### Post by modorf on 2007-04-26
what about leaving a term window open and top running.
This will tell you which process is hogging 100%+ cpu time.

---

### Post by Footer on 2007-04-26
Tom -- Thanks for the reply.  However, this condition happens even with Cool-N-Quiet disabled in my BIOS!  I turned it on yesterday just to give it a few days and see if there's any difference.  So far, so good.  I'm just starting to learn about this frequency scaling stuff and it's a bit puzzling.  AMD has drivers specific to Linux and this processor here (third one down):
[INDENT]
[http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html](http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html)[/INDENT]

However, the README file is a little thin on details and I'm not quite sure how to build it in to my kernel.  So I assume what I'm using now for frequency scaling is whatever the generic process/drivers are that come with Kubuntu Feisty.  So perhaps it would be good to go with the ones from AMD but I'm clueless how to install them.

Also, I'm wondering what the best way is to monitor the frequency the processors are running at?

And yes modorf, I will try using top in a terminal window next time to see if that tells me what's sucking up the processors at 100%.

Thanks for the replies thus far!

:)

---

### Post by Jouke74 on 2007-04-27
Using the AMD drivers instead of the generic won't change it I think. The programs basically do the same. Also I think you might have more issues, not related to the CPU frequency scaling. I don't know what, because the average time my computer is on is less than a single day. Check also if there are no program's with memory leaks which start to make you use the swapspace (makes computer slow as well).

---

