---
title: "[SOLVED] Swiftfox AMD64 problems"
date: 2007-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by p_quarles on 2007-11-05
First of all, I'm fairly new to the 64-bit OS, and have been loving it. I've been re-encoding my music collection to FLAC, and the speed is amazing.

I've hit a snag, though, and I'm hoping someone can help. When I was using 32-bit Ubuntu, I always used Swiftfox, as it seemed slightly faster and more stable than Firefox. When I switched to 64 bits, I noted on Swiftfox's web site that the version compiled for my processor (Pentium D dual) was a 32-bit version, the same one I'm using on my Core 2 duo laptop. I used Firefox for a while, but was getting *very *unhappy with its performance. I decided to give the one 64-bit compile of Swiftfox a chance (compiled on an AMD processor) -- and I was blown away by the performance increase. *Much* more noticeable than what I'd seen in 32 bits.

Long prologue, I know. Just wanted to explain *why *I want to get this working properly, rather than reverting to Firefox. Anyway, the problems are:
1) Flash isn't working. On any site. I *do* have the nspluginwrapper installed, and Flash works just fine in the default Firefox installation. 

2) The widget style is completely different from the one I actually have set for my desktop. It's supposed to be set on QTcurve, but it looks like Light Style or something similar. Again, the default Firefox dealt with my settings correctly. 

In my previous experiences, I've never had any problems getting Swiftfox to inherit all of the Firefox settings. Obviously, problem 1 is much more important to me than the widget style, but I mention both cause I suspect they're related. 

Any ideas? The only thing I can think of is that I'm using a version of Swiftfox that was compiled for a different manufacturer's chip. But it's the same architecture, so I'm guessing that's not the problem. Thanks in advance for any suggestions.

---

### Post by Kilz on 2007-11-05
> **p_quarles said:**
> First of all, I'm fairly new to the 64-bit OS, and have been loving it. I've been re-encoding my music collection to FLAC, and the speed is amazing.

I've hit a snag, though, and I'm hoping someone can help. When I was using 32-bit Ubuntu, I always used Swiftfox, as it seemed slightly faster and more stable than Firefox. When I switched to 64 bits, I noted on Swiftfox's web site that the version compiled for my processor (Pentium D dual) was a 32-bit version, the same one I'm using on my Core 2 duo laptop. I used Firefox for a while, but was getting *very *unhappy with its performance. I decided to give the one 64-bit compile of Swiftfox a chance (compiled on an AMD processor) -- and I was blown away by the performance increase. *Much* more noticeable than what I'd seen in 32 bits.

Long prologue, I know. Just wanted to explain *why *I want to get this working properly, rather than reverting to Firefox. Anyway, the problems are:
1) Flash isn't working. On any site. I *do* have the nspluginwrapper installed, and Flash works just fine in the default Firefox installation. 

2) The widget style is completely different from the one I actually have set for my desktop. It's supposed to be set on QTcurve, but it looks like Light Style or something similar. Again, the default Firefox dealt with my settings correctly. 

In my previous experiences, I've never had any problems getting Swiftfox to inherit all of the Firefox settings. Obviously, problem 1 is much more important to me than the widget style, but I mention both cause I suspect they're related. 

Any ideas? The only thing I can think of is that I'm using a version of Swiftfox that was compiled for a different manufacturer's chip. But it's the same architecture, so I'm guessing that's not the problem. Thanks in advance for any suggestions.

Swiftfox is a proprietary build of Firefox. It has a restrictive license that limits what we can do with it. For instance I cant add it to the 32bit browser howto because of its license(limits redistribution and modification). As such it makes you the user experience problems. One is that all builds of Swiftfox are 32bit.
But there is an alternative that is free and open source. [Try Swiftweasel.]("http://swiftweasel.wiki.sourceforge.net/")

---

### Post by p_quarles on 2007-11-05
> **Kilz said:**
>  As such it makes you the user experience problems. One is that all builds of Swiftfox are 32bit.
So the AMD-64 build of Swiftfox is actually a 32 bit program?  I had no idea. That makes perfect sense, though, because I had exactly the same issues when I tried out the Linux binary of Firefox 3 (which is presumably also compiled for the 32-bit processor).

> But there is an alternative that is free and open source. [Try Swiftweasel.]("http://swiftweasel.wiki.sourceforge.net/")
Good point. If I'd realized the problems with Swiftfox, that's probably what I'd have done in the first place. /sigh

Thanks for the help. I'll post back about how it goes.

---

### Post by p_quarles on 2007-11-05
Well, that was easy. Swiftweasel didn't manage to inherit all of my settings, but that's fixable. Flash works, my widget style is correct, and it's fast. Thanks much, Kilz. :)

---

